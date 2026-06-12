---
title: "boot into SHELL"
date: 2009-11-22
forum: General Help
---

### Post by KONEY on 2009-11-22
Hi all!

I know this sounds stupid but I cannot reach the shell to my installation of Ubuntu!

After an upgrade to 9.10 I removed some packets that had some problems and now the system dont boot anymore. I get the white ubuntu logo, something quicly flash on screen and it remains blanked. CTR-ALT-F1 doesn't do anything and the recovery mode is all messed and doesn't work as well.

So I'm asking what other way have to access the shell, including bootdisks if necessary, to be able to re-install the missing packets that prevento the graphix environment to load?

Thanx in advance!

---

### Post by KONEY on 2009-11-22
Small update: if pressing CTRL-ALT-F1 during the white logo display this becomes garbled....

---

### Post by fluffman86 on 2009-11-22
If you can't even boot into recovery mode, then there's not really anything we can do to help you.  A reinstall will be quicker and easier.

---

### Post by KONEY on 2009-11-22
ok. I should re-install ubuntu 9.10 now?

Is it possible to re-install without formatting and save all my data?

Thanx

---

### Post by fluffman86 on 2009-11-22
If you manually set your home directory as a separate partition during install, then you can do the same thing during your re-install and you won't have to format /home.

If you did a normal guided installation, then everything is on a single partition and you will have to manually back up your /home/user directory before reinstalling.

If you didn't place /home on a separate partition last time, now would be a good time to do that, for this very reason. :)

---

### Post by ibuclaw on 2009-11-22
> **KONEY said:**
> ok. I should re-install ubuntu 9.10 now?

Is it possible to re-install without formatting and save all my data?

Thanx

In the LiveCD, mount:
[LIST=1]
[*]An external drive
[*]Your Ubuntu partition
[/LIST]
Then copy over all your files to the external drive.


One question I am inclined to ask though...

Can you take a photograph of the "garbled" output you get from the Ctrl+Alt+F1 screen, and possible the Recovery Menu too? :)

That way, having a look at it may help us decide just *what* has happened to your system and if there is any way to prevent it happening again.

Regards
Iain

---

### Post by KONEY on 2009-11-22
> **tinivole said:**
> 
One question I am inclined to ask though...
Can you take a photograph of the "garbled" output you get from the Ctrl+Alt+F1 screen, and possible the Recovery Menu too? :)
That way, having a look at it may help us decide just *what* has happened to your system

Sure! I made two short videos, zipped here: [http://dl.dropbox.com/u/3066410/UBUNTU_problems.zip](http://dl.dropbox.com/u/3066410/UBUNTU_problems.zip) !

I'm not hiding a small hope that you can find a way for me to reach the shell prompt :)

Thanx againg

---

### Post by dcstar on 2009-11-22
> **tinivole said:**
> 
.........
That way, having a look at it may help us decide just *what* has happened to your system and if there is any way to prevent it happening again.


Apart from removing obviously critical packages?

If people are going to do this sort of thing, then these are the consequences.

---

### Post by KONEY on 2009-11-22
> **dcstar said:**
> Apart from removing obviously critical packages?

If people are going to do this sort of thing, then these are the consequences.

I HAD to! the graphix driver ran unbeliveably slow so I had to put the nvidia ones, but after since the audio also wasn't working anymore I tried to re-install alsa that didn't install because xorg nouveau prevented it to so I removed that ant this is what happened. 

I didn't know that upgrading to 9.10 would have been such a mess! :(

---

### Post by whitethorn on 2009-11-22
Not quite sure if this is gonna help or screw up your installation even more.  But, boot using the live CD, copy your data to an external drive or wherever.  Then chroot to your ubuntu installation and try to update and upgrade or reinstall gnome-desktop-environment.  Then try rebooting, might fix your problem.  Just be sure to backup your data first.

---

### Post by KONEY on 2009-11-22
that COULD work!

---

### Post by ibuclaw on 2009-11-22
> **KONEY said:**
> that COULD work!

Indeed it could. From looking at the videos, is your Ubuntu Installation on sdb5 ?

If so, follow these instructions directly.

[LIST=1]
[*]Load Ubuntu LiveCD (select "Try Before Installing Ubuntu")
[*]Open up a Terminal (Applications -> Accessories -> Terminal)
[*]Run the following in order:
```

sudo mount /dev/sdb5 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt

```
The shell prompt should now change, and you are now root.
[*]Setup all temp stuff:
```

mount -t sysfs sysfs /sys
mount -t proc proc /proc
mount -t devpts devpts /dev/pts
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

```
[*]Now run an update/upgrade.
```

apt-get update
apt-get install -f
apt-get upgrade

```
[*]Probably for safe measure, install the ubuntu metapackages too, as that will install all packages that came with your installed system. (When you first installed it).
```

sudo apt-get install ubuntu-desktop ubuntu-standard ubuntu-minimal

```
[*]Undo all setup temp changes.
```

unlink /sbin/initctl
dpkg-divert --rename --remove /sbin/initctl
umount /dev/pts
umount /proc
umount /sys
exit

```
And the shell will change back to the LiveCD prompt.
[*]Unmount the filesystem (if possible, not essential).
```

sudo umount /mnt/dev
sudo umount /mnt

```
[*]Reboot your system.
[/LIST]

Quite a long list ... but should bring you back to speed if it's package configuration.

Regards
Iain

---

### Post by KONEY on 2009-11-23
I will try all of this! The only thing I'm not sure is, shall I use a 9.10 live cd since the system is upgraded to 9.10 or for this job a 9.04 is ok?


Thanx! you gave me one hope :)

---

### Post by KONEY on 2009-11-23
IT WORKED! I managed to go get a shell prompt at boot! YEEES! Issuing a startx now makes it behave as usual and I cannot install ubuntu-desktop and other packets because they say there are problems with the xorg-nouveau packets, but from here it shouldn't be too difficult to get everything back to work!

THANX!

---

