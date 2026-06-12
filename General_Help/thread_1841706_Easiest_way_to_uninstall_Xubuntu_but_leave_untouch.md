---
title: "Easiest way to uninstall Xubuntu but leave untouched"
date: 2011-09-09
forum: General Help
---

### Post by BKbroila on 2011-09-09
I've been intending to uninstall Xubuntu for quite a while, but never got around to it...

So I asked in another thread yesterday here: [http://ubuntuforums.org/showthread.php?t=1838584](http://ubuntuforums.org/showthread.php?t=1838584)

I just wanted to make sure that bcbc's recommendation would be easiest and best for me. I already have Win7 installed, and would love to keep it untouched. 

My biggest worry is about the bootloader - I don't want to mess it up and have my laptop running loops or grub/burg still loading up.

---

### Post by 2F4U on 2011-09-10
If you are totally horrified, then leaf it as it is if you don't need the space currently occupied by Xubuntu. If you need the space or absolutely want to get rid of Xubuntu, then first recover the Windows boot loader as described in the thread. Don't touch Xubuntu at this time, just recover the Windows boot loader. If that goes well, go ahead and delete Xubuntu partitions. If it doesn't go well, there is always the chance to recover grub and boot as before.

---

### Post by FormatSeize on 2011-09-10
> **BKbroila said:**
> 
I just wanted to make sure that bcbc's recommendation would be easiest and best for me. I already have Win7 installed, and would love to keep it untouched. 

This is pretty straightforward and correct if you know how to follow those steps.

If you don't feel comfortable with the steps described by bcbc, then you shouldn't mess with it unless you know how to do what he/she is talking about. Those steps won't mess with your Win7 install. 

But to be honest, I have never dealt with LiLo successfully. Luckily, that part isn't absolutely necessary. But if you can be sure that you can re-install the Windows bootloader to the MBR, then be sure that when you boot you go straight into Windows, things will work out so that you don't have to worry about the process affecting your Win7 installation.

---

### Post by BKbroila on 2011-09-10
> **FormatSeize said:**
> This is pretty straightforward and correct if you know how to follow those steps.

If you don't feel comfortable with the steps described by bcbc, then you shouldn't mess with it unless you know how to do what he/she is talking about. Those steps won't mess with your Win7 install. 


Alright thanks. Do you know if the command he wrote (bootrec /fixmbr) would require a installation cd? Or is that the only thing I would need to run? Google just keeps showing unrelated links

---

