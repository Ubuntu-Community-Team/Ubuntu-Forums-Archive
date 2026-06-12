---
title: "ClamAV on-access scan (clamnd &amp; ClamFS)"
date: 2010-02-13
forum: General Help
---

### Post by veggen on 2010-02-13
From what I've gathered, it's smart to have an antivirus if you are on a dual-boot system with Windows, which I am. Reading the specs seems to indicate that ClamAV is the only one capable of on-access scanning, so I'm planning to go for that option. Now, what I'm confused about is the purpose of clam-deamon and ClamFS. Both are supposed to be used to enable on-access scanning. Do I need one of the two or both? Are there any advantages to one over the other? Is on-access really necessary?

I know this is not really an Ubuntu question, but this is the only place for asking I could come up with. I searched before posting but there were no topics on this specific matter.

Thanks for any advice.

---

### Post by veggen on 2010-02-13
Sory for such a soon bump... topics sink very fast here...

---

### Post by ndoro on 2010-04-21
i have the same problem...

waiting for someone can help this...

---

### Post by dcstar on 2010-04-21
> **veggen said:**
> 
.......
Now, what I'm confused about is the purpose of clam-deamon and ClamFS. Both are supposed to be used to enable on-access scanning. Do I need one of the two or both? Are there any advantages to one over the other? Is on-access really necessary?


[LIST=1]
[*]A daemon loads into memory and remains there. Clamd is a daemon version of Clamfs. Clamfs has to be loaded and unloaded every time it is used.
[*]There is no point in on-access scanning of any Linux file at the moment. Linux is not Windows.
[/LIST]

---

### Post by ndoro on 2010-04-22
what about protection for samba ?
is that not necessary ?

---

### Post by veggen on 2010-04-26
> **dcstar said:**
> [LIST=1]
[*]A daemon loads into memory and remains there. Clamd is a daemon version of Clamfs. Clamfs has to be loaded and unloaded every time it is used.
[/LIST]
Ok, I get it now. Thanks for clarifying it.
> **dcstar said:**
> [LIST=1]
[*]There is no point in on-access scanning of any Linux file at the moment. Linux is not Windows.
[/LIST]
Ok, but what about Windows files that are easily accessible through auto-mounted partitions? Is this an unnecessary worry or an actual threat?

Thanks

---

### Post by 98cwitr on 2010-04-26
unnecessary worry, a windows malware CANNOT infect a Linux box at the moment.

---

### Post by veggen on 2010-04-26
Hehe, I think you got me wrong :) I was worried about getting Windows' files infected by surfing unprotected in Ubuntu (with NTFS partitions automounted and Wine installed).

---

