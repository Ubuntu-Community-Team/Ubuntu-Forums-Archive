---
title: "What is the splash that covers the verbose bootup in Breezy"
date: 2006-02-19
forum: General Help
---

### Post by Vetto on 2006-02-19
How do I change it (there are many different versions of bootslpashes on KDE-Look.org, some for lilo and other splash managers...)

I would think that there should be a "HOWTO" or tips section on this somewhere, I just cant find it. :(

---

### Post by nrwilk on 2006-02-19
I just did this earlier today.  It's easy to get verbose mode.

backup menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Open up menu.lst:
```
sudo kwrite /boot/grub/menu.lst
```

Find the entry near the bottom for the kernel version which you like most to use.  It should look something like this:
```
kernel              /boot/vmlinuz-2.6.12 root=/dev/hda2 ro quiet splash
```

Remove the word "splash" from the line, or comment it out by putting a pound sign in front of it like this:
```
kernel              /boot/vmlinuz-2.6.12 root=/dev/hda2 ro quiet #splash
```

Save the file and restart.  Enjoy the verbose splash!

If you don't like it, reverse the changes you made to the file.  Or, just use the backup you made.

---

### Post by Adrian on 2006-02-19
[QUOTE=Vetto]How do I change it (there are many different versions of bootslpashes on KDE-Look.org, some for lilo and other splash managers...)

I would think that there should be a "HOWTO" or tips section on this somewhere, I just cant find it. :([/QUOTE]

Check out this wiki page:
[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

---

### Post by Vetto on 2006-02-19
NRWILK, Thanks, but i should have been more clear: I'm not looking to get the verbose output, just change the splash from the default kubuntu load version

---

### Post by Vetto on 2006-02-19
[QUOTE=Adrian]Check out this wiki page:
[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)[/QUOTE]

I read that page, and it looks good...except it never says that USplash is the splash "engine" that kubuntu breezy is using by default.  Is it?

Also, KDE-Look has many other bootsplash themes that are more than 640 x480 16 colors...99% of them do not specify what app they are designed  for.  Any thoughts?

---

### Post by nrwilk on 2006-02-19
Whoops!  sorry.

I'll bet you'll find a bunch more info here:
[http://www.bootsplash.org/](http://www.bootsplash.org/)

They have some splashes for download.  Also, info on creating your own.

---

### Post by Vetto on 2006-02-19
Holy Cow!  I am not recompilling my kernel for a bootsplash.  I tried to install "splashy" from the debian repositories (which I have used before on a non-kubuntu system)  but is wants me to remove usplash...which is fine except kubuntu-desktop depends on usplash!

---

### Post by nrwilk on 2006-02-19
kubuntu-desktop is just a metapackage, it can safely be removed.

---

### Post by Adrian on 2006-02-19
[QUOTE=nrwilk]kubuntu-desktop is just a metapackage, it can safely be removed.[/QUOTE]

Unless you do it with **aptitude** ;)

---

### Post by Vetto on 2006-02-19
[QUOTE=nrwilk]kubuntu-desktop is just a metapackage, it can safely be removed.[/QUOTE]
Thanks...i removed it via synaptic and all is well.
I found a way to make splash screens for the default usplash[http://ubuntuforums.org/showthread.php?t=77290]("http://ubuntuforums.org/showthread.php?t=77290")
There is a shell script there that does the install from any png (as long as it is 16color indexed correctly )

Thanks guys.

---

