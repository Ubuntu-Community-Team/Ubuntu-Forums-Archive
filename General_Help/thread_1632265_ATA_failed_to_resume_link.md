---
title: "ATA failed to resume link?"
date: 2010-11-27
forum: General Help
---

### Post by PrvSAT on 2010-11-27
Hi,

I have my ubuntu running pretty decent under Lucid but I get some errors when it start loading and I spent lots of hours to find the source and I was unable to do it.
Basically I have 6 hard drives attached via an eSATA with port multiplier PCI card and all are mounting OK after system is fully loaded with no problem but as I was saying at boot up I get:
[  17.380569] ata7.11: failed to resume link (SControl 0)
[  18.408052] ata7.12: failed to resume link (SControl 0)
[  19.436048] ata7.13: failed to resume link (SControl 0)
[  27.192042] ata8.01: failed to resume link (SControl 0)
... and so on up to 40
[  40.116043] ata8.14: failed to resume link (SControl 0)

Could anyone please help me out and try to get rid of these errors? It also takes much longer to start since at every error it stays about 2 seconds. 
Thank you for reading this.

Oh, BTW:
I boot up from 2.6.22-26, mobo Asus P5B on a dual Core Intel.

and when I do: dmesg | grep ata
here is the result: [http://pastebin.com/qA4YC5ct](http://pastebin.com/qA4YC5ct)

---

### Post by PrvSAT on 2010-11-29
Hello,

Could anyone please give me an idea where the above errors are coming from?

---

### Post by doublemeat on 2011-05-17
I get the same thing when coming out of sleep. (And sleep takes longer than other OSes on this machine to come out of.)

In my case at least, it seems to have zero effect on anything - e.g. performance, or further ability to enter sleep. 

Since it doesn't seem to affect much for me, I haven't done any serious debugging (other than googling which brought me here and to other similar, unanswered posts). Have you narrowed down your performance issues to this problem, or could it be unrelated?

10.10 on Macbook Pro 6,2 (Core i5).

---

### Post by indium on 2011-08-07
seeing the same problem on mbp 6,2 and ubuntu 11.04. It delays the resume after sleep. I have no idea. Little info on the internet.

---

### Post by Cas07 on 2011-11-27
There is an [email]("http://comments.gmane.org/gmane.linux.ide/49801") on the linux mailing list that explains that it is nothing to be concerned about and a fix to change the message from Error to Warning has been submitted to 3.1 kernel.

---

