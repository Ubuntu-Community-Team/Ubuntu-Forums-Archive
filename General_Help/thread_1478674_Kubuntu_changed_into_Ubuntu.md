---
title: "Kubuntu changed into Ubuntu"
date: 2010-05-10
forum: General Help
---

### Post by shaneg-nz on 2010-05-10
So was on the internet reading a story about a guy who is auctioning off  virgins in Nevada.... 

And my system hangs...  so    "Alt+PrtScreen +R+EI+S+U+B"

And now i have Ubuntu.... all my kde  stuff is on it, all my apps and my AWN dock, but ubuntu panels.

I  thought i read somewhere yesterday on here it couldnt happen...

Well  its happened. 


How to fix it? 

[IMG]http://kubuntuforums.net/forums/index.php?action=dlattach;topic=3111751.0;attach=6891;image[/IMG]

---

### Post by James78 on 2010-05-10
Screenshot??

---

### Post by Ubuntiac on 2010-05-10
First up, make sure you get your bid in on one of those Nevada virgins. Second, make sure you pick a virgin, who is skilled in the use of K/Ubuntu Linux.

Hey, they'll probably just do sudo apt-get install kubuntu-desktop && sudo apt-get remove ubuntu-desktop but virgins are wacky so you never know what they'll try.

Also make sure they look at what is going to be removed in the second command. If something pulled in ubuntu-desktop, there's a chance it will be removed. :/ Ask virgin for details.

Anyway, good luck and happy bidding.

---

### Post by shaneg-nz on 2010-05-10
[http://lifestyle.msn.co.nz/nzmenslifestyle/latestnews/1050391/documentary-about-people-selling-their-virginity-to-go-ahead](http://lifestyle.msn.co.nz/nzmenslifestyle/latestnews/1050391/documentary-about-people-selling-their-virginity-to-go-ahead)

Here is the story.. enjoy hahaha


thanks will give it a go, didnt want to try anything incase it rooted my bootmanager like when i updated to lucid...  still cant boot into vista.. not that i need to though.

---

### Post by shaneg-nz on 2010-05-10
> **James78 said:**
> Screenshot??


umm its already up.

---

### Post by shaneg-nz on 2010-05-10
[B]

darkhorse@darkhorse:~$ _sudo apt-get install kubuntu-desktop_
[sudo] password for darkhorse: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
darkhorse@darkhorse:~$ _sudo apt-get remove ubuntu-desktop_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
darkhorse@darkhorse:~$ [/B]

---

### Post by lisati on 2010-05-10
> **shaneg-nz said:**
> umm its already up.

Where?

---

### Post by Ubuntiac on 2010-05-10
Ok. So have you tried rebooting?

I'd also be curious to see what 4 packages aren't being upgraded. You can see by doing:

sudo apt-get dist-upgrade

WARNING: As in previous suggestion be very careful to check if this operation is asking to remove any packages you need before saying "Yes" to it continuing. (It asks after you enter the command)

PS Your image doesn't show at all in FireFox. Konqueror displays an icon showing an unloadable image.

---

### Post by shaneg-nz on 2010-05-10
ok just rebooted and on gnu grub it had changed from saying Kubuntu to Ubuntu 
the splash screen when i restart says kubuntu

[B]darkhorse@darkhorse:~$ sudo apt-get dist-upgrade
[sudo] password for darkhorse: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-keyring libgcr0 libgp11-0 libpam-gnome-keyring
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,071kB of archives.
After this operation, 4,096B of additional disk space will be used.[/B]

i can see the pic??

ok i added them as attatchments

the second photo has an error with: 
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

---

### Post by shaneg-nz on 2010-05-10
.

---

### Post by shaneg-nz on 2010-05-10
..

---

### Post by shaneg-nz on 2010-05-10
ok.... i fixed it

still dont know how it installed itself, and as you can see the package wasnt installed, 
so i ask why is it there taking up space on my hdd?

[http://www.watchingthenet.com/switch-between-gnome-and-kde-desktops-in-ubuntu-or-kubuntu.html](http://www.watchingthenet.com/switch-between-gnome-and-kde-desktops-in-ubuntu-or-kubuntu.html)

sooo easy 
anyway glad to be back on kde, sorry gnome guys, but its not my cup of tea.
but it is quite cool if both packages are installed you can switch between them.

---

