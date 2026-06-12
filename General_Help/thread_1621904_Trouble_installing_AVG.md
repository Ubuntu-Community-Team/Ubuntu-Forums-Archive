---
title: "Trouble installing AVG"
date: 2010-11-14
forum: General Help
---

### Post by alonewestand on 2010-11-14
I have a pretty nasty virus on my Windows boot that won't even give me access to the system restore, so I'm trying to scan the files from Ubuntu and get rid of it.  I followed the guides outlined in this thread [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064) but I get a problem.  The thread states to enter "sudo rm -r /usr/share/applications/avggui.desktop" into the terminal but I get alonewestand@Wraithstorm:~/Desktop$ sudo rm -r /usr/share/applications/avggui.desktop
rm: cannot remove `/usr/share/applications/avggui.desktop': No such file or directory

Then it says to enter sudo nano /usr/share/applications/avg.desktop and enter some information, and save and exit.  But when I go to "file" there is no option to save and exit.  There are some commands at the bottom like ^G Get Help but when I type them nothing happens.  

I could really use some help getting the AVG GUI working so I can get back onto my Windows.

---

### Post by plucky on 2010-11-16
> Then it says to enter sudo nano /usr/share/applications/avg.desktop and enter some information, and save and exit. But when I go to "file" there is no option to save and exit. There are some commands at the bottom like ^G Get Help but when I type them nothing happens.



```

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

The ^ mean type CTRL key on the keyboard.

So CTRL+O will write to the file (Save Contents) and CTRL+X will close the nano window. 

As for AVG I cannot help you there.

Good luck

---

