---
title: "fixing XP boot registry with Ubuntu ?"
date: 2009-10-27
forum: General Help
---

### Post by 2blue on 2009-10-27
My father has an old computer with Windows XP on it. For some reason he shut it down last night holding the start button down, when it was installing several updates. Now it will not boot at all, and I am wondering if I can run a "fsck" command from the Ubuntu CD or some kind of linux booting soft ware? We cannot find the original recovery XP CD. 

Any idea what might have happened? I have only Ubuntu on my laptop these days, and this is the only internet connection working well right now.

---

### Post by kasrawis on 2009-10-27
what error do you face when you turn your XP on can you specify that

---

### Post by 2blue on 2009-10-27
I only get the standard message that windows could not boot up as usual and the regular options for booting in safe mode, last working configuration, or safe mode with command line only etc. Neither of them works.

---

### Post by lykwydchykyn on 2009-10-27
There isn't a fsck utility for ntfs, about all you can do is use chkdsk from a Windows CD.  You can run badblocks and determine if the disk is failing, but it won't fix anything.

---

### Post by drrakken on 2009-10-27
I would suggest downloading the files required for a startup disk and then trying to fix the boot.ini or fixboot or mbr.

---

### Post by 2blue on 2009-10-27
Thanks for replies. I suppose computer has to be sendt to  someone who can fix it, at least retrieve data and reinstall Windows.  

I have found the original XP recovery that came with my Fujitsu laptop, but I think it only works with my laptop, and not any other brands.

---

### Post by 2blue on 2009-10-27
> **drrakken said:**
> I would suggest downloading the files required for a startup disk and then trying to fix the boot.ini or fixboot or mbr.

What files do I need?

---

### Post by mike555 on 2009-10-27
I recommend using the Ubuntu live cd to mount the Windows partition (if you can) and copy the "documents & settings" folder to an external usb drive or thumbdrive .

---

### Post by mike555 on 2009-10-27
You might also want to try a different bootloader before paying some to fix it ....... maybe "GAG"



that is if the MBR is the only problem.

---

### Post by pricetech on 2009-10-27
I doubt you'll be able to fix it.  Shutting down during an update usually pretty much trashes winders.

However:  If you can find the recovery disk for the computer you might try Recovery Console and may be able to restore to an earlier time before the updates began.

Boot to the live CD and salvage your data before you attempt anything else though.

Good luck to you either way.

---

