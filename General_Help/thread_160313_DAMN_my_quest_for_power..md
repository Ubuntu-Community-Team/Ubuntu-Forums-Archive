---
title: "DAMN my quest for power."
date: 2006-04-14
forum: General Help
---

### Post by WaveMyBlackFlag on 2006-04-14
](*,)  Okay well, it took me  a while but I got my install just how I want it.  

of course, i go to   [http://doc.gwos.org/index.php/TweakExt3](http://doc.gwos.org/index.php/TweakExt3)   and decide, hey more speed, SURE...it wasnt until the very bottom of the page that I saw "problems booting unless...", which kinda stuck with me.  I went on with it anyway, now...yay no ubuntu.  sweet, I like it when this happens.  :-? .

K so when I boot, about half the start up modules fail and it mounts the file system as read only.  i've been able to get to the files I need to edit, yet i cannot open them because...read only...right.

So long story short, I just want to reverse this procedure and get back on track.  

Any help would be greatly appreciated, I dont wanna start all over.  IT WAS SUDOPERFECT I tell you.

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=WaveMyBlackFlag]](*,)  Okay well, it took me  a while but I got my install just how I want it.  

of course, i go to   [http://doc.gwos.org/index.php/TweakExt3](http://doc.gwos.org/index.php/TweakExt3)   and decide, hey more speed, SURE...it wasnt until the very bottom of the page that I saw "problems booting unless...", which kinda stuck with me.  I went on with it anyway, now...yay no ubuntu.  sweet, I like it when this happens.  :-? .

K so when I boot, about half the start up modules fail and it mounts the file system as read only.  i've been able to get to the files I need to edit, yet i cannot open them because...read only...right.

So long story short, I just want to reverse this procedure and get back on track.  

Any help would be greatly appreciated, I dont wanna start all over.  IT WAS SUDOPERFECT I tell you.[/QUOTE]

Quoted from the first page of the thread:

> Another way to rescue is to reboot into recovery mode, when it gets you to the CLI type:

mount -o remount,rw /dev/hdXX /

hdXX being your hard drive partition. This will allow you to edit the fstab and menu.lst to undo the changes.

---

### Post by WaveMyBlackFlag on 2006-04-15
trying...

---

### Post by WaveMyBlackFlag on 2006-04-15
alright, i get this:

[4295358.920000] Ext3-fs:cannot change data mode on remount
mount: / not mounted already, or bad option.

I missed sumthing i think.

---

### Post by WaveMyBlackFlag on 2006-04-15
yeah, left out the root call at the end.  now to edit.  yes, right see I didnt think to ask how to edit from the command line.  I was used to sudo gedit, realizing as I type it, this won't work I have no X.  

I've searched, probably for the wrong things, but i cannot find how to edit.  I cannot startx at all, so everything has to be done from the command line, which in my short 3 month linux run (2 of those being mandriva), this is a first.  Im not totally in the dark, but a little basic's help out is what I need

---

### Post by Face1 on 2006-04-15
I'm about as new to this as you are, so I can't help you with much other than that you can edit text files at the command line with the relatively easy to use pico or nano (those are the program names, just type in 'sudo pico textfilename' (of course, you only need the sudo if you need permissions for that file)).  Or you can use vi, which is kinda a pain if you don't know the commands.  Just use pico or nano ;) .

---

### Post by WaveMyBlackFlag on 2006-04-15
My comrades, I thank you.

I learned how to edit from command line, remount a drive, and I was able to fix the problem.

Heres what you saved, its not much, but after about 1 month of tinkering with more to come, im pretty damn proud of it.

---

### Post by PriceChild on 2006-04-15
You can use
```
sudo nano /etc/fstab
```
&
```
sudo nano /boot/grub/menu.lst
```
To edit from a command line.

---

