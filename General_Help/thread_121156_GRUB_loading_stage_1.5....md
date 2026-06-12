---
title: "GRUB loading stage 1.5..."
date: 2006-01-24
forum: General Help
---

### Post by zapoqx on 2006-01-24
As the title says, I have a problem with GRUB now.

Earlier I was using XP installing something and then it froze. So I had to tell my laptop to restart by pushing and holding the lovely power button.

So I got the system to restart and it gets to:
GRUB loading stage 1.5

Then the system reboots. I can use any cd/dvd bootable disc to start them up ahead of the hard drive, but other than that, I have no control as to getting it to boot from the hard drive itself..

I checked to see if it was a hardware thing but it seems I can access all parts of the system (but have yet to check the hard drive section).

If you must know, I have 3 partitions on my 100GB hard drive, 10.2GB for WinXP, 20.1GB for Kubuntu, and the remaining for Windows XP's Various files I'd put on.

So can anyone help me on this?

---

### Post by linuxden on 2006-01-24
Well i dont know why this has happened , am not a Wizzard... But you could try reeinstalling grub...

That usually does the trick...

How confident are using linux?

---

### Post by zapoqx on 2006-01-24
Not all that confident yet.  I just had some help with a friend yesterday to get the ATI drivers working correctly as well as a number of other things (ndiswrapper and all).

So how do I re-install the GRUB bootup? *bows the I'm not worthy bow*

---

### Post by linuxden on 2006-01-24
[QUOTE=zapoqx]Not all that confident yet.  I just had some help with a friend yesterday to get the ATI drivers working correctly as well as a number of other things (ndiswrapper and all).

So how do I re-install the GRUB bootup? *bows the I'm not worthy bow*[/QUOTE]

No need for that...!!! (the bowing)

I was just wondering so that i may best advise you...

[http://www.ubuntuforums.org/showthread.php?t=113730&highlight=grub+rescue](http://www.ubuntuforums.org/showthread.php?t=113730&highlight=grub+rescue)

the technique described there is really easy...

---

### Post by zapoqx on 2006-01-24
Thanks but there is a problem now.  It seems it is routine and I don't know how but I know it has to do with Windows XP.  For some reason, it ends up messing up GRUB after a while and I think GRUB also sometimes messes up my powerdown feature as sometimes I find my laptop doesn't shut down correctly or start back up correctly from the standby and hibernation states. Any help?

---

### Post by linuxden on 2006-01-25
[QUOTE=zapoqx]Thanks but there is a problem now.  It seems it is routine and I don't know how but I know it has to do with Windows XP.  For some reason, it ends up messing up GRUB after a while and I think GRUB also sometimes messes up my powerdown feature as sometimes I find my laptop doesn't shut down correctly or start back up correctly from the standby and hibernation states. Any help?[/QUOTE]

Yes hibernate and standby features on laptops are incredibly light on linux... some work straight off some dont... there have been loads of threads on that before perhaps search in the laptop section of this forum...

with regards to your "windoze" messing up GRUB and in turn GRUB messing up hibernate+Shutdown it shouldnt do, i have exactly the same setup as you windows on my master drive and linux on my slave...

EDIT: Sorry confused your post with another i was helping out late last night.... having windows and linux on same hard-drive should not be a prob either...

Never had a prob ;o)

---

### Post by zapoqx on 2006-01-25
Alright Thanks. I hope I figure out what causes this.

---

