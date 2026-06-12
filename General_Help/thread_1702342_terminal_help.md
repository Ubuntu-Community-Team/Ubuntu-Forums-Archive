---
title: "terminal help"
date: 2011-03-07
forum: General Help
---

### Post by btf18 on 2011-03-07
Hi there,

I know how to open files and directories on my laptop from the terminal using the command gnome-open 'random file'. But i was wondering if it is possible to open applications, for example rythmbox music player. I havent figured out how, and i don't know how to find where rythmbox is located in my computer. Also, is there a way to search your pc from the terminal for files, directories, and applications, if you do not know where they are?

Thank you

---

### Post by xtremesupremacy3 on 2011-03-07
Don't worry, the terminal is pretty easy once you get used to it, it's nice to see someone trying it though.

With applications its simple. Most applications can be started up in a terminal just by typing their name
```
rhythmbox
```
Will open rhythmbox
```
firefox
```
will open firefox etc

Try the command 'find' for searching.

To find out more about the command try the manual:
```
man find
```

---

### Post by wiggly81 on 2011-03-07
to open rhythmbox type
```
rhythmbox
```

is that half of what you wanted ?

---

### Post by xtremesupremacy3 on 2011-03-07
With finding something in a terminal it can work like this:

first you issue the command 'find' followed by the directory to look in, and then for instance what it's looking on, followed by the criteria.

For example, if i want to see if there is a music file called abc.mp3 that I want to find somewhere in my homedirectory...I would issue this command:

```
find ~ -name "abc.mp3"
```
as you can tell I told it to look in the home directory (~) and that I'm searching on a name (-name) and finally the name of the song.

if you dont know something or want a longer list there is the wildcard.

Let's say I want a list of all mp3's I replace the name with an star like this:

```
find ~ -name "*.mp3"
```

Does that help at all?

---

### Post by AlphaLexman on 2011-03-07
Sometimes a system may have more than one version of a program...
```
which program_name
```
would output the path to the default choice.

And,
```
locate program_name
```
would output ALL program_name available.

---

### Post by btf18 on 2011-03-07
Thanks all. That was a great help. It may just take a few attempts to find what ubuntu calls some apps in the shell, like mozilla firefox is just firefox and rhythmbox music player is just rhythmbox. Also, thanks for the find command. I haven't managed to successfully find something with it yet. For example i tried to find a song, so i typed find /home/ben 'name of song.mp3', and it showed the list it was searching through, it even did go show the exact file i was looking for in the list, but at the bottom it said no such file or directory. I know i typed the filename correctly as i've been doing many commands such as cp, mv, rm, chown, chmod on this file. I will keep trying to learn about the find command. But Im just curious where the applications are located on my computer such as rhythmbox, like what directory they are in. Does anyone know? Or is that something ubuntu doesnt want us to know/dont need to know?

---

### Post by btf18 on 2011-03-07
Actually i didnt see alphalexmans reply, and i think that did help, as locate rhythmbox shows me its in a variety of directories. Which rhythmbox shows me however that it is located in /usr/bin/rhythmbox. Im a bit confused about this result. /usr/bin/rhythmbox must be the location of the default rhythmbox. Thank you Alpha

Locate is really working for me to find files
which is working for apps

awesome guys, cheers

---

### Post by AlphaLexman on 2011-03-07
Another awesome search method is the command: **apropos** from the terminal.
If you want to search your machine for programs related to say, **pdf**'s, you would type:
```
apropos [COLOR="Blue"]pdf[/COLOR]
```
and enjoy the results!

---

### Post by wojox on 2011-03-07
> **btf18 said:**
> Thanks all. That was a great help. It may just take a few attempts to find what ubuntu calls some apps in the shell, like mozilla firefox is just firefox and rhythmbox music player is just rhythmbox. Also, thanks for the find command. I haven't managed to successfully find something with it yet. For example i tried to find a song, so i typed find /home/ben 'name of song.mp3', and it showed the list it was searching through, it even did go show the exact file i was looking for in the list, but at the bottom it said no such file or directory. I know i typed the filename correctly as i've been doing many commands such as cp, mv, rm, chown, chmod on this file. I will keep trying to learn about the find command. But Im just curious where the applications are located on my computer such as rhythmbox, like what directory they are in. Does anyone know? Or is that something ubuntu doesnt want us to know/dont need to know?

To find an mp3 try:

```
$ find /home/ben -name '*.mp3'
```

---

### Post by btf18 on 2011-03-07
Thanks wojox, so if the songs filename is "01 Beast and the Harlot.mp3" I would type: find /home/ben '01 Beast and the Harlot.mp3' '*.mp3'     ?

or maybe the same but with the dash before the name like this:

"01 Beast and the Harlot.mp3" I would type: find /home/ben -'01 Beast and the Harlot.mp3' '*.mp3'
?

And thanks lexman, i will test that command out :-)

---

### Post by AlphaLexman on 2011-03-07
I'm sorry for pointing you to **pdf** advice, I was helping on two different threads, and got confused, hopefully you can logically replace pdf with mp3!
> I would type: find /home/ben -'01 Beast and the Harlot.mp3' '*.mp3'
?is wrong, you are trying to find files ***.mp3.mp3** and you probably don't have double filename extensions!

A generic *.mp3 find would be as wojox suggested:
```
$ find /home/ben -name '*.mp3'
```

If you are looking for a specific file as you mentioned, then
```
find /home/ben -name "01 Beast and the Harlot.mp3"
``` will search recursively through all sub-directories to find the exact file.

---

### Post by btf18 on 2011-03-08
Thanks alpha :-) Im just not sure what goes in place of -name..?

---

### Post by AlphaLexman on 2011-03-08
> **btf18 said:**
> Thanks alpha :-) Im just not sure what goes in place of -name..?
The **find** command has OPTIONS, TESTS, and ACTIONS

The -name is a TEST to check for filenames matching an expression, such as [COLOR="Blue"]'*.mp3'[/COLOR].

If you want another TEST for your find command look at...
```
man find |less +/"TESTS"
```

---

### Post by btf18 on 2011-03-08
awesome it works xD Thanks. So basically in the code you just wrote, man is like a "manual" command in this case for the manual of the command find, the | is a pipe used to connect the commands 'man find' and 'less +/"tests"', and less is to view the readme of it and tests is to show the different tests you can do to find? >.<

---

### Post by AlphaLexman on 2011-03-08
Yes **man** is equivalent to a manual, and the '|' is actually a **pipe** command, and the **less** statement is replacing the $PAGER variable, and the '+/' is the external search keystroke in **less** to search for a sequence.

---

### Post by btf18 on 2011-03-08
Thanks ^^

I would say this thread is well and truly solved!

---

