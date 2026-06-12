---
title: "terminal"
date: 2009-11-18
forum: General Help
---

### Post by rbee on 2009-11-18
simple question needs simple answer----how do you use terminal--i "sudo apt-get upgrade" how do i get it to install..or i copy/paste into terminal..how do i install

---

### Post by emigrant on 2009-11-18
i wonder whether you are a bot :D
any way start from here:
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

---

### Post by hwttdz on 2009-11-18
Ok, it seems there are a few questions here, 

1) how do I open a terminal
applications->accessories->terminal 

2)  how do I update/install programs?
There are a few commands to know here, first sudo gives you admin powers, which is necessary to update programs but should also be scary, because it gives you real power to break your system.  So when running a command using sudo make extra sure you know what you're doing, you will get no "are you sure you want to do this" dialogue box.  
Next apt is the program used to manage the software installed on your ubuntu box, apt gets all it's knowledge from a repository, in order to get fresh knowledge from the repository you have to ask apt to update "apt-get update", but as this is a system admin task you need admin powers to run it so run "sudo apt-get update", it will ask you for your password (you will see no stars, just type it in and press enter).
Now you have fresh knowledge of packages, you can ask apt to upgrade all your software to the current version "sudo apt-get upgrade".
And if you want apt to install or remove a package just say "sudo apt-get install packagename" or "sudo apt-get remove packagename".

Simple enough?  You can also do most of what you can do with apt using a graphical interface in synaptic.

---

### Post by fluffman86 on 2009-11-18
I'm really not following your English here, sorry, but I'll try anyway:

1. Go to Applications > Accessories > Terminal

2. Type:
```
sudo apt-get update
```
to update your database of available applications

3. Type:
```
sudo apt-get upgrade
```
to upgrade to the latest versions of all of your installed applications.

4. Type:
```
sudo apt-cache search SEARCHTERM
```
to search for available programs

5. Type:
```
sudo apt-get install PROGRAMNAME
```
to install a program

Hope that helps!

edit: re-reading you post, I see you also want to copy/paste into terminal.  There are 3 ways to do this in Linux:
1. You can highlight something, and then middle-click with your mouse.  This uses clipboard #1.
2. You can highlight something, then use the "Edit" menu at the top of the program you are using to copy, and then Edit > Paste.  This uses clipboard #2.
3. You can highlight something, then press CTRL+C (hold Ctrl, then press C and release), to copy, and CTRL+V to paste.  This also uses clipboard #2.

Both of the 2 clipboards work independently of each other, so you can CTRL+C to copy one thing, then highlight something else, and you have 2 copies of something ready to pate--one with the middle-mouse button and the other with CTRL+V.

Note: The terminal can't read or understand CTRL+C or CTRL+V alone, so when in there you can either use Method 1 or Method 2 above, or you can use CTRL+SHIFT+C and CTRL+SHIFT+V.

edit #2: The terminal is very powerful and very fast, but it's not always very easy to use if you don't know what you're doing.  You can do all of the installing you need by going to System > Administration > Synaptic, as hwttdz suggested.  Synaptic is also very powerful, but again, sometimes not very easy to use.  The easiest way to get programs is with Applications > Ubuntu Software Center (in Karmic) or Add/Remove Programs (anything pre-Karmic, like Jaunty, Intrepid, and Hardy).

---

