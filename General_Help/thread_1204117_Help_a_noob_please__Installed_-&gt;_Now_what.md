---
title: "Help a noob please?  Installed -&gt; Now what?"
date: 2009-07-04
forum: General Help
---

### Post by jdm63nva on 2009-07-04
Hey everyone,

I'm about as new to linux as they come. Fresh off the Windows XP vine so to speak. I have a spare 2.2ghz P4 box that I decided to give ubuntu a try after hearing some talk about it. Lastnight I successfully installed v9.0.4  or rather it looks like everything is working right up to the point where I'm trying to add new applications to the application menu. It appears I'm missing the System tools menu of applications.  How do I get that back?

Also, whenever I try to run sudo commands I'm told I don't have access.

Aside from all this, now that I have it installed.. I'm lost. Where do I start?  One of the things I'd like to do is share files on my home network, however my other Windows computers are in another workgroup. 

Thanks a bunch,

Jim

---

### Post by DeMus on 2009-07-04
> **jdm63nva said:**
> Hey everyone,

I'm about as new to linux as they come. Fresh off the Windows XP vine so to speak. I have a spare 2.2ghz P4 box that I decided to give ubuntu a try after hearing some talk about it. Lastnight I successfully installed v9.0.4  or rather it looks like everything is working right up to the point where I'm trying to add new applications to the application menu. It appears I'm missing the System tools menu of applications.  How do I get that back?

Also, whenever I try to run sudo commands I'm told I don't have access.

Aside from all this, now that I have it installed.. I'm lost. Where do I start?  One of the things I'd like to do is share files on my home network, however my other Windows computers are in another workgroup. 

Thanks a bunch,

Jim

Hi Jim, welcome in the wonderful world of Linux.

First, how did you install Ubuntu? From the CD on a clean disk, or did you use Wubi, or a virtual machine?
During installation it asks you to add a user. Most people type as username their own name or nickname. You also have to type a password (double to eliminate errors). This user is granted sudo rights whenever needed. Every time you need to do something as root (administrator) you have to type your password to tell the system it is really you.
Then you should be granted the rights to perform root's tasks.

What exactly do you mean with adding new applications to the applications menu?
You want to install new software, or what? Please explain so we can help.

For sharing files on your home network, you have to install Samba, which is a program which manages the layer between Windows and Linux on a network.
Go to: System > Administration > Synaptic.
In the search field type samba
Click on the little square box at the beginning of the line which says Samba and choose install. It will probably install several other things it is depending on. Just accept that and in the button bar at the top of the screen choose Apply.
Now when you open Nautilus (the file manager) you can choose a network on the left side of the screen. On the right it will show you an icon, double click it and so on. Until you find your Windows disks.
It's not that difficult.
Have fun with this new (for you) operating system.

---

### Post by tuskenraider on 2009-07-04
well.... the workgroup thing is solved here
[http://ubuntuforums.org/showthread.php?t=392088](http://ubuntuforums.org/showthread.php?t=392088)

the sudo thing... copy paste what it says... i prob cant help with that... well i can say verify that you are typing in the correct password for root "admin" privledges. num lock on? caps lock? sorry just have to ask...  

and right click the bar at the top or bottom of your screen and add to bar...  or what ever it says... and then add the menu...  itll be in there... should be... beyond that.. i cant help..

hey... 1/3 aint bad i dont spose.. lol 

tusken-not so fantastic linux user lol -raider

---

