---
title: "how on earth do i uninstall this beta vesion of adobe flash 10.1"
date: 2010-02-18
forum: General Help
---

### Post by Jfuse on 2010-02-18
why is everything with this ubuntu so complex and difficult? this operating system turns the act of installing/uninstalling into a huge task let me tell ya.

just yesterday I installed the beta release of flash 10.1, i thought that it went into my firefox folder, but i checked firefox 3.5.7 plugins and it isn't there.

so my question is, where on earth could it have possibly gone? terminal said that it installed somewhere on my home directory, but i've been searching everywhere and i can't find anything. i know it's there because videos require flash WORK. where is my home directory, and what is it?

can someone help me find this so i can delete/uninstall it? i'm using ubuntu 9.10.

---

### Post by tom4everitt on 2010-02-18
Ubuntu is actually pretty simple when it comes to installing/uninstalling:

To install:
sudo aptitude install name-of-package

To uninstall:
sudo aptitude remove name-of-package

So the easy way to install/unistall flash is 
sudo aptitude install/remove flashplugin-nonfree
(this does not apply to you now, since you installed it another way, but it can be good to remember).


Now to your problem:
How does the terminal say its in your home folder? Cause if it says its there, it probably gives you the exact place?

Your home directory is simply the directory in which files that belongs to you as a user, rather than to the system, is stored. Its path is /home/name-of-your-user.
You can also open it by clicking places->Home Folder in the top left menu.

---

### Post by tom4everitt on 2010-02-18
Oh, and the really quick way to remove it is probably:

rm -rf ~/.mozilla

If your fine with deleting all your bookmarks etc.. (and emails if you're using thunderbird as email client). 

This will delete your personal mozilla-folder, which is probably the place where flash was installed (if you installed it through firefox).

---

### Post by Seq on 2010-02-18
Have you checked ~/.mozilla/plugins?

You installed it from a terminal? What command did you use to install it? (I'm assuming it wasn't with apt since it is the 10.1 beta)

---

### Post by mkvnmtr on 2010-02-18
Have ypu by chance ñooked in the .adobe file in home?

---

### Post by lovinglinux on 2010-02-19
For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

