# scipy-conference official documentation translations

[![Contributor Covenant](https://img.shields.io/badge/contributor%20covenant-2.1-4baaaa.svg)](https://github.com/tkoyama010/scipy-conference-doc-translations/blob/main/CODE_OF_CONDUCT.md)

[scipy-conference official documentation translations](https://github.com/tkoyama010/scipy-conference-doc-translations) is a project to provide scipy-conference official documentation, hosted on
the Read The Docs platform, in multiple languages.

> [!NOTE]
> The current procedure is bit tricky because Read The Docs
> doesn't have a way to specify options for `sphinx-build` command.
> **conf.py** files for each languages have `language` and `locale_dirs`
> values without having full copy of **conf.py** of scipy-conference doc. If we want
> to specify **conf.py** file that is out of source directory, we will use
> `-c` option for the `sphinx-build` command. Unfortunately Read the Docs
> doesn't support that. If there is a better way, open an issue.

## How the translated documentation projects are setup on RTD

Instructions:
https://docs.readthedocs.org/en/latest/localization.html#project-with-multiple-translations

Key points:

- There is a RTD project for each language.
- Each project needs the correct **Language** setting on the
  **Settings** page.
- The parent project needs connections created to each translated
  project on the **Translations Settings** page.

| Language                 | Build Status                                                                                                                                              | RTD Project                                                                                                                  | Transifex                                                                                                                             |
| :----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| English (parent project) | [![Documentation Status](https://readthedocs.org/projects/scipy-conference/badge/?version=latest)](https://scipy-conference.readthedocs.io/en/latest/?badge=latest)       | [![readthedocs.org](https://img.shields.io/badge/readthedocs-en-ff7964.svg?)](https://readthedocs.org/projects/scipy-conference/)    |                                                                                                                                       |
| 日本語                   | [![Documentation Status](https://readthedocs.org/projects/scipy-conference-ja/badge/?version=latest)](https://scipy-conference-ja.readthedocs.io/ja/latest/?badge=latest) | [![readthedocs.org](https://img.shields.io/badge/readthedocs-ja-ff7964.svg?)](https://readthedocs.org/projects/scipy-conference-ja/) | [![Transifex](https://img.shields.io/badge/Transifex-ja-blue.svg?)](https://app.transifex.com/tkoyama010/scipy-conference-doc/translate/#/ja) |

## How to add a new language translation

1.  Add new language to `locale/update.sh`:

```diff
-   rm -R es ja
-   tx pull -l es,ja
+   rm -R es ja pt_BR
+   tx pull -l es,ja,pt_BR
```

2.  Update po files:

```
sh ./locale/update.sh
```

3.  Commit them

4.  Add new project on Read The Docs. For example, for `pt_BR`:

    https://readthedocs.org/projects/scipy-conference-pt-br/

> [!NOTE]
> If a RTD project name for a translation is already taken,
> create a unique project name instead. For example, when `scipy-conference-ru`
> was taken, `scipy-conference-doc-ru` was used instead.

5.  Add new translation project to parent project:

    https://readthedocs.org/dashboard/scipy-conference/translations/
