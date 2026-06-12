---
title: "cpu usage 100 all the time"
date: 2010-08-30
forum: General Help
---

### Post by dagame on 2010-08-30
hi everyone, this is my first post here. I decided to try out linux

for the first time. I really like it and all, the only problem i'm

having so far is that when i go to the terminal, type the top

command says: kacpi_notify is using 95-100% of my cpu usage

i have done all the system updates. So any ideas on how to fix this

plz let me know asap. Thanks in advance. 

Dagame

---

### Post by MooPi on 2010-08-30
Hello first poster. If your cpu is running 100% thats not good so go to your system resource monitor under menu       /System/Administration/System Monitor
Look and see what processes are using the most of the cpu cycles.
Take a screen shot and post it back here if you can

---

### Post by JC Cheloven on 2010-08-30
Hi, it seems to be a certain bug in kacpi since 2005, that comes over now and then with some kernel updates in some hardware. It can produce such high CPU usages. From a quick googling: 

[http://forums.gentoo.org/viewtopic-p-5992975.html?sid=dbbc49d95e6abb5d3af559282f6a11ae](http://forums.gentoo.org/viewtopic-p-5992975.html?sid=dbbc49d95e6abb5d3af559282f6a11ae)
[http://lists.debian.org/debian-user/2005/02/msg01885.html](http://lists.debian.org/debian-user/2005/02/msg01885.html)
[http://www.frihost.com/forums/vt-94452.html](http://www.frihost.com/forums/vt-94452.html)
[https://lists.linux-foundation.org/pipermail/bugme-new/2007-March/016040.html](https://lists.linux-foundation.org/pipermail/bugme-new/2007-March/016040.html)

People says that updating/downgrading the kerner should solve it. If not, a bios update of your computer. Or even disabling the service is adviced. I think google is your friend here.

---

### Post by howefield on 2010-08-30
> **dagame said:**
> So any ideas on how to fix this

What version of Ubuntu are you using ?

You could try starting here...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280088)

---

### Post by howefield on 2010-08-30
> **MooPi said:**
> Hello first poster. If your cpu is running 100% thats not good so go to your system resource monitor under menu       /System/Administration/System Monitor
Look and see what processes are using the most of the cpu cycles.
Take a screen shot and post it back here if you can

Is the OP really not that clear ?

:lolflag:

---

### Post by dagame on 2010-08-30
im using the new ubuntu 10.04. thanks for the quick reply guys!

---

### Post by dagame on 2010-08-30
howelfield, so exactly what patch do i need to download from that site? sorry for my ignorance, i just started out with linux. :)

---

### Post by JC Cheloven on 2010-08-30
> **dagame said:**
> im using the new ubuntu 10.04. thanks for the quick reply guys!
You're welcome. I didn't notice that you were new here. A bit of explanation is in order :)

To disable the service, first make a backup of the related file:

```
sudo cp /etc/default/grub /etc/default/grub-old
```

edit as superuser the file:

```
sudo nano /etc/default/grub
```

Identify and change the related line, to read:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off apm=on"
```

Save (ctrl-o) and exit (ctrl-x). Then reboot, and see how well it works for you (restore the file in case it behaves bad). If the pc doesn't boot, you can always boot from live cd, and restore the original grub file.

Cheers

---

### Post by dagame on 2010-08-30
jc, so i did all that, i rebooted and still the same. Is there anything else you suggest i do?

i dunno if it could be the netbook i'm using, i have an msi l2100. Maybe ubuntu is just too heavy to run?

---

### Post by JC Cheloven on 2010-08-30
> **dagame said:**
> jc, so i did all that, i rebooted and still the same. Is there anything else you suggest i do?
Strange. Do you still see in top the same process? That should have get rid of it. Anyway... if it didn't work, please revert the change (renaming the file grub-old back to grub).
And, well, I admit this is a shot in the dark, but you can try pressing 'e' when the list of boots is presented in grub. Search for the line beginning by "linux /boot/vmlinuz(...)" which will probably end with "(...) quiet splash". Please replace "quiet splash" by "noapic nolapic". Then ctrl-x to boot, and see if this helped. The above didn't made any permanent change in your system. If it happens to work, you can make it permanent afterwards in the /etc/default/grub file).

A bit more info could also help. Please post the output of ```
ps -al
``` when the cpu is that busy.

> i dunno if it could be the netbook i'm using, i have an msi l2100. Maybe ubuntu is just too heavy to run?
I didn't have any experience with that computer, but it's a quite recent one. And Ubuntu is quite lightweight compared with typical proprietary OSes. I dare to say that the processing power of your pc shouldn't be a problem at all.

---

### Post by dagame on 2010-08-30
> if it didn't work, please revert the change (renaming the file grub-old back to grub).

im soryy but how exactly do i do that? i'm a newbie here @ using the terminal still. :confused:

ok i typed ps and this is what came up:

```
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 R  1000  2940  2923  0  80   0 -   625 -      pts/0    00:00:00 ps

```

> 
I didn't have any experience with that computer, but it's a quite recent one. And Ubuntu is quite lightweight compared with typical proprietary OSes. I dare to say that the processing power of your pc shouldn't be a problem at all.


ok cool, now i know my netbook is not the issue here lol.

---

### Post by dagame on 2010-08-30
ok seems like is fixed now all i did was, i ran update-grub rebooted & is not showing there any more, my netbook is running a lot more quiet than before,thanks JC & the other ones for the help, you guys are awsome! :)

btw how how do i solve the thread?

---

### Post by dagame on 2010-08-30
ok i figure it out lol

thanks again guys!

---

### Post by JC Cheloven on 2010-08-31
He he, you figured out everything by ourself... an excellent start in gnu-linux, that of yours ;)

I admit I don't understand what the 'beep' your problem had to do with grub. But I'm glad you solved it anyway. Out of curiosity, do you notice any remarkable difference between your present /etc/default/grub and the former /etc/default/grub-old?

> **dagame said:**
> im soryy but how exactly do i do that? i'm a newbie here @ using the terminal still. :confused:
Well, it was with the cp (from 'copy') command you used formerly. You could also use mv (from 'move'). I don't issue the exact command because now (after your update-grub) it makes no sense. It could even revert things to a wrong state (well, it shouldn't, but update-grub shouldn't have fix anything either :confused: ).


> ok i typed ps and this is what came up:
```
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 R  1000  2940  2923  0  80   0 -   625 -      pts/0    00:00:00 ps

```
Another surprise to me. Only the ps process itself is reported. It should have reported that high cpu consuming process you noticed. Well it seems that this will remain as one of the many problems solved automagically. 

PS.- sorry for a not snappy answer. There is an ocean between us ;)

JC

---

### Post by dagame on 2010-08-31
> He he, you figured out everything by ourself... an excellent start in gnu-linux, that of yours ;)

I admit I don't understand what the 'beep' your problem had to do with grub. But I'm glad you solved it anyway

well this is what i did i changed the GRUB_CMDLINE_LINUX_DEFAULT="acpi=off apm=on" like you told me to, rebooted & nothing happened. Supposedly, it should have worked right? well it didn't so i went back to the terminal typed sudo nano /etc/default/grub i noticed it said 
```
If you change this file, run 'update-grub' afterwards to update
```
that's what i did, and boom the kacpi_notify disappeared & my cpu was running normaly, unluckily after i got it solved another problem appeared but this was with my sound, i don't wanna spamm this thread with a different topic so here it is:
[http://ubuntuforums.org/showthread.php?p=9789151#post9789151]("http://ubuntuforums.org/showthread.php?p=9789151#post9789151")

---

### Post by JC Cheloven on 2010-09-01
> **dagame said:**
> well this is what i did i changed the GRUB_CMDLINE_LINUX_DEFAULT="acpi=off apm=on" like you told me to, rebooted & nothing happened. Supposedly, it should have worked right? well it didn't so i went back to the terminal typed sudo nano /etc/default/grub i noticed it said 
```
If you change this file, run 'update-grub' afterwards to update
```
that's what i did, and boom the kacpi_notify disappeared & my cpu was running normaly
Oh! I'm sorry, my fault. Indeed you have to run update-grub after any change in the file, and I forgot to tell you! Well, I understand now, It worked as expected. I'll sleep better tonight ;)

> unluckily after i got it solved another problem appeared but this was with my sound, i don't wanna spamm this thread with a different topic so here it is: [http://ubuntuforums.org/showthread.php?p=9789151#post9789151]("http://ubuntuforums.org/showthread.php?p=9789151#post9789151")
Ok, let's have a look to that one :)

---

