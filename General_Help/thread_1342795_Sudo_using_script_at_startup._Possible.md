---
title: "Sudo using script at startup. Possible?"
date: 2009-12-01
forum: General Help
---

### Post by kajman on 2009-12-01
Hi all!

My laptop lost one of it's hard drives (as I've checked in BIOS diagnostics), so I've reinstalled whole system only on the other working drive. Everything is almost ok.

As I don't use my first drive which is corrupted I like to have it powered off (it heats a lot, and my computer freezes after a while, so I have to have my disk turned off).

I use the following 
```
sudo hdparm -Y /dev/sda
```
to force it to sleep mode, and it helps.

Is it possible to have my system run this command right after startup? Is it possible to do it automatically without having to enter password every time?

kajman

---

### Post by smani on 2009-12-01
You could create a custom startup script, either using the old init system (from which ubuntu is moving away though), for example see [http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian](http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian) , or with the new upstart system which is intended to replace init, see for example [http://www.linux.com/archive/feature/125977?theme=print](http://www.linux.com/archive/feature/125977?theme=print) .

---

### Post by 3rdalbum on 2009-12-01
> **kajman said:**
> Hi all!

My laptop lost one of it's hard drives (as I've checked in BIOS diagnostics), so I've reinstalled whole system only on the other working drive. Everything is almost ok.

As I don't use my first drive which is corrupted I like to have it powered off (it heats a lot, and my computer freezes after a while, so I have to have my disk turned off).

I use the following 
```
sudo hdparm -Y /dev/sda
```
to force it to sleep mode, and it helps.

Is it possible to have my system run this command right after startup? Is it possible to do it automatically without having to enter password every time?

kajman

It certainly is possible. Open the file "/etc/rc.local" as root with a text editor, and add:

```
hdparm -Y /dev/sda
```

before the "exit" line.

The contents of /etc/rc.local are run as root, so you don't need to use sudo.

---

### Post by kajman on 2009-12-01
The second answer was great in simplicity and I've learned something that might be handy in the future, but it doesn't solve this particular problem.

Maybe the script is run at a point that kubuntu still "wants something" from the drive, because when I checked just after boot the disk was running (again?).

As of the first answer, I would be happy to check it out when I find some more time (there's some reading to do :) )

Thank you both.

---

