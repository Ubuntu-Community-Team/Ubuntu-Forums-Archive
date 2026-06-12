---
title: "command-line == difficult?"
date: 2011-05-31
forum: General Help
---

### Post by micha8l on 2011-05-31
Is it just me or is there some secret to using command lines like bash? Maybe it's because I am so used to using GUIs that I'm so poor at using the command line. I find every time I download and install a new program (that probably does a really good job despite there being no GUI) I delete it out of frustration.

I know there's 'help' or '?; or 'man', but all these seem to do is add an additional layers of complexity, or a huge list of commands with names that barely explain their usage. Whereas in GUIs the command and input parameters are clear; it's just click > read > type > job done.

I understand making GUIs for large programs is difficult, but is there anything that can lighten this 'transition barrier' from GUIs to command lines?

---

### Post by Thewhistlingwind on 2011-05-31
> **micha8l said:**
> 
I understand making GUIs for large programs is difficult, but is there anything that can lighten this 'transition barrier' from GUIs to command lines?

Start thinking of the GUI in terms of the commandline. Not explicitly, but remember that theres two ways to get somewhere, one just asks for a lot more characters.

---

### Post by jerrrys on 2011-05-31
heres a place to start

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=cli&as_qdr=all&sa=Google+Search&lang=en#836](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=cli&as_qdr=all&sa=Google+Search&lang=en#836)

---

### Post by dFlyer on 2011-05-31
Open a terminal and enter

man bash

This is the bash manual for ubuntu

---

### Post by Thewhistlingwind on 2011-05-31
> **dFlyer said:**
> Open a terminal and enter

man bash

This is the bash manual for ubuntu

If you need to scroll quickly, hold the f key. Also, to read regular files like the man pages, use the less command.

---

### Post by coldraven on 2011-05-31
I can backup my Nokia phone via Bluetooth in one line, like this
```
gammu --backup my_nokia.ldif
```
How hard is that? What do you guess the command to restore it is?

---

### Post by oldos2er on 2011-05-31
Which CLI programs are you wanting to use?

---

### Post by WorMzy on 2011-05-31
There's no real "secret" to using the command line, but you can't just go from being GUI-dependent to a CLI guru in one step. Take it one step at a time; start with the basics (e.g. cd = change directory, ls = list directory contents, mv = move a file or directory, cp = copy a file or directory), then move on to some more complicated things from there.

---

### Post by Grenage on 2011-05-31
> **micha8l said:**
> Is it just me or is there some secret to using command lines like bash? Maybe it's because I am so used to using GUIs that I'm so poor at using the command line. I find every time I download and install a new program (that probably does a really good job despite there being no GUI) I delete it out of frustration.

I know there's 'help' or '?; or 'man', but all these seem to do is add an additional layers of complexity, or a huge list of commands with names that barely explain their usage. Whereas in GUIs the command and input parameters are clear; it's just click > read > type > job done.

I understand making GUIs for large programs is difficult, but is there anything that can lighten this 'transition barrier' from GUIs to command lines?

It can be a pain, but there are some good reasons for the CLI; that said, there are many good reasons for a GUI.  There are plenty of programs that offer both.

Ultimately I want CLI if I'm going to use an application in a script (encoding, for example), and a CLI if I am not.

---

### Post by iclestu on 2011-05-31
> **Grenage said:**
> .....
Ultimately I want **CLI** if I'm going to use an application in a script (encoding, for example), and a **CLI** if I am not.

lol - typo or clever pun!?

---

### Post by Grenage on 2011-05-31
Alas, a typo; I am so damn tired, it's a miracle I was even typing on the right keyboard.

---

### Post by Swagman on 2011-05-31
But I want the shell

;)

---

### Post by Habitual on 2011-06-01
Add this in a terminal to your .bashrc
```

echo "export LESS='FiX'" >> ~/.bashrc
```
and then
```
source ~/.bashrc
```

type man bash and scroll a page or 2 then Q for exit.
All the man pages outputs will stay on the screen from now on.

That should help.

