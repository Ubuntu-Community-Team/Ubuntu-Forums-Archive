---
title: "Load GRUB2 with GAG bootloader"
date: 2010-06-25
forum: General Help
---

### Post by ScttN485 on 2010-06-25
This may be a long post so bear with me.

I have an HP laptop that I am trying to boot both Ubuntu 10.04 and Windows 7. 

My first issue was trying to figure out how to stop my computer from rebooting from every time it reached the Windows 7 starting screen. I found a forum where it talks about GRUB2 having issues booting Windows properly [here]("http://ubuntuforums.org/showthread.php?p=8363434#post8363434"), but it didn't work for me. 

I instead found a workaround and installed GAG to the mbr to boot Windows. It worked perfectly for Windows, but unfortunately, it won't boot Ubuntu. I installed GRUB2 to Ubuntu's partition before that and kept getting and error in GAG saying "boot sector not found or invalid". I was able to reinstall GRUB to the partition with the live cd thinking something may have gotten corrupt. I was then able to boot into Ubuntu with GAG, but once I reboot my computer, with doing nothing to the operating system, I got the same "boot sector not found or invalid."

There may be another post similar to this, but I haven't found it yet. Does anyone have a solution to this or able to point me to the right thread to solve my issue?

---

### Post by Morbius1 on 2010-06-25
This has come up before and I don't think GAG is compatible with Grub2.

I looked at the sourceforge page and the last update was Aug 2008. That probably predates grub2. You might be able to remove grub2 and replace it with grub but I've used BootIT NG for so long I don't know how to do that.

Doing a quick search on the forum yielded this:
[http://ubuntuforums.org/showthread.php?t=1360501](http://ubuntuforums.org/showthread.php?t=1360501)

---

### Post by ScttN485 on 2010-06-26
GAG was able to boot into GRUB2 only after I kept restoring it from the LiveCD. but I forgot about BootIt NG. I used it before, so I might just try it again. Thank you. I'll let you know how it goes.

**Update:** BootIt NG ran into the same problem as GAG. Ubuntu was able to start once after I repaired GRUB, but when I rebooted, I wasn't able to boot into Ubuntu again. I decided to just revert to grub-legacy. It seems to be working for both Ubuntu and Windows, so far. I actually found a better solution on how to revert to grub-legacy at the bottom of [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2").

---

### Post by Don Barzini on 2010-06-26
> **ScttN485 said:**
> Does anyone have a solution to this or able to point me to the right thread to solve my issue?

You probably need to download the *bootinfo script* to a local directory and follow the instructions and post the output of the Results.txt file.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That way it will become clear as to what is going on with your system.

---

### Post by Morbius1 on 2010-06-26
That's odd about BootIt NG. I have it on multiple machines all multibooting with with at least one grub2 dependent linux os.

Anyway, at least you found a solution.

---

