---
title: "Grub not recognizing kernel?"
date: 2010-02-09
forum: General Help
---

### Post by extc on 2010-02-09
Ok, here is one:  Booting fine, selected Ubuntu from the list (XP is the other.) Goes straight to the GRUB prompt 1.97 4 and don't know what to do. Any attempt to use the root command with any of the partitions is met with "Cannot find kernel."

Using:
Koala 9.10
Intel Dual core i386 32-bit.

Possible cause: selected "update grub" from the menu in recovery mode instead of drop to shell.

Would be very greatful for any help.

Extc

---

### Post by Leppie on 2010-02-09
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by extc on 2010-02-09
looking into it right now!

---

### Post by extc on 2010-02-09
It was installed with wubi, and we have a theory - we believe that it did not create a partition, nothing could be found with different versions of grub. The linux is basically a folder within windows.

---

### Post by extc on 2010-02-10
Here it is. (results.txt attached)

It's like there are to two Grubs. I selected my old Ubuntu install from the first list, then I get the prompt for windows or Ubuntu, then when I select it, just the blank grub screen. New installation of Ubuntu on a new partition working fine. Old one cannot be accessed.

Thanks! :p;):D:D:D

---

### Post by Leppie on 2010-02-10
you seem to have a wubi install and a side by side install. which one is the one you are using (want to keep)?

---

### Post by extc on 2010-02-10
The wubi one was the one I can't access, I went to boot it oneday and I just got a blank grub prompt. Then I made a new installation from live CD (the second one, which works OK) in the hope that I could mount the first from the second and recover my files. But no luck. Tried all kinds of "mount" from the command prompt. But no luck.

Thanks

---

### Post by extc on 2010-02-10
Am trying as I type to recover with testdisk.

---

### Post by extc on 2010-02-10
It is not showing with testdisk even with deep search!

---

### Post by Leppie on 2010-02-10
if you just want to recover your files from the wubi install and then continue with the side by side install, have a look at this howto: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
or this page: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

testdisk will not find the wubi partition as it is just  a "file" in the windows partition.

---

### Post by extc on 2010-02-10
THank you very much for your help, but we have decided to give up and delete/re-install everything.

Bless,

extc

---

