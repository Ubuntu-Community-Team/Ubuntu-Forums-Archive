---
title: "[HOWTO] add an autocomplete file extension in bash shell"
date: 2011-11-24
forum: General Help
---

### Post by skief on 2011-11-24
**This HOWTO is for you if:**

[I]You have a command "somecommand" which you type at the Bash prompt,
  and you would like it to be associated with a certain file extension, "ext" say.[/I]

Surprisingly, googling "ubuntu bash completion file extension" did not bring up any Ubuntu Forums hits on the first page, and none of the results seemed to directly address my question. Hence this HOWTO.


**Short and sweet...**
You need only add the line
```

complete -f -X '!*.ext' somecommand

```
to your .bashrc file.

To be perfectly clear on what this will achieve, consider the following example. Suppose you were in a directory that had exactly two files in it,
```

foo.txt
foo.ext

```
**Before** adding the 'complete' command to bashrc, typing
```

somecommand foo

```
and then pressing TAB would result in
```

somecommand foo.

```
since there is no preference associating 'somecommand' with the extension 'ext'.
**After** adding the 'complete' command, pressing TAB would produce
```

somecommand foo.ext

```
as desired.


**If you want to know more...**
Scads of such 'complete' commands are written in the file /etc/bash_completion, and you may work by example if you want to do fancier things, like associating several different file extensions with a single command.

It may be that the proper or preferred way to add your own commands is to create new files in the directory /etc/bash_completion.d, rather than simply adding lines to your bashrc. I cannot speak with any authority on this.

This page,
[http://www.debian-administration.org/article/316/An_introduction_to_bash_completion_part_1](http://www.debian-administration.org/article/316/An_introduction_to_bash_completion_part_1)
and the Part 2 that follows it, are rather informative.

Good luck. :)

---

