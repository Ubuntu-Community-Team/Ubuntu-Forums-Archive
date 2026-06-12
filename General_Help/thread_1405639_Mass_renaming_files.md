---
title: "Mass renaming files"
date: 2010-02-12
forum: General Help
---

### Post by blueshiftoverwatch on 2010-02-12
I have a folder with various subfolders of files. These files all have two extra characters on the end that I want to get rid of.

How would I go about telling the terminal to go into X directory and every subdirectory of X directory, look for all files with the extra characters, remove them, and keep everything else the same?

---

### Post by kaibob on 2010-02-12
The following is the command I use to recursively rename files. You have to change target directory and old (the characters you want to remove). You probably don't need -name '*.ext'. The $ after old tells rename only to remove from the end of the file name. If you provide some examples, we can give you something more specific.

```
find /target/directory -name '*.ext' -type f -exec rename -n 's/old$//' '{}' ';'
```

The -n options does a dry run and reports proposed changes. Substitute -v for -n to actually rename the files

---

### Post by blueshiftoverwatch on 2010-02-13
Thanks, that worked.

Some of these commands are long enough to make your eyes bleed. I don't know how people can make use of them without either copy+pasting them from a text file and modifying the variables. Or using the man function to look up the correct syntax every time.

---

### Post by kaibob on 2010-02-13
Some of these command lines do get a bit long. Over the years, I have used the notecase utility to assemble a large collection of useful command lines that I copy and paste into a terminal window. There's no way I could remember them otherwise. 

Probably not important but Bash 4--which is in karmic--has a globstar shell option that enables recursive globbing with **. This would shorten my earlier command to:

```
shopt -s globstar ; rename -n 's/old$//' **
```

Anyways, glad you got things working with the other command.

---

