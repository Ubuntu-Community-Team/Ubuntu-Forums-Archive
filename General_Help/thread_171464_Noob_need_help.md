---
title: "Noob need help"
date: 2006-05-06
forum: General Help
---

### Post by macoxp on 2006-05-06
I tryed searching the fourms for abour an hour. So if this is already answered I'm super sorry. Anyways I'm trying to change a setting it's asking for the root password. However I was never given a chance to set the root password during install. Just my personal account password. any help here would be great. Like how to set the root password to what i want, not the default. and what is the default password anyways?

---

### Post by @jens on 2006-05-06
There is no "root" in ubuntu. It goes similar like in MacOS:
$ sudo [like somewhat]
password: Your *user* password
Keep on...
hth a bit
@jens

---

### Post by aysiu on 2006-05-06
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by macoxp on 2006-05-06
Ok well here is what I'm trying to do.

I installed Kubuntu.
When it comes to where the log-in screen should be it's all sorts of pink lines on the screen.

I searched the forums for the fix. and it seems i need to change the driver from nv to vesa. To do so I need to use. sudo spkg-reconfigure xserver-xorg. 

When i enter that command i get Password:

I enter my password and it says log-in incorrect. So i asumed it wanted a different password aka root,  but sense there is no root i'm not sure whats going on. I know I've entered the right password....

---

### Post by aysiu on 2006-05-06
[QUOTE=macoxp]
I enter my password and it says log-in incorrect. So i asumed it wanted a different password aka root,  but sense there is no root i'm not sure whats going on. I know I've entered the right password....[/QUOTE] No, it should be your user password. This assumes, of course, that your user belongs to the *admin* group (and thus has *sudo* privileges).

The first user you create during installation should be in the *admin* group. Any users you've added after that would not be in the *admin* group unless you go out of your way to add them to that group.

... unless you did an *expert* install. Then, *sudo* won't function properly.

---

### Post by Omnios on 2006-05-06
[QUOTE=macoxp]Ok well here is what I'm trying to do.

I installed Kubuntu.
When it comes to where the log-in screen should be it's all sorts of pink lines on the screen.

I searched the forums for the fix. and it seems i need to change the driver from nv to vesa. To do so I need to use. sudo spkg-reconfigure xserver-xorg. 

When i enter that command i get Password:

I enter my password and it says log-in incorrect. So i asumed it wanted a different password aka root,  but sense there is no root i'm not sure whats going on. I know I've entered the right password....[/QUOTE]

 Pink lines is a Xorg config problem I think as I had that problem before with nvidia and a KTX monitor. Xorg tryes to run the monitor as hard as it can by default till you get into your graphical Interface. I solved this problem by looking at the refresh rate in windows and lowering the vert refresh rate to the the max refresh rate that I wanted in Gnome which I think was 75. As long as you do not increase the rate you should be ok.

 This can be either moded by " sudo gedit /etc/X11/xorg.conf " and mondify the monitor part in the text file or using " sudo dpkg-reconfigure xserver-xorg " which is like a turtle graphics config thingy for xorg and use monitor advanced to set the refresh rates.

 A better option would be to use versa and get better drivers for your graphics card (3D) as that useually clears up most of the problems.

---

### Post by macoxp on 2006-05-06
YAY! i figured it out. I had to log into my account then use the sudo command to give "admin" rights to the account while running that command. Typed my password when promped and it worked :D now I switched the driver to vesa. Now all i have to do is figure out how to install the drivers off the nvidia website.

---

