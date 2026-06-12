---
title: "I screwed up something - need help fixing"
date: 2010-11-26
forum: General Help
---

### Post by damon118 on 2010-11-26
I installed Ubuntu 10.10 along side vista from the cd. My vista wouldn't boot up anymore, just kept getting BSOD.

I decided to use my recovery partition to restore windows and it wrote over everything, deleting ubuntu.

Now when I try to restart my comp it just boots into GRUB rescue prompt, saying partition not found.

My laptop didn't come with a recovery cd, just the partition. I also can't seem to get back into my recovery partion when I boot(f9) or anything for that matter...just GRUB rescue prompt.

Anyone know how I can fix this problem from within my ubuntu 10.10 live cd or any other bootable program?

Tried searching, tried using some command lines that was suppose to download widows sys files or something but could never get it to work.

---

### Post by praveenthivari on 2010-11-26
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by Quackers on 2010-11-26
You need to fix the Windows mbr by running Startup Repair up to 3 times from a Windows repair disc (not a recovery disc). If you don't have a Windows repair disc have a look below to get one.

[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

---

### Post by damon118 on 2010-11-26
> **Quackers said:**
> You need to fix the Windows mbr by running Startup Repair up to 3 times from a Windows repair disc (not a recovery disc). If you don't have a Windows repair disc have a look below to get one.

[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

Thanks for the link, any idea how I can burn the image to disc being that I am using a live cd. Tried starting the software with the live cd in then puting the blank cd in when I am ready to burn the image but it won't let me do anything without the live cd in.

---

