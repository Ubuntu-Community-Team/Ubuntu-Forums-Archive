---
title: "Automounting external hard disk in a defined place."
date: 2006-06-27
forum: General Help
---

### Post by paulyche on 2006-06-27
Hi, I've had a look around the forums but I can't find the answer to this:

I've got an external disk that I'd like to mount to a specific location. I've put this location in my fstab and it mounts on bootup as expected.

The thing is I don't have this drive turned on all the time and I'd like it if it'd automount to this location when I turn it on during an ubuntu session.

Instead I have to turn it on and then select the drive in admin >> disks and enable the drive (bit of a chore). It then mounts where I want it, but is labelled as "IOMEGA_HDD" rather than after the mount point like one would expect.

Not an urgent problem by any means, but it's been anoying me.

1. Do I have to enable the drive every time?
2. Any idea why the disk is appearing on my desktop/places with the wrong name?


Yours sincerely,

The laziest man on the ubuntu forums.

---

### Post by turbojugend_gr on 2006-06-27
Answer to question 2: 
That is because FSTAB is mounted at startup, while in case of usb stick and other such devices are auto handled outside the fstab when pluged in during a session. So if you want it to mount at your fstab defined directory you should turn it on and instead of going through disk managment try this:
> fstab -a

this is going to remount all your fstab defined partitions-drives automaticly. Normally including this drive.

The best solution should be though to turn your drive on before booting, when  you wish to use it.(kind of an answer to question 1)

I hope I was helpfull. I will be away for the next week, so I won't be able to follow your progress. Though what i suggested should work gracefully and shouldn't trouble you.

---

### Post by paulyche on 2006-06-27
> That is because FSTAB is mounted at startup, while in case of usb stick and other such devices are auto handled outside the fstab when pluged in during a session.

Yes, that would make sense. I think you meant
```
mount -a
```
but it works and mounts my usb drive.
Think I'll make a panel button to do just that with a click.

The mounted drive is still listed as "IOMEGA_HDD" though..

Would just leave my disk on all the time, but it hums so damn loudly when I'm trying to listen to quiet music!

---

### Post by iluva on 2006-06-27
hey, it is just an idea, but it could function. plug your drive an look were it mounts. <e.g. /media/IOMEGA_HDD/>, this directory should stay alway the same, doesn't it?  plug it, automounter will mount it, and make a softlink to whatever place you like <e.g. /mnt/yeah/ oder ~/Desktop/thats-it> and when you have pluged the drive, you can access the link, when you don't it's not accessible. just an idea

---

### Post by scxtt on 2006-06-27
[quote=paulyche]The mounted drive is still listed as "IOMEGA_HDD" though.[/quote]this is information that the device supplies, i have a little 256mb lexar "jumpdrive" and when plugged in would mount as "LEXAR" on the desktop all the time ... i've since reformatted it, and it now shows up as "usbdrive" on the desktop ... so i'm thinking there's a "hidden" file in there somewhere (which i wiped out) which supplies the name ... i think i found it once, when i was looking @ the drive in recovery mode and saw "LEXAR",  but it's now gone ...

btw, what interface does this drive use?

---

