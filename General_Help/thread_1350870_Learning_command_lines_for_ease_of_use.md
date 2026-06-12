---
title: "Learning command lines for ease of use ?"
date: 2009-12-09
forum: General Help
---

### Post by aklo on 2009-12-09
I noticed something...apart installing stuff from the software center, most other software requires some sort of command line input...

sudo blah blah (whatever it means)

Would it enchance my experience of using linux(ubuntu) if i dedicate some time to learning those commands?

Right now i'm having trouble installing songbird with the .tag.gz files and i found the solution ...man was the solution long...

---

### Post by chaanakya_chiraag on 2009-12-09
Trust me, it's **really** worth the time to learn some basic terminal commands like ls, aptitude install, aptitude remove, cd, etc.  I mean, I can upgrade my whole system with **one** command.  Now can you do that with Window$?  I don't think so!! :D

---

### Post by llamabr on 2009-12-09
I don't know what songbird is, but probably there's something in the repos that does it.  What does it do?

brock@hops:~$ apt-cache search songbird
pidgin-musictracker - Plugin for Pidgin which displays the current music track in your status
brock@hops:~$ 

Regarding the cli, I find that you'll learn it as you need to.  Most things can be accomplished with a gui, and someday you'll be doing something repetative, and realize that computers are better suited for repetative tasks than you, and you'll look up a script to do it.

In the mean time, if you don't know why you need the cli, you probably don't.

---

### Post by chaanakya_chiraag on 2009-12-09
By the way, the command sudo gives you admin privileges.  This prefix is required by all commands that might possible affect system stability and things that play with OS files.  Therefore, you need it to install/remove software, edit/delete certain files, etc.

---

### Post by chaanakya_chiraag on 2009-12-09
Songbird is a media player, like Rhythmbox, Totem, Banshee, Exaile, etc.

---

### Post by chaanakya_chiraag on 2009-12-09
Also, to "install" Songbird, just extract the archive you downloaded.  That's it!  Download the Songbird archive here:[URL="http://download.songbirdnest.com/installer/linux/i686/Songbird_1.2.0-1146_linux-i686.tar.gz"]
http://download.songbirdnest.com/installer/linux/i686/Songbird_1.2.0-1146_linux-i686.tar.gz[/URL]

---

### Post by audiomick on 2009-12-09
In my experience, most software doesn't need the command line if you are installing from the standard repositories and know how to use the relevant functions on the graphical user interface.

llamabr is right to an extent: if you don't know why you need the command line interface, don't worry about it too much.

On the other hand, there are a lot of things that are simply easier or quicker if you know a few commands. It is worth finding out a bit about the command line interface.

---

### Post by chaanakya_chiraag on 2009-12-09
If you want a menu item, go to System->Preferences->Main Menu.  Click on the "Sound & Video" thing on the left sidebar.  Click on "New Item" and name it Songbird.  Click on "Browse" and go to where you saved the extracted Songbird directory.  Inside that, you will find a "songbird" file, which is the one you want to run, so select that file.  Click "Ok" and you should be good!

---

### Post by chaanakya_chiraag on 2009-12-09
Another good reason to learn a bit about the command line is that you can't be conned by some (dangerous) prankster who decides to "help" someone by giving him/her the command to delete everything on his/her hard drive.

---

### Post by Finalfantasykid on 2009-12-09
Alot of the time, there are .deb packages of popular programs, which makes installing the programs much easier.

[http://www.getdeb.net/software/Songbird](http://www.getdeb.net/software/Songbird)  There is songbird :)

But even though the command line may seem a little bit challenging right now, over time you will probably grow to really like it(at least if you are a computer n3rd :P).  If there is a command that you do not understand, just type

```
man command_name_here
```

That should give you some information on the program's usage, though understanding it is another thing entirely ;)

---

### Post by chillyomi on 2009-12-09
yes learning some basic commands would be a good perk;)

---

### Post by NT4usB on 2009-12-09
Anything you can do in Linux via GUI, you can do via command line.
You cannot do everything in Linux via GUI but you can do everything via command line.

Tab autocomplete is your friend.

Type:```
$ sudo bla
```followed by the Tab key autocompletes to```
$sudo bla bla
``` Well, not really since bla is not a command.

If one Tab doesn't return anything, two Tabs will show all the options that begin with 'bla'.

```
$ apropos bla
``` will tell you what bla does.

Note:```
$ apro
``` Then Tab, autocompletes to ```
$ apropos
``` since I can never remember how to spell apropos...

Typing/long/paths/to/file/or/folders is a bother, but Tab will work there too. 
Tab once completes the name up to the next '/' or two Tabs to see your choices. 
Add a couple more letters, to make it unique, Tab again and you're off!

Useful if you have file or folder names that have spaces or punctuation that you're not sure how to properly 'escape.'

---

### Post by ManyBeers on 2009-12-09
> **chaanakya_chiraag said:**
> If you want a menu item, go to System->Preferences->Main Menu.  Click on the "Sound & Video" thing on the left sidebar.  Click on "New Item" and name it Songbird.  Click on "Browse" and go to where you saved the extracted Songbird directory.  Inside that, you will find a "songbird" file, which is the one you want to run, so select that file.  Click "Ok" and you should be good!

Thanks to this post I was finally able to get a 
game I had installed to my Home folder on the Main Menu where it belongs.

---

### Post by NFblaze on 2009-12-09
Yes, learn the commandline/shell. It can be very very useful. Especially when you want to get down to power usage and make scripts. I've been using Ubuntu for about a year. I think the shell and shell scripting is pretty powerful. 

Though, if you will just be doing cursory usage, then no it's not a necessary to get that involved in it besides the general stuff like cp,mv,mkdir,ls,dpkg/apt/aptitude,man. Also, I would learn how to compile programs. All, that lightweight stuff.

---

### Post by deathbyswiftwind on 2009-12-10
Yes its definatly worth while to learn some command lines. Say for instance you go to login one day after an update and your x gets broken and you drop to a terminal. Most of the time with a little bit of anger and command lines you can have everything up and running in a few minutes. Not knowing any of the commands youd probably just end up formatting and losing everything. No thanks!

---

### Post by SuperSonic4 on 2009-12-10
I'd say so, the terminal is a lot more efficient

---

### Post by hobit on 2009-12-10
Yes, knowing the command line, scripting etc. is very useful and will help if you ever decide to try other flavours of Linux / Unix.

You might find this page useful, [http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

When in doubt use man or google the command.

---

### Post by anonSam on 2009-12-10
There's a real nice tutorial here just about anyone can follow:

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by chaanakya_chiraag on 2009-12-10
> **ManyBeers said:**
> Thanks to this post I was finally able to get a 
game I had installed to my Home folder on the Main Menu where it belongs.

Glad I was able to help! :)

---