and visit/bookmark [http://ss64.com/bash/](http://ss64.com/bash/)

---

### Post by sidzen on 2011-06-01
See [http://www.tuxradar.com/content/master-linux-command-line](http://www.tuxradar.com/content/master-linux-command-line)

---

### Post by katykat on 2011-06-01
[QUOTE=micha8l;10883849]Is it just me or is there some secret to using command lines like bash? /QUOTE]

The GUI is nothing but lipstick on a pig.

The bacon is the command line. 

Its the key to using scripts, which are the keys to the kingdom of independence in the cyber world. 

There are, actually only a few commands you really need to learn for the command line. 
ls, clear, cd, export, man, top, killall, shutdown, passwd, chroot  and a few others,  I know I'm forgetting a bunch. 

I use a file manager for all file manipulations as I certainly dont want to make mistakes when moving, copying, deleting files, or when setting permissions or groups. 

Some traditional unix utilities in the textbooks like awk, sed, cut, etc  are better off done in Perl, with its more powerful options and capabilities. 

But most important, is the ability to PIPE commands - where the output of one command is the input to another. When dumped into a simple bash script a string of commands can become a powerful utility, with near infinite variations. 

With a serial port motor controller, you could even have it feed the cat. 
Three times a day. 

The best way to learn the command line and scripting is to determine what you want to do, and then google the heck out of it till you find a scrpt that does something similar, and then google more till you find out what you need to change it into what you want. 

I started off learning Perl by getting a database transfer/translate  script.
That didnt work. 

It took a while, but I got the thing working, and learned a helluva lot in the process. 
It enabled a large database to direclty feed a website. And working scripts were scarce and expensive.

A little motivation goes a long way to learning....

---

### Post by krapp on 2011-06-01
^ Great post, learned a lot, thanks for taking the time.

---

### Post by arvevans on 2011-06-02
In the original UNIX (way before there was a Linux OS) the intent of the command line was to do simple things very fast.  I/O pipes were then used to string these simple commands together to do slightly more complex things.  Next a group of simple commands could be put into a file and executed in sequence to make even more complex commands.

Linux has deviated only slightly from the original shell or command line language.  Most shell or CLI commands are still relatively simple and fast.

A good approach for newcomers to UNIX and Linux (including OS-X, BSD, etc.) is to learn about one CLI command at a time.  Once you have mastered 4 or 5 of the more common ones you can start stringing them together to accomplish more complex tasks.  When you feel comfortable with this you can put several CLI commands into a file, make it executable, and call it your very own new program.

Much of today's Linux administration is still written and executed as shell-script CLI commands.  A great many of the install programs are run as executable files of CLI commands.  In Linux you have CLI or shell script commands, where in Windows you have CLI or batch language commands...it is all pretty much the same thing.  Difference may be that UNIX and it's Linux derivatives have many more CLI commands than might be experienced with Microsoft's CLI language.

_Remember_ "single tasks that run fast" and "linking them together with pipes, or in executable files".  Learn the simple CLI commands first:  cat, cut, grep, col, and so on.  Then go on to more complex commands.

---

### Post by akand074 on 2011-06-02
> **micha8l said:**
> Is it just me or is there some secret to using command lines like bash? Maybe it's because I am so used to using GUIs that I'm so poor at using the command line. I find every time I download and install a new program (that probably does a really good job despite there being no GUI) I delete it out of frustration.

I know there's 'help' or '?; or 'man', but all these seem to do is add an additional layers of complexity, or a huge list of commands with names that barely explain their usage. Whereas in GUIs the command and input parameters are clear; it's just click > read > type > job done.

I understand making GUIs for large programs is difficult, but is there anything that can lighten this 'transition barrier' from GUIs to command lines?

Honestly I use a number of command line apps, I don't think most people know the commands off heart except ones you use often. I know I don't. Really you just need to look up the commands you'll need and just save them somewhere and copy/paste them or look at them for reference when you forget. If you use it often enough, you'll start just remembering off top of your head and you'll understand what each part of the command does as you tweak it. It might be more difficult/time consuming than GUI for some at first, but after you get the hang of it, it's a lot faster.

---

### Post by Habitual on 2011-06-02
> **katykat said:**
> The GUI is nothing but lipstick on a pig.
The bacon is the command line.

Classic.

---

