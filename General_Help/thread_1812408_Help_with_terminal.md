---
title: "Help with terminal?"
date: 2011-07-26
forum: General Help
---

### Post by QuantumMonkey on 2011-07-26
I got Ubuntu 11.04 yesterday, and I'm loving it. I've successfully installed Compiz and its awesome cube and other eye-candy, but I was told by a friend that the thing that I will be using the most in Linux is the Terminal. 

I'm not quite sure what you would do with the Terminal, apart from updating and installing software. Can anyone give me some pointers as to what I will be needing the terminal for and how it will benefit me? :D

---

### Post by haqking on 2011-07-26
> **QuantumMonkey said:**
> I got Ubuntu 11.04 yesterday, and I'm loving it. I've successfully installed Compiz and its awesome cube and other eye-candy, but I was told by a friend that the thing that I will be using the most in Linux is the Terminal. 

I'm not quite sure what you would do with the Terminal, apart from updating and installing software. Can anyone give me some pointers as to what I will be needing the terminal for and how it will benefit me? :D


Well the power lies at terminal.

However with the GUI these days if there is something you cant do then you can probably do it in the terminal.

If you need to ask what you can use the terminal for then you probably dont need it yet so dont worry about it.

however come the time you do then see here:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

and there are lots of resources online to help learn the commands needed such as :

[http://linuxcommand.org/](http://linuxcommand.org/)

and the 2 most useful comands i use are 

man (manual pages for a command etc) such as man cp to see how to use the copy (cp) command
and

apropos

which allows you to find the appropriate command when you dont know what it is ;-)

---

### Post by QuantumMonkey on 2011-07-26
Thanks a lot, I was worried that I was using Ubuntu wrong, I've only touched it to install Compiz :P

---

### Post by oldsoundguy on 2011-07-26
To USE Ubuntu and the majority of the programs in the repositories, the use of terminal is NOT required. (the new user friendly aspect of Ubuntu) When you start delving into programs from outside sources (the newer cutting edge versions for instance) or when you  want to open up the hood of Ubuntu and peer inside and either fix or change things more to your liking, THEN you will start using terminal.

Terminal is just like the Windows CMD window in principle .. however, in Ubuntu and Linux in general it can become a much more powerful tool.

Initially, when you start using it, you will be cutting and pasting your commands and code from some web page or even here on the forums.  Then you will be using simple commands (like getting a list of your hardware or testing ports or checking to see what you have loaded and so on).  After that, the sky is the limit.

It is NOT the scary thing that the Windows fanbuyoys get all worked up about.  
At one time, it was the ONLY way to get things done in Linux and there are certain Linux users that want it to go back to that point as they really don't want "dumb newbies" using "their system". Pandora's box is open. No going back. It's a good thing.

---

### Post by seawolf167 on 2011-07-26
As an example of the power of command-line arguments, take a look at the link "LinuxCommands" in my signature, or randomly pick a command and browse it's man page to see how many options are available.

i.e. type

```
man rsync
```

to see all the different command line ways this particular one program can be utilized.

---

### Post by AlphaLexman on 2011-07-26
I think the 'find' command was my first foray at the terminal...
```
man find
```
Good Luck!

---

### Post by nothingspecial on 2011-07-26
> **QuantumMonkey said:**
> 

I'm not quite sure what you would do with the Terminal, apart from updating and installing software. Can anyone give me some pointers as to what I will be needing the terminal for and how it will benefit me? :D

Heres my 2 pointers


You can listen to punk.

These next 3 lines are only needed once, one at a time.

```
sudo apt-get install mplayer
 echo "alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'" | tee -a ~/.bash_aliases
. ~/.bashrc

```

Now every time you want to listen to some punk, open up a terminal (Ctrl-Alt-T) and type 

```
punk
```

or you can look up tectonic plates on wikipedia

Again, these 5 lines set it up, you only have to do them once.

```
sudo apt-get install surfraw elinks
mkdir $HOME/.config/surfraw/
echo -e "SURFRAW_graphical=no"'\n'"SURFRAW_text_browser=/usr/bin/elinks" > $HOME/.config/surfraw/conf
surfraw-update-path -add -all
. ~/.bashrc
```

Now look up those plates

```
wikipedia tectonic plates
```

or google for ubuntu terminal

```
google ubuntu terminal
```



Of course you can do anything you want with a terminal. It's up to you.

Have fun :popcorn:

---

