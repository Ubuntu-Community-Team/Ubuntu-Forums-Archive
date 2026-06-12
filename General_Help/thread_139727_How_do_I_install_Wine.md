---
title: "How do I install Wine?"
date: 2006-03-04
forum: General Help
---

### Post by maxpayne on 2006-03-04
I want to install wine and I really have no clue.  I was following a tutorial on how to do it.  So far I added a repository to synaptic for wine and searched for the name wine and came up with four things, two I downloaded and applied.  Here is a screenshot.  I have no idea what to do next or if I even downloaded the right thing.  Such a newbie.

---

### Post by Almighty on 2006-03-04
Check out automatix... it makes installing software Microsoft easy.

[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix]("http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix")

---

### Post by maxpayne on 2006-03-04
oh did i mention I am running x64 version lol :(

---

### Post by xhie on 2006-03-04
After you install it with synaptic just check to make sure you have .wine folder in your home directory, if you do then your good to go. From that screenshot it says your installing xwine not wine, is that on purpose?

---

### Post by maxpayne on 2006-03-04
that is the only thing i could find on search...

---

### Post by maxpayne on 2006-03-04
also .wine is not in my home directory... so i think... here is a SS:

---

### Post by stalefries on 2006-03-04
That's because any file that starts with a "." is a hidden file. When you are looking through your home folder, press Ctrl+H, this will show hidden files in Nautilus.

---

### Post by maxpayne on 2006-03-04
It is still not there... so how do I correctly install it?

---

### Post by Lunixfanboy on 2006-03-04
[QUOTE=maxpayne]It is still not there... so how do I correctly install it?[/QUOTE]
Open terminal, or Ctl-Alt-F2 to a console, then simply type wine at a prompt. Since you haven't run it before, first time wine runs, it configures a fake windows drive in the .wine subdirectory off your home directory.

---

### Post by tamarku on 2006-03-05
I too have been having problems getting WINE to work.  It appears to have been installed but I have no idea how to start it.  When I go to a terminal and wine in here is what I get. 

thomas@wintergreen:~$ wine
Wine 0.9.9
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
thomas@wintergreen:~$

Where do I go from here?

---

### Post by jam'ez on 2006-03-14
try to see if you can get on the configure part. in terminal type.
winecfg

---

### Post by aysiu on 2006-03-14
Wine doesn't run by itself.
It's a helper application that runs .exe files.

For more info...
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

