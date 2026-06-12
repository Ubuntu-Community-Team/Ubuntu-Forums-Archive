---
title: "Computer freezes when gdm shows"
date: 2011-01-11
forum: General Help
---

### Post by kabeza on 2011-01-11
Hi
I was browsing on Firefox, and computer just reset.
After it restarted, it shown grub correctly, started like always, but after Ubuntu plymouth, gdm started and then computer froze when showing the userlist.

There's no way to do anything but pressing reset button.

The computer has dual-boot shared with Windows XP, which works ad run perfectly. Keyb and mouse are fine. I also did a hard disk and memory check, without problems.

Question: I guess the only option left is to do a repair. Which data will I loose in case I put a 10.10 DVD and do a repair?

PS: any other way to debug problem?

Ubuntu 10.10, latest kernel, didn't upgrade since 2 or 3 weeks
2gb ram, 160gb disk, Intel C2D E7200, GForce 8400GS

---

### Post by Rubi1200 on 2011-01-11
Hi,
please post the contents of this file (wrap with code tags when posting back)
> .xsession-errors
You can find it in your home folder (it is hidden so use Ctrl + H to unhide).

You can also try setting nomodeset as you boot to see if that makes a difference.

As the computer starts, GRUB menu > highlight entry > press "e" to edit > find the line with and remove quiet splash and type nomodeset > "Ctrl" + "X" to boot

---

### Post by kabeza on 2011-01-12
Hi again
I could read the linux partition from Windows and could copy the .xsession-errors file. I've attached and shared in pasteBin

[http://pastebin.com/GVtneEAF](http://pastebin.com/GVtneEAF)

---

### Post by kabeza on 2011-01-14
sorry, got error when posting but indeed got posted

---

### Post by kabeza on 2011-01-14
Hi again
Sorry for bumping, but I cannot find anything that can guide me to solve this error. Did any read the .xsession-error file I posted to see if something is wrong?

Please at least someone confirm me if repairing the install from DVD will erase any personal data from /home/***. I was doing it, but cancelled when it asked me to install Ubuntu again (because I think it will repartition everything, screw the windows install, etc. and this freaks me)

I need that PC to work and is the only with linux at the office :(

Thanks

---

### Post by kabeza on 2011-01-14
sorry

---

