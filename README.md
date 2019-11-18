# _Google Spreadsheet._ Open Microservice

> This is a google-sheets service.

[![Open Microservice Specification Version](https://img.shields.io/badge/Open%20Microservice-1.0-477bf3.svg)](https://openmicroservices.org)
[![Open Microservices Spectrum Chat](https://withspectrum.github.io/badge/badge.svg)](https://spectrum.chat/open-microservices)
[![Open Microservices Code of Conduct](https://img.shields.io/badge/Contributor%20Covenant-v1.4%20adopted-ff69b4.svg)](https://github.com/oms-services/.github/blob/master/CODE_OF_CONDUCT.md)
[![Open Microservices Commitzen](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Introduction

This project is an example implementation of the [Open Microservice Specification](https://openmicroservices.org), a standard
originally created at [Storyscript](https://storyscript.io) for building highly-portable "microservices" that expose the
events, actions, and APIs inside containerized software.

## Getting Started

The `oms` command-line interface allows you to interact with Open Microservices. If you're interested in creating an Open
Microservice the CLI also helps validate, test, and debug your `oms.yml` implementation!

See the [oms-cli](https://github.com/microservices/oms) project to learn more!

### Installation

```
npm install -g @microservices/oms
```

## Usage

### Open Microservices CLI Usage

Once you have the [oms-cli](https://github.com/microservices/oms) installed, you can run any of the following commands from
within this project's root directory:

#### Actions

##### createSpreadsheet

> Create new google spreadsheet.

##### Action Arguments

| Argument Name   | Type     | Required | Default | Description                                                                                                                               |
| :-------------- | :------- | :------- | :------ | :---------------------------------------------------------------------------------------------------------------------------------------- |
| title           | `string` | `true`   | None    | Title for new spreadsheet.                                                                                                                |
| emailAddress    | `string` | `true`   | None    | The gmail email address of the user or group to which this drive permission refers (used to view sheet from email address drive account). |
| role            | `string` | `true`   | None    | The role granted by this permission, the roles currently allowed - writer ( recommended ), organizer , fileOrganizer, commenter , reader. |
| type            | `string` | `true`   | None    | The type of the grantee. the types currently allowed - user ( recommended ), group, domain, anyone.                                       |
| CREDENTIAL_JSON | `string` | `true`   | None    | Base64 data of credential.json' file.                                                                                                     |

```shell
oms run createSpreadsheet \
    -a title='*****' \
    -a emailAddress='*****' \
    -a role='*****' \
    -a type='*****' \
    -e CREDENTIAL_JSON=$CREDENTIAL_JSON
```

##### findSpreadsheet

> Get spreadsheet by ID.

##### Action Arguments

| Argument Name   | Type     | Required | Default | Description                           |
| :-------------- | :------- | :------- | :------ | :------------------------------------ |
| spreadsheetId   | `string` | `true`   | None    | The ID of spreadsheet.                |
| CREDENTIAL_JSON | `string` | `true`   | None    | Base64 data of credential.json' file. |

```shell
oms run findSpreadsheet \
    -a spreadsheetId='*****' \
    -e CREDENTIAL_JSON=$CREDENTIAL_JSON
```

##### addSheet

> Add new sheet in spreadsheet.

##### Action Arguments

| Argument Name   | Type     | Required | Default | Description                           |
| :-------------- | :------- | :------- | :------ | :------------------------------------ |
| spreadsheetId   | `string` | `true`   | None    | The ID of spreadsheet.                |
| sheetTitle      | `string` | `true`   | None    | The title for new sheet.              |
| CREDENTIAL_JSON | `string` | `true`   | None    | Base64 data of credential.json' file. |

```shell
oms run addSheet \
    -a spreadsheetId='*****' \
    -a sheetTitle='*****' \
    -e CREDENTIAL_JSON=$CREDENTIAL_JSON
```

##### findSheet

> Get sheet by sheet title.

##### Action Arguments

| Argument Name   | Type     | Required | Default | Description                           |
| :-------------- | :------- | :------- | :------ | :------------------------------------ |
| spreadsheetId   | `string` | `true`   | None    | The ID of spreadsheet.                |
| sheetTitle      | `string` | `true`   | None    | The title of sheet.                   |
| CREDENTIAL_JSON | `string` | `true`   | None    | Base64 data of credential.json' file. |

```shell
oms run findSheet \
    -a spreadsheetId='*****' \
    -a sheetTitle='*****' \
    -e CREDENTIAL_JSON=$CREDENTIAL_JSON
```

##### updateSheetSize

> Update sheets row and column.

##### Action Arguments

| Argument Name   | Type     | Required | Default | Description                           |
| :-------------- | :------- | :------- | :------ | :------------------------------------ |
| spreadsheetId   | `string` | `true`   | None    | The ID of spreadsheet.                |
| sheetId         | `int`    | `true`   | None    | The ID of sheet.                      |
| row             | `int`    | `true`   | None    | Length of rows to add in sheet.       |
| column          | `int`    | `true`   | None    | Length of columns to add in sheet.    |
| CREDENTIAL_JSON | `string` | `true`   | None    | Base64 data of credential.json' file. |

```shell
oms run updateSheetSize \
    -a spreadsheetId='*****' \
    -a sheetId='*****' \
    -a row='*****' \
    -a column='*****' \
    -e CREDENTIAL_JSON=$CREDENTIAL_JSON
```

##### updateCell

> Update sheet content.

##### Action Arguments

| Argument Name   | Type     | Required | Default | Description                             |
| :-------------- | :------- | :------- | :------ | :-------------------------------------- |
| spreadsheetId   | `string` | `true`   | None    | The ID of spreadsheet.                  |
| sheetTitle      | `string` | `true`   | None    | The title of sheet.                     |
| cellNumber      | `string` | `true`   | None    | The cell number eg - A1.                |
| content         | `string` | `true`   | None    | The content to update on cell of sheet. |
| CREDENTIAL_JSON | `string` | `true`   | None    | Base64 data of credential.json' file.   |

```shell
oms run updateCell \
    -a spreadsheetId='*****' \
    -a sheetTitle='*****' \
    -a cellNumber='*****' \
    -a content='*****' \
    -e CREDENTIAL_JSON=$CREDENTIAL_JSON
```

##### deleteSheet

> Delete sheet.

##### Action Arguments

| Argument Name   | Type     | Required | Default | Description                                                 |
| :-------------- | :------- | :------- | :------ | :---------------------------------------------------------- |
| spreadsheetId   | `string` | `true`   | None    | The ID of spreadsheet.                                      |
| sheetId         | `int`    | `true`   | None    | The ID of sheet to delete (To delete first sheet use ID 0). |
| CREDENTIAL_JSON | `string` | `true`   | None    | Base64 data of credential.json' file.                       |

```shell
oms run deleteSheet \
    -a spreadsheetId='*****' \
    -a sheetId='*****' \
    -e CREDENTIAL_JSON=$CREDENTIAL_JSON
```

##### newRowUpdate

> Triggered any new row is added.

##### Action Arguments

| Argument Name   | Type     | Required | Default | Description                           |
| :-------------- | :------- | :------- | :------ | :------------------------------------ |
| spreadsheetID   | `string` | `true`   | None    | The spreadsheet ID to subscribe.      |
| sheetTitle      | `string` | `true`   | None    | The title of sheet to subscribe.      |
| CREDENTIAL_JSON | `string` | `true`   | None    | Base64 data of credential.json' file. |

```shell
oms subscribe newRowUpdate \
    -a spreadsheetID='*****' \
    -a sheetTitle='*****' \
    -e CREDENTIAL_JSON=$CREDENTIAL_JSON
```

## Contributing

All suggestions in how to improve the specification and this guide are very welcome. Feel free share your thoughts in the
Issue tracker, or even better, fork the repository to implement your own ideas and submit a pull request.

[![Edit google-sheets on CodeSandbox](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/github/oms-services/google-sheets)

This project is guided by [Contributor Covenant](https://github.com/oms-services/.github/blob/master/CODE_OF_CONDUCT.md).
Please read out full [Contribution Guidelines](https://github.com/oms-services/.github/blob/master/CONTRIBUTING.md).

## Additional Resources

- [Install the CLI](https://github.com/microservices/oms) - The OMS CLI helps developers create, test, validate, and build
  microservices.
- [Example OMS Services](https://github.com/oms-services) - Examples of OMS-compliant services written in a variety of
  languages.
- [Example Language Implementations](https://github.com/microservices) - Find tooling & language implementations in Node,
  Python, Scala, Java, Clojure.
- [Storyscript Hub](https://hub.storyscript.io) - A public registry of OMS services.
- [Community Chat](https://spectrum.chat/open-microservices) - Have ideas? Questions? Join us on Spectrum.
