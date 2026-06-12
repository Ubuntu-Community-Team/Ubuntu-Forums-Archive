---
title: "Flash problem, white screen"
date: 2011-11-22
forum: General Help
---

### Post by saltcushy on 2011-11-22
Sometimes I see bug when watching a movies(lubuntu 11.10) [[IMG]http://img256.imageshack.us/img256/1619/201111181234541280x1024.th.png[/IMG]](http://imageshack.us/photo/my-images/256/201111181234541280x1024.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by ajgreeny on 2011-11-22
How did you install flash?

---

### Post by LinuxFan999 on 2011-11-22
Have you tried other browsers?

---

### Post by collisionystm on 2011-11-22
You need to manually install flash for opera.

It goes in the /usr/lib/opera directory, under plugins i think? I dont know for sure. I am not on Ubuntu at the moment.

its the libflash.so you download from the adobe site. You want the .tar.gz file. It extracts from there

---

### Post by saltcushy on 2011-11-24
Flash installed from a repository under Ubuntu Tweak
@collisionystm, yours a instructions don't work(Before, removed flash from ubuntu tweak) :(
By the way In Lubuntu 11.04 saw same the bug :(

---

### Post by collisionystm on 2011-11-24
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by saltcushy on 2011-11-24
I tried this the guide, but doesn't work or Do I  do something wrong
> Flash problems
Acroread Plugin Problems(but this I cant' find a nppdf.so)

---

### Post by collisionystm on 2011-11-25
okay just tested this. Hopefully this fixes it for you.

Open Firefox
Install Flash-Aid plugin.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Restart Firefox
Click on Flash aid icon in upper right of firefox. Red Circle icon.

Run Wizard. I always choose beta.

This program will place the flash file in
/usr/lib/mozilla/plugins

Opera automatically checks this directory for the flash file.
The flash installer that comes with ubuntu does not place the file into this directory. Cant remember where, but i know its not there. ( havent used it in quite a while ).


Either way, once you do that. Close Opera, re-open it. Your flash should work.

I tried to make this as easy as possible! Good luck

---

### Post by saltcushy on 2011-11-26
still the problem occurs,omg :confused:

---

