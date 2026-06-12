---
title: "no numlock on start?"
date: 2011-11-28
forum: General Help
---

### Post by rczar on 2011-11-28
lubuntu 11.10, desktop, plain keyboard


I need numlock on boot.  I've tried editing a file in /home/, ".lubuntu"* 


edited a line:
removed the "#"
changed "numlock=0" to "numlock=1"

still no numlock on boot...


*will come back to edit, don't remember actual file name (I was actually looking for openbox's config file so i could add "&&numlock 1" or something like that [been a while], but I found some config file that seemed ubuntu specific)

thanks for your help, no help found on google yet



-----
so installed *numlockx* and it seems to work.  all the google results showed text editing gdm setting, so i didnt try until now cause i have no gdm.  no editing of lightdm settings was necessary.

---

### Post by drmrgd on 2011-11-29
I don't use Lubuntu, so this is a bit of a guess.  Usually there is a setting in the System Settings > Keyboard (or something like that) that will allow you to turn on NumLock at startup.  Can you find something like that on your system?

---

### Post by glen-shennan on 2011-12-09
Same problem here. No, the option isn't in the keyboard preferences.

---

### Post by WorMzy on 2011-12-09
I don't use lubuntu, but check the settings for whatever session/login manager it uses. I use Openbox as a standalone window manager, with Slim as a login manager. In slim's config file (/etc/slim.conf) there's an option to have numlock enabled or disabled at boot time.

---

### Post by Rodney9 on 2011-12-09
Install numlockx with Synaptic

> Utilities to enable the keyboard's Numeric Lock during X11
session initialization or using command line utility.

The package automatically installs session script to enable numlock
on session start.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by glen-shennan on 2011-12-09
Edit [FONT=Courier New][SIZE=2]/etc/xdg/lubuntu/lxdm/lxdm.conf[/SIZE][/FONT]

Find the line [FONT=Courier New][SIZE=2]# numlock = 0[/SIZE][/FONT] and change it to [FONT=Courier New][SIZE=2]numlock = 1[/SIZE][/FONT]

Adapted from [http://us.generation-nt.com/answer/lxde-numlock-key-help-203128882.html](http://us.generation-nt.com/answer/lxde-numlock-key-help-203128882.html)

I'm running lubuntu 11.10. I assume things like this will change version to version while lubuntu is young.

---

### Post by glen-shennan on 2011-12-09
[> Lubuntu Rocks, so Fast, so Sleek]("http://ubuntuforums.org/showthread.php?t=1844755")

Word

---

### Post by jorok_tupur on 2011-12-26
> **glen-shennan said:**
> Edit [FONT=Courier New][SIZE=2]/etc/xdg/lubuntu/lxdm/lxdm.conf[/SIZE][/FONT]

Find the line [FONT=Courier New][SIZE=2]# numlock=0[/SIZE][/FONT] and change it to [FONT=Courier New][SIZE=2]numlock=1[/SIZE][/FONT]

Adapted from [http://us.generation-nt.com/answer/lxde-numlock-key-help-203128882.html](http://us.generation-nt.com/answer/lxde-numlock-key-help-203128882.html)

This works for me. Thanks.

---

### Post by momist on 2012-05-16
Thanks  - I needed that!

Lubuntu is So fast!   ):P

---

### Post by pordzio on 2012-05-29
> **momist said:**
> 
Lubuntu is So fast!   ):P

My words exactly - the only thing I chose Lubuntu for.

---

### Post by brujoquizz on 2012-06-02
Just what I needed. Thank you!

edited:
On precise (12.04) doesn't work, the best option is installing numlockx from synaptic.

---

### Post by mikaere66 on 2013-03-20
Awesome thank you ... Numlockx works for me!

---

### Post by Squirrelking on 2013-07-19
File edit works in Raring Ringtail (13.04) but you need to open in terminal under root:

```
sudo leafpad /etc/xdg/lubuntu/lxdm/lxdm.conf
```

As before find the line 

```
# numlock-0
```

and edit to

```
numlock-1
```

then hit save and the jobs a good 'un.

---

