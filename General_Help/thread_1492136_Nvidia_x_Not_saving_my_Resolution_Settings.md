---
title: "Nvidia x Not saving my Resolution Settings?"
date: 2010-05-24
forum: General Help
---

### Post by blaqkmagic on 2010-05-24
Hey all,
First off sorry if this is in the wrong place. First time on  this forum.

I recently installed Ubuntu, 10.4

My problem  is that when i log in, the resolution isnt what i want.
So i change  it via the Nvidia x server settings, and press Save to x config file

Yet  when i log in again, it defaults back to what it was before i changed  it?

Can any one help?
Iv looked all over the internet for the  past 2 days and nothing seems to work.

Thanks again!

---

### Post by Frogs Hair on 2010-05-24
You could try going to  preferences > startup applications and  remove the check for Nvidia X server settings, then in options tab  remove the check for remember running applications . Change your resolution recheck the Nvidia X server settings in startup apps window and check remember running apps. It sounds like it's remembering the setting you don't want.

---

### Post by WinterRain on 2010-05-24
You need to launch nvidia settings with:
```
gksudo nvidia-settings
```
*then* make your changes.

---

### Post by BobvanderPoel on 2010-05-24
To a startup script add:

   nvidia-settings -l

which will get the nvidia-settings program to read it's config file (where the settings are saved) and restored them.

I have added this to my system->prefs->startup applications

and it works just fine. To make sure that it's right, etc. you can also type the command from a terminal, etc.

---

### Post by blaqkmagic on 2010-05-24
Hey all, Thanks for the advice

I done the removing Nvidia x from start up etc , it didnt work

I also tried running Nvidia x from sudo, also didnt work.. ?

Im new to Ubuntu, so im not sure how to make a script? Sorry?

Iv attached my Config file incase iv made a complete newbie mistake in it?

Thanks again for the help guys, really , appreciate it!

---

### Post by kswenson on 2010-12-08
The fix in this thread worked for me:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1242804&page=4](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1242804&page=4)

---

### Post by drewsus on 2010-12-09
In Nvidia X Server Settings (command: nvidia-settings) go to "X Server Display Configuration" change the resolution to what you want, then click "Save to X Configuration File", check/uncheck as desired "Merge with existing file" and choose save. 
Profit.

---

