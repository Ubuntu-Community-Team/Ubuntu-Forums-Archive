---
title: "Problem Booting Windows after Routine Ubuntu Upgrade"
date: 2009-10-26
forum: General Help
---

### Post by Plumtreed on 2009-10-26
Where did this come from? The last thing of any importance was a routine Ubuntu upgrade. Perhaps it wasn't particularly routine because it took a considerable amount of time. It all worked OK and my 'puter was deemed to be 'up-to-date'

The problem lies in trying to boot to Windows which was always fairly routine but now fails! I have Win98 dual booting with 9.04 on two hard disks. I keep Win98 because it is the only thing that runs an accounting program that suits me and my small business.

Grub seems to work and when I boot into Win98 I get the start-up logo but it hangs with the message "File Allocation Table Bad, drive C"

Has the upgrade upset things or has my Win98 just died? Any suggestions?

---

### Post by arrrghhh on 2009-10-26
It sounds like either GRUB didn't update your menu.lst properly, or your Win98 is hosed...

What I would try (just to rule it out) would be to disconnect the hard drive that has Ubuntu/GRUB on it.  Just have that Win98 hdd plugged in, and adjust your boot order so it boots from that device first.  Then see what happens.  If it boots OK, there's probably something wrong with the GRUB entry for Win98.  If it doesn't, then you KNOW for a fact it's Win98.

---

### Post by Plumtreed on 2009-10-26
Thats a good idea but Grub shows the Win98 entry and if I choose it the Win98 logo shows for about 5 seconds before trying to activate.

As Win98 tries to fire up it hangs at the error message. I am guessing that Grub may be OK.

I will try to boot directly to the Win98 disk???

---

### Post by Plumtreed on 2009-10-27
I guess that the update damaged the FAT file and I will have to learn how to set that up again in order to get my Windows back.

---

