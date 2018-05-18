# Contributing
Contributions to the yuzu Games Wiki are welcomed, as keeping all of the data up to date and accurate is a community effort.

**Table of Contents**:
- [Info About This Wiki](#info-about-this-wiki)
  - [Angle Brackets](#angle-brackets)
  - [yuzu Version](#yuzu-version)
  - [Dates](#dates)
  - [GitHub Issues](#github-issues)
  - [Screenshots](#screenshots)
  - [Title IDs](#title-ids)
  - [TOML](#toml)
- [Code](#code)
  - [Metadata](#metadata)
  - [Icon](#icon)
  - [Boxart](#boxart)
  - [Game Screenshots](#game-screenshots)
  - [Savefiles](#savefiles)
    - [Save Metadata](#save-metadata)
    - [Save Data](#save-data)
- [Wiki](#wiki)

## Info About This Wiki

### Angle Brackets
Throughout this guide, code blocks like `<Value>` are used. This means that "Value" should be replaced by something, and the "<>" should be deleted.

### yuzu Version
All data must be collected from the latest official yuzu nightly, downloaded from [here](https://yuzu-emu.org/downloads/).

### Dates
All dates follow the format `<4-Digit Year>-<2-Digit Month>-<2-Digit Day>`. For example, June 3rd 2017 would be "2017-06-03".

### GitHub Issues
Game issues can be found [here](https://github.com/yuzu-emu/yuzu/issues). The ID of the issue can be found at the end of the URL. For example, [RA BeetlePSX and mGBA cores fail to boot](https://github.com/yuzu-emu/yuzu/issues/266)'s ID is 266.

### Screenshots
The recommended application for capturing the icon, boxart, and screenshots is [ShareX](https://github.com/ShareX/ShareX). Screenshots can not be compressed, and must be in the PNG format.

### Title IDs
To-Do

### TOML
In this repo, DAT files follow the [TOML](https://github.com/toml-lang/toml) syntax, where each line consists of the creation of a piece of data. The simplest form of this is assigning a value to a key (`<Key> = <Value>`). The data types used for these `Value`s in this wiki are:
 - Booleans, true or false (Example: `true`.)
 - Integers, numbers (Example: `5`.)
 - Strings, characters with surrounding quotes (Example: `"Hi!"`.)
 - Arrays, collection of booleans, integers, or strings (Example for an array of integers: `[33, 2398, 234]`.)

These key/value pairs can be grouped together using an array of tables (Example: `[[ Stuff ]]`, with the pairs on the next lines.). These can be used more than once in a TOML file.

## Code
The code consists of the actual files in the Github repisitory. To modify them, you have to fork this repo, make your changes, and send a pull request.

At the root, there's a folder for each game. The names of these folders should follow these specifications:
- Only use letters, numbers, and hyphens (No spaces!), because they will be linked to on the site.
- Names should be lowercase to ensure consistency.
- Have a wiki page with the same name.

### Metadata
The metadata for the game is located at `/<Game Name>/game.dat`. This is required info about the game, all feilds are mandatory unless noted otherwise. The DAT values (See: [TOML](#toml)) are:
- `title` (String): English title of the game. This doesn't have to match the wiki or folder name, so there can be spaces.
- `description` (String): Get these from [Wikipedia](https://en.wikipedia.org/wiki/List_of_Nintendo_Switch_games). Short, 2-3 line description of the game.
- `github_issues` (Array of integers): The GitHub issue IDs for the game. See: [GitHub Issues](#github-issues).
- `needs_system_files` (Boolean): Whether the game requests the system files or not, regardless of whether it could be played without them (See: [yuzu Version](#yuzu-version)).
- `needs_shared_font` (Boolean): Whether the game requests the shared font or not, regardless of whether it could be played without them (See: [yuzu Version](#yuzu-version)).
- `game_type` (String): Whether the game has a retail release, `"switch"`, or E-Shop **exclusive**, `"eshop"`. This line is optional for retail releases.
- `releases` (Array of tables): Info about each release of the game. **The USA release should come first.**
  - `title` (String): Title ID of this release of the game. See: [Title IDs](#title-ids).
  - `region` (String): Region of the game. Possible values are:
    - `aus`
    - `chn`
    - `eur`
    - `jpn`
    - `kor`
    - `twn`
    - `usa`
    - `all` (Don't tag a game released in multiple regions as `all`. This is reserved for specific games released as such.)
  - `release_date` (String): When the game was released in this region. See: [Dates](#dates).
  - `title` (String): Title ID of this release of the game which was used during testing. See: [Title IDs](#title-ids).

An example of a game metadata file is the one for [Puyo Puyo Tetris](https://github.com/yuzu-emu/yuzu-games-wiki/blob/master/games/puyo-puyo-tetris/game.dat):
```toml
title = "Puyo Puyo Tetris"
description = "Puyo Puyo Tetris is a puzzle video game developed by Sonic Team and published by Sega. The game is a crossover between the Puyo Puyo series and the Tetris franchise, and features various gameplay modes incorporating both aspects."
github_issues = [2517]
needs_system_files = false
needs_shared_font = false

[[ releases ]]
title = "010073C001D5E000"
region = "usa"
release_date = "2017-04-25"

[[ releases ]]
title = "0100F3D001DEE000"
region = "eur"
release_date = "2017-04-28"

[[ releases ]]
title = "010053D0001BE000"
region = "jpn"
release_date = "2017-03-03"
```

### Icon
To-Do

### Boxart
To-Do

### Game Screenshots
To-Do

### Savefiles
To-Do

## Wiki
The wiki contains info about specific game problems, and can be modified by anyone. They use [Markdown](https://guides.github.com/features/mastering-markdown/) formatting.

Each page's title should match the game's respective folder in the code section, except with hyphens in the code changed to spaces on the wiki. **Don't use the following characters in your wiki page's titles: \ / : * ? " < > |.**

The format of each page is as follows:
- H2 header with text saying `Summary`.
- Brief summary of how the game performs: graphically, auditorily, and frame rate (with general hardware comparison - see MK7 example). See: [yuzu Version](#yuzu-version).

An example of a game wiki page is the one for [Puyo Puyo Tetris](https://github.com/yuzu-emu/yuzu-games-wiki/wiki/puyo-puyo-tetris):
```markdown
## Summary
Puyo Puyo Tetris is very broken in Yuzu. It only shows a couple of intro logos before gettings
stuck in an infinite loop.
```
