---
title: "CD rom wont mount? wtf???"
date: 2010-02-06
forum: General Help
---

### Post by altjx on 2010-02-06
I can't believe I'm sitting here troubleshooting a got damn CD rom issue. Excuse my anger but this is frustrating as hell....

I unmounted my CD rom earlier and now it's giving me trouble. It won't show up in File Browser anymore. When I reinser the CD, it comes for about 1 second and goes away... What the hell???

---

### Post by mushwars on 2010-02-06
you could try mounting the cdrom drive manually.

```
sudo mount /dev/sr0 /mnt/cdrom
cd /mnt/cdrom
ls -a
```

Post any errors. if you do get errors also post 

```
dmesg | tail
```

---

### Post by altjx on 2010-02-06
> **mushwars said:**
> you could try mounting the cdrom drive manually.

```
sudo mount /dev/sr0 /mnt/cdrom
cd /mnt/cdrom
ls -a
```Post any errors. if you do get errors also post 

```
dmesg | tail
```

Soon as I type sudo mount /dev/sr0 /mnt/cdrom, i get this

```
alton@alton-laptop:~$ sudo mount /dev/sr0 /mnt/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
alton@alton-laptop:~$ 

```

The minute I type cd /mnt/cdrom I get
```
alton@alton-laptop:~$ cd /mnt/cdrom
bash: cd: /mnt/cdrom: Permission denied
alton@alton-laptop:~$ 

```

When I type dmesg | tail, I get
```
alton@alton-laptop:~$ dmesg | tail
[ 1104.344655] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1104.429208] ISO 9660 Extensions: RRIP_1991A
[ 1115.176914] UDF-fs: No VRS found
[ 1115.176918] UDF-fs: No partition found (1)
[ 1115.241399] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1115.292564] ISO 9660 Extensions: RRIP_1991A
[ 1144.846352] UDF-fs: No VRS found
[ 1144.846360] UDF-fs: No partition found (1)
[ 1145.030267] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1145.030300] ISO 9660 Extensions: RRIP_1991A

```

---

### Post by mushwars on 2010-02-06
doh >_< my bad I forgot you have to sudo cd /mnt/cdrom 

better yet.
```
sudo chown -R <your username> /mnt/cdrom
cd /mnt/cdrom
```
Replace <your username> with your name.

CDROM is ALWAYS mounted readonly, thats what cd's are. ;) so dont worry that is not an error.

if that code doenst work you can sudo cd /mnt/cdrom

it is a good sign though that your deice was able to mount, which means its an ubuntu probem and NOT a cdrom problem. 

YOu are luck then ;)

---

### Post by altjx on 2010-02-06
Gonna try

---

### Post by altjx on 2010-02-06
well apparently i took ownership but i still cant get access in it

alton@alton-laptop:~$ cd /mnt/cdrom
bash: cd: /mnt/cdrom: Permission denied
alton@alton-laptop:~$ sudo cd /mnt/cdrom
sudo: cd: command not found
alton@alton-laptop:~$

I cant even eject the damn thing without manually doing sudo eject /media/cdrom... I hope my touchpad isn't next -.-
According to cdrom folder's properties. The owner is still -1 - user #-1, same as before.

---

### Post by mushwars on 2010-02-06
thats right you cant sudo cd, sorry that was my bad again.

There is no point in logging in as root and using your cdrom from bash, you will need to fix gnome automounter, that is where the problem is.

**HERE IS HOW TO GET YOUR CD OUT**
```
sudo umount /mnt/cdrom
```

---

### Post by altjx on 2010-02-06
> **mushwars said:**
> thats right you cant sudo cd, sorry that was my bad again.

There is no point in logging in as root and using your cdrom from bash, you will need to fix gnome automounter, that is where the problem is.

**HERE IS HOW TO GET YOUR CD OUT**
```
sudo umount /mnt/cdrom
```

I've done that. Doesnt do anything different. Still can't eject CD without sudo eject /media/cdrom... And what do you mean gnome automounter? lol I know nothing about that. I'm sorta new =\

---

### Post by mushwars on 2010-02-06
I am sooooo sorry I cant be of much help there I dont like my devices to automatically mount. I like doing it manually. For some reason I never have that problem in gentoo with mounting, it seems that ubuntu REALLY doenst want you to mount your own devices. I can mount a cdrom and then open it in nautilus just fine.

I hope your problem gets worked out. :)

---

### Post by altjx on 2010-02-06
Thanks, lol.
I'm just about 5 minutes from going back to windows anyway. It seems like linux has more issues than vista w/o SP1... 2hr troubleshooting on a CD rom

---

### Post by mushwars on 2010-02-06
suit yourself, It was good that you atleast gave it a try, You can always dual boot. I would do that install windows (dont make it fill the whole drive ) then install ubuntu again, so that way you can go back and forth.

Linux seriously is a much better system. But Windows does have its perks.

Good luck

---

### Post by altjx on 2010-02-06
Well, I'm dual booting BackTrack 4 right now. just waiting on a wireless usb adapter to come in, because of course, it doesnt detect my integrated wlan card. no surprise there, lol. like i said though, im pretty sure tomorrow i'll be trying to find out why my touchpad isnt working and having a new thread on that too, xD

---

### Post by altjx on 2010-02-06
Also, for some reason any other Cd will work. It's nothing wrong with the Cd though because Virtual Box (windows XP) detects it with absolutely no problem. Why is it just this specific CD isnt working?

Although the eject still doesnt work.

---

### Post by mushwars on 2010-02-06
I just read this
[http://www.linuxquestions.org/questions/linux-desktop-74/gnome-automount-not-working-556463/](http://www.linuxquestions.org/questions/linux-desktop-74/gnome-automount-not-working-556463/)

It looks like either you need to reinstall gnome-volume-manager or try to get it running.

try alt + f2 gnome-volume-manager 
then try your cd. if still nothing

```
sudo apt-get purge gnome-volume-manager
sudo apt-get install gnome-volume-manager
```

good luck.

---

### Post by altjx on 2010-02-06
> **mushwars said:**
> I just read this
[http://www.linuxquestions.org/questions/linux-desktop-74/gnome-automount-not-working-556463/](http://www.linuxquestions.org/questions/linux-desktop-74/gnome-automount-not-working-556463/)

It looks like either you need to reinstall gnome-volume-manager or try to get it running.

try alt + f2 gnome-volume-manager 
then try your cd. if still nothing

```
sudo apt-get purge gnome-volume-manager
sudo apt-get install gnome-volume-manager
```good luck.

Lol man, I formatted last night and it's doing the same thing. Linux definitely did something to the CD I had. Thanks though. I still have trouble getting the CD ejected though

---

