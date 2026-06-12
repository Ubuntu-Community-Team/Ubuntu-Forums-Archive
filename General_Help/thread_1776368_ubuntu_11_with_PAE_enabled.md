---
title: "ubuntu 11 with PAE enabled"
date: 2011-06-06
forum: General Help
---

### Post by waitformee on 2011-06-06
dear all,

I am very new to ubuntu, I hope this is the correct place for me to post this question.

I just installed ubuntu 11.04 from the ISO downloaded and i installed PAE. but my memory is still 3.2gb. I have 5 gb and my system information in my bios indicated 5 gb.

may i know how can I check what is wrong?

My PC is pentium 4 ht.

Please help. thanks in advance.

---

### Post by wildmanne39 on 2011-06-06
> **waitformee said:**
> dear all,

I am very new to ubuntu, I hope this is the correct place for me to post this question.

I just installed ubuntu 11.04 from the ISO downloaded and i installed PAE. but my memory is still 3.2gb. I have 5 gb and my system information in my bios indicated 5 gb.

may i know how can I check what is wrong?

My PC is pentium 4 ht.

Please help. thanks in advance.
Hi put this in a terminal and make sure you have the kernel with pae installed.
```
uname -a
```

---

### Post by waitformee on 2011-06-06
[COLOR=#00681C]Linux mee 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

It is [/COLOR][COLOR=#00681c]generic-pae, does it means that it is enabled?
[/COLOR]

---

### Post by psusi on 2011-06-06
Why not just use the 64 bit version?  At least try the 64bit live cd and see if it can see all the ram.  If not, then you have a motherboard problem.

---

### Post by wildmanne39 on 2011-06-06
Hi, his computer is to old it will not run 64 bit, I think is the issue,it is a penthium 4.

---

### Post by wildmanne39 on 2011-06-06
> **waitformee said:**
> [COLOR=#00681C]Linux mee 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

It is [/COLOR][COLOR=#00681c]generic-pae, does it means that it is enabled?
[/COLOR]
Hi, no it should be working since it is installed, I do not know of anything you need to do to enable it, I used pae three years ago and I did not do anything but install the kernel for it.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **waitformee said:**
> dear all,

I am very new to ubuntu, I hope this is the correct place for me to post this question.

I just installed ubuntu 11.04 from the ISO downloaded and i installed PAE. but my memory is still 3.2gb. I have 5 gb and my system information in my bios indicated 5 gb.

may i know how can I check what is wrong?

My PC is pentium 4 ht.

Please help. thanks in advance.

Try this:
```

sudo aptitude install linux-generic-pae linux-headers-generic-pae

```

---

### Post by psusi on 2011-06-06
If it is that old then it may not be able to handle more than 4gb of ram.  Also 5gb is a rather odd amount, are you sure it isn't just 4?  Check dmesg for the section listing the e820 bios memory map.

---

### Post by waitformee on 2011-06-08
I have 2 x 2gb ram and a 1 gb and a 512mb.

In my BIO, it says 5.5GB. The PC is about 6 years old. My worries too that it is too old.

I tried 
sudo aptitude install linux-generic-pae linux-headers-generic-pae[B]

sudo: aptitude: command not found

[/B]

---

