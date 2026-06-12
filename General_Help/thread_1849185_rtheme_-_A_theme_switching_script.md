---
title: "rtheme - A theme switching script"
date: 2011-09-24
forum: General Help
---

### Post by vehemoth on 2011-09-24
[B][U][SIZE=3][COLOR=Blue]Intro

[/COLOR][/SIZE][/U][/B][SIZE=3][COLOR=Blue][COLOR=Black][SIZE=2]This is a simple script designed for automatic switching of themes, it is designed to be run at login but could also be run using other methods. It is written in bash but may switch languages in the future.

There is  a README included in the archive, I suggest that you give it at least a quick read over before trying to use the script

[/SIZE][/COLOR][/COLOR][/SIZE]**_[SIZE=3][COLOR=Blue]Usage Help[/COLOR][/SIZE]_**

You can get the current help options at any time by running (change the path as necessary):

```

rtheme -h

```or
```

 rtheme --help

```     ```

Usage: rtheme [OPTION]...
rtheme changes the theme according to conditions
Example: rtheme --gtk2 Clearlooks

Common options:
  -h, --help        Displays this help message

Change setting using database:
  -r, --random        Random new theme from database
  -n, --next        Next numerical theme in database
  -p, --previous    Previous theme from database
  -t, --theme        Theme from database by number

Notes
  If conflicting modes are selected, the first mode will be used without warning (even in verbose mode)

```**_[SIZE=3][COLOR=Blue]Please Note[/COLOR][/SIZE]_**[SIZE=3][COLOR=Blue][SIZE=2][COLOR=Black]

This script is licensed under the latest version of the GPL at time of reading this. The latest version at time of last update is GPLv3 the license terms can be found at [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

Any feedback, bug reports and contributions will be greatly appreciated but mightn't be attended to for a few days.
[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by raja.genupula on 2011-09-24
nice job man , i will try this now .
keep it up .

---

### Post by vehemoth on 2011-10-23
**[COLOR=Red][SIZE=4]UPDATE[/SIZE][/COLOR]**

Updates as follows:

[LIST]
[*]Added more options these can be seen in help (-h, --help and in first post)
[/LIST]

[LIST]
[*]Fixed a bug which occured if you had multiple entries in the database that used the same theme
[/LIST]
Planned features:

[LIST]
[*]More options
[*]Verbose mode
[*]Cleaning up of code
[/LIST]

---

