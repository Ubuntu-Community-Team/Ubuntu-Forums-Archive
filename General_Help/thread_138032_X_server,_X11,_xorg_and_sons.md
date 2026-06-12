---
title: "X server, X11, xorg and sons"
date: 2006-03-01
forum: General Help
---

### Post by manchette on 2006-03-01
Hi all,
when i boot on the Breezy OS i can't log in for i haven't got any keyboard nor mouse available.
wireless keyboard & mouse : Genius Twintouch luxemate
wired original keyboard & mouse : Fujitsu Siemens
(usb legacy is enabled i n Bios)

i'm wondering how i can  have access to the X server when my keyboard and mouse do not react   (? )
i can't act from ubuntu but i'm using triple boot xp/suse/ubuntu
...So, can i act from Suse ?
it seems like i need to edit the /etc/X11/xorg.cong file
do you agree and how shall i edit it?
i was told to hold down ctrl+alt+F1 and run 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf 
can i change ubuntu from within Suse? or which way?

---

### Post by andrewsawyer on 2006-03-01
I'm not sure on the settings you would need in your xorg.conf, however there would be no problem in making Ubuntu config changes from within Suse.  If you were to run a program to reconfigure the xorg you may have a problem, but just using nano or gedit to make direct config changes can be done from any distro you like.

---

### Post by manchette on 2006-03-01
so if i run what i said before in suse, will this change the ubuntu file?

---

### Post by andrewsawyer on 2006-03-01
You will have to make sure you do it to the Ubuntu one and not the Suse one.  So, if you mount the Ubuntu partition as /mnt inside Suse, then you will be typing: ```
 sudo gedit /mnt/etc/X11/xorg.conf
```
What you wrote above assumes that you are working from within Ubuntu.

---

### Post by manchette on 2006-03-01
i've already got a mounted /ubuntu partition in suse and a /suse one in ubuntu

why do i have to mount again?i guess i don't

then how can i apply the code from my 1st post? 
adding the sudo gedit line before the 1st post code?
(what's sudo gedit ?)

---

### Post by andrewsawyer on 2006-03-01
Ok,

If you have mounted the Ubuntu partition inside a directory called /ubuntu, then the code would be:

```
sudo gedit /ubuntu/etc/X11/xorg.conf
```

You don't need to mount it again.  I was going on the basis that it wasn't mounted.

Sudo is the command for Super User or root privileges in Ubuntu.  Not 100% sure whether Suse uses sudo or not, but basically you have to be a super user to make changes to files outside your /home directory.  So try with sudo, but if that doesn't work then try 'su'.

Gedit is a Gnome, GUI version of nano.  You can use either - it's upto you.

I hope this helps,

Andy

---

