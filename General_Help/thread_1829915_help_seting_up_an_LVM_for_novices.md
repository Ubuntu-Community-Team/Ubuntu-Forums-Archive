---
title: "help seting up an LVM for novices"
date: 2011-08-20
forum: General Help
---

### Post by 37fleetwood on 2011-08-20
ok, setting up a new system with an encrypted LVM and having a bit of trouble.
so far I haven't found any information on how to ad a new drive to the encrypted volume.
basically I bought 2 new 2tb drives and want to achieve having a 4tb encrypted volume with everything on it. so far, the LVM software has only shown me several ways to totally screw it all up. I've had to re-install like 3 times. I can't figure it out and there doesn't seem to be any instruction manual to that particular piece of software.
I've gotten as far as adding the other drive to the group but can't figure out how to enlarge the lvm into it.:confused:
any help would be thankfully apreciated!

---

### Post by jquis8411 on 2011-08-21
Setting up LVM can be a huge pain with Ubuntu. Are you setting up a server? Fedora may be a better bet for an easy LVM config.

---

### Post by YesWeCan on 2011-08-21
[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

pvcreate
vgextend
lvextend
resize2fs

---

### Post by YesWeCan on 2011-08-21
This may be more helpful: [http://www.howtoforge.com/encrypted-root-lvm](http://www.howtoforge.com/encrypted-root-lvm)

---

### Post by 37fleetwood on 2011-08-22
Ok, since this is a brand new machine with nothing on it that I need to save, I decided to try out Fedora.
a couple of observations,
Pro:
it installed very quickly and with no trouble. the installer asked easy questions about the disks I wanted to include. it did exactly what I wanted without any hassles, and it did it from the live disk!
Con:
Fedora wouldn't update anything, kept giving me can't install this package which I would have to go through and remove from the list of packages to install then it would give me another can't install that. after about hunting down 5 or 6 packages in the list of several hundred files on the initial update I gave up. I quickly realized that it wanted to update packages I would need updated and gave no solution as to how to get them to update. Ubuntu's update is much better. I miss Ubuntu's software center, it's nice to have both it and apt available. Fedora wouldn't let me install any packages, same basic issue as updating.

I'm left with the question, Why hasn't Ubuntu addressed the issue of making this easier? obviously it can be done, Fedora figured it out.
also why is Fedora so much more crude? they're one of the biggest distros, they've been around forever.

in today's world of ever increasing security issues this is an important issue to get right.

I have 2 requests,
1. please Ubuntu, fix the issue of including multiple hard drives to the encrypted lvm upon install.
2 someone please fix the logical volume management package so it works so idiots like me can use it without messing things up! at least someone create a manual...Please!

---

### Post by 37fleetwood on 2011-08-25
first thanks for the replies, I do appreciate them. I'm hoping there is an easy way to use the gui to get this done, I'm not too knowledgeable with the command line.

the most recent update is that I moved back to Fedora 14 and got a more regular Gnome desktop and cured all the update and install problems. still I kinda have become used to Ubuntu and am not sure about moving to Fedora.
thanks again for the help!

---

### Post by 37fleetwood on 2012-04-26
Ok, six months or more with Fedora and the only thing it does well is setting up the LVM.
I really want to move back to Ubuntu but really find the multi-drive LVM to be invaluable.
please help me to figure this out.
here's what I'm thinking,
first, I'm thinking after the install I will need to reboot to the live cd where I will have to install the LVM tools needed. next I'm hoping I can add physical drives to the logical volume group and expand the encrypted volume onto it. 
my questions are, am I on the right track? the LVM tools don't seem to like the idea of me messing with the logical volume the system is installed on while it is running. can I get where I want to be by running the live cd and manipulating the Logical volume with it?
next, with an encrypted system, do I have to encrypt each new physical drive separately before adding them, or will it work to expand the encrypted volume across empty physical volumes after adding them to the Logical volume?
another way I have read about was accomplished by running the live cd and installing the LVM tools. from there you manually create the Logical volume as you need it, and then install the system to it from the live cd.

here is my setup right now in Fedora, if possible, I'd like the new setup to look just like this when done.
[IMG]http://classicbicyclefanatics.com/gallery/albums/userpics/10062/Screenshot-Logical_Volume_Management.jpg[/IMG]

---

