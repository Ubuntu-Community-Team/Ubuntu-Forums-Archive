---
title: "cant log in"
date: 2010-06-11
forum: General Help
---

### Post by wigglestix on 2010-06-11
I can not log in to my computer. When i try to log in i dont get any authentication errors, it just starts to boot up and then goes back to the login screen. Prior to this i was reinstalling my murrine gtk engine because when i did a system update it started to misbehave.I have no idea why i am not able to log in. Any help is appreciated i must get my laptop up and running as soon as possible.

If not is there a wey to recover my files.

---

### Post by Peter09 on 2010-06-11
OK,
during boot you should hold down the shift key. This will get you to the grub menu.
Select the recovery mode (normall one down) and allow it to boot to the menu. Select the boot to command line option.
 
When you get to the command line do the following
 
```
 
passwd <your user name>

```
 
and follow on from there.
 
Then reboot

---

### Post by Peter09 on 2010-06-11
Follow up:
 
If this does not work try,
 
do the same again, but at the command prompt do
 
```
startx
```
 
and tell us what happens.

---

### Post by wigglestix on 2010-06-11
> **Peter09 said:**
> Follow up:
 
If this does not work try,
 
do the same again, but at the command prompt do
 
```
startx
```and tell us what happens.


I have it booed in safe mode right now and have allready started x. Unfourtnatly it boots in xfce not gnome which is really no big deal, but now i need to figure out how to fix what is wrong to be able to boot normally?.

---

### Post by Peter09 on 2010-06-11
I do not know XCFE much but if its anything like gnome it will have a configuration file which holds all of your settings for the desktop. At a guess that file is corrupt or misconfigured. Normally, if you remove that file in gnome, when you login the default is created again and all is ok, with just a default desktop config
 
Can you do that with XFCE.
 
Note the reason you can boot with startx is that you are using the default (root) config.

---

### Post by wigglestix on 2010-06-11
> **Peter09 said:**
> I do not know XCFE much but if its anything like gnome it will have a configuration file which holds all of your settings for the desktop. At a guess that file is corrupt or misconfigured. Normally, if you remove that file in gnome, when you login the default is created again and all is ok, with just a default desktop config
 
Can you do that with XFCE.
 
Note the reason you can boot with startx is that you are using the default (root) config.

I am not farmilliar with xfce either, i use gnome but for some odd reason it booted xfce instead. I did have xfce installed but i was not currently using it. I am thinking there is something wrong with gnome but i have no idea how to fix those types of things.

---

### Post by Peter09 on 2010-06-11
Try booting normally, when you get to the login screen there is a selctor at the bottom which you can use to select the desktop to boot into. Check that that is set to gnome.

---

### Post by wigglestix on 2010-06-11
> **Peter09 said:**
> Try booting normally, when you get to the login screen there is a selctor at the bottom which you can use to select the desktop to boot into. Check that that is set to gnome.


This is strange. There appears to be no sessions not even xfce or gnome or the other few i have tried over time.

---

### Post by Peter09 on 2010-06-11
You may need to select your user - have the password field open - before the session information is shown?

---

### Post by wigglestix on 2010-06-11
> **Peter09 said:**
> You may need to select your user - have the password field open - before the session information is shown?


Yes i am aware of this when i select myself as the user i get no sesssion options.

---

### Post by donaloflynn on 2010-06-11
I have the same problem and I booted to recovery mode and entered startx  on the command prompt. My screen just went black, other than the mouse  arrow.

I don't know what XFCE is, I just want to be able to log in. I restarted  the computer after removing Evolution Mail via the synaptic  applications menu and ever since my password is accepted at log in but  then the log in page just comes up again in an endless loop.

Thanks

---

