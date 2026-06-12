---
title: "Computer restarts as soon as ubuntu is about to start"
date: 2010-08-14
forum: General Help
---

### Post by apoorvumang on 2010-08-14
Ubuntu was working fine, then I ran some program in wine that caused the computer to restart. After that, whenever Ubuntu is about to start (ie when those orange/white dots are on the screen), the computer just restarts.

I tried using a live cd, but the same thing happens - it restarts after that same screen.

What should I do?

---

### Post by ubudog on 2010-08-14
Are you sure you actually started the live cd?  You have to hit like F-10 or F-12.

---

### Post by apoorvumang on 2010-08-14
Yeah, it shows the screen saying try ubuntu, install ubuntu etc. 
Also, booting from live cd takes a considerable time to reach that screen where it restarts.

One more thing: I disconnected the hard drive and tried booting from cd - same result.

---

### Post by ubudog on 2010-08-14
Can you start into the recovery mode via GRUB?

---

### Post by apoorvumang on 2010-08-14
Update : Now, *sometimes* when I start the computer, Ubuntu starts up. I can open one or two programs, but if I try to close a program or open any folder, it restarts and gets stuck up in that restart loop.

---

### Post by apoorvumang on 2010-08-14
> **ubudog said:**
> Can you start into the recovery mode via GRUB?
How do I do that?

---

### Post by ubudog on 2010-08-14
At startup, right after the bios screen goes off, press shift until the GRUB menu comes up.  Select the Recovery Mode option.

---

### Post by apoorvumang on 2010-08-14
Ok, got into the recovery mode.
Now it shows me a recovery menu(resume, clean, dpkg, failsafex, grub, netroot)
What next?

---

### Post by apoorvumang on 2010-08-14
bump

---

### Post by DarkAmbient on 2010-08-14
> **apoorvumang said:**
> Ubuntu was working fine, then I ran some program in wine that caused the computer to restart. After that, whenever Ubuntu is about to start (ie when those orange/white dots are on the screen), the computer just restarts.

I tried using a live cd, but the same thing happens - it restarts after that same screen.

What should I do?

are you sure it was a application in Wine that causes your computer to restart? For what i know programs through wine should'nt be able to a harm Ubuntu at all. Atleast never heard of it.

---

### Post by apoorvumang on 2010-08-14
I think I got what caused it.
I started a game through wine (Unreal Tournament). It wasn't working earlier, so I messed up with its graphics settings, and was able to get it to run. Then it crashed after 10-15 seconds, and the whole restart problem began.
However, now I'm able to get Ubuntu to run without restarting by choosing the option "Start ubuntu in low graphics mode" when X says it was unable to get graphics card settings etc etc. So maybe that was the problem.

Still, how do I get it to run in normal graphics?

---

### Post by coolman98 on 2010-08-14
backup and reinstall?

---

### Post by apoorvumang on 2010-08-14
> **coolman98 said:**
> backup and reinstall?
Umm..this might sound really stupid, but do I need an external hard drive to backup, or just another partition on my existing hard drive, or a dvd?
Also, how do I actually backup?

---

### Post by apoorvumang on 2010-08-14
So I found this program called Deja Dup that backs up the file system.
Can I use that to backup my current installation on a different partition, reinstall ubuntu, and then restore it?
Also, is it enough to just include the home folder in the backup (thats whats there by default), or should some other folders be added?

---

### Post by DarkAmbient on 2010-08-14
You should know that UT is available for linux aswell. :-)

But on topic, if you got anything you would like to save in your homefolder. 

If your unable to run ubuntu and access your homefolder. Then one way is to backup is to start a livesession with the ubuntu cd. Then open the partition that hold your /home folder, and copy everything to another a external disk or burn it on a dvd or so :-)

Dont know if thats the best way but I mng to save some stuff at one time when my system was messed up thanks to trying out some unstable systempatches.

edit: sorry kept my post "unposted" for some time before clicking post reply so.. didnt read last post. Anyway,I've never tried deja vu as I dont find it annoying at all to do a full reinstallation of ubuntu, takes like 15min with a usb stick. I'm just backing up some config files or so... actually a clever way to backup (if it's only smaller files) is to make use of Ubuntu One. Then they gets restored on the next installation of ubuntu as soon as youve linked your computer to Ubuntu One.

But I'm sure there is tons of better way to backup files. I always keep "important" files on my external drives so I never lose em incase of a reinstall.

---

### Post by ubudog on 2010-08-14
All you need is a large enough flash drive.  Just boot into recovery mode, and copy your home directory or whatever using this command:
```
sudo cp -a /home/foo /media/nameofdrive
```

(foo being your username, nameofdrive being the name of your flashdrive)
You can find out the name of your flash drive by typing:
```
ls /media
```

---

