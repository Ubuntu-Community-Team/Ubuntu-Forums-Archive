---
title: "Want Vista Bootloader - Not Grub"
date: 2010-05-09
forum: General Help
---

### Post by Sir Prospect on 2010-05-09
Hi everyone,

I am not that great with ubuntu, so bear with me here.

After installing Ubutnu 10.04, I realised that when booting, it gave me the grub screen instead of the usual dual-boot screen, (which i presume is the vista bootloader), and my question is how do i get that back, as I feel Grub is just too cluttered...

Thanks in Advance!

---

### Post by Seal Daemon on 2010-05-09
Arrow UP/DOWN + Enter .. cluttered ? :-s

---

### Post by wilee-nilee on 2010-05-09
> **Sir Prospect said:**
> Hi everyone,

I am not that great with ubuntu, so bear with me here.

After installing Ubutnu 10.04, I realised that when booting, it gave me the grub screen instead of the usual dual-boot screen, (which i presume is the vista bootloader), and my question is how do i get that back, as I feel Grub is just too cluttered...

Thanks in Advance!

I'm not sure there is a way to use a MS bootloader with Ext4, if it is booting all operating systems, consider yourself lucky, and get used to it. Unless somebody has another idea.

I would also say that grub is a much better bootloader, it can boot MS and also be modified, your impression of clutter is I think not understanding it, and maybe some bias from MS forums where by and large they do not know how to deal with it or the MBR. Other then using a 3rd part or auto-repair in W7.

---

### Post by Sir Prospect on 2010-05-09
So is there any way possible, i dont mind re-installing Vista or Ubuntu (Since I just installed both of them)

And yes, it is cluttered for me, why have 5 options, including rarely used things like memtest, when you can have 2?:P

---

### Post by wilee-nilee on 2010-05-09
> **Sir Prospect said:**
> So is there any way possible, i dont mind re-installing Vista or Ubuntu (Since I just installed both of them)

And yes, it is cluttered for me, why have 5 options, including rarely used things like memtest, when you can have 2?:P

What your seeing is probably vista and vista recovery and the kernels for Ubuntu. I have tried with the little I know to explain, but maybe somebody knows different

Welcome to open source you have to know what your doing, and what not to do. I use XP and W7 so I am familiar with dual booting etc.

---

### Post by garvinrick4 on 2010-05-09
> **Sir Prospect said:**
> So is there any way possible, i dont mind re-installing Vista or Ubuntu (Since I just installed both of them)

And yes, it is cluttered for me, why have 5 options, including rarely used things like memtest, when you can have 2?:P

In your file system you can go to /etc/default/grub and uncomment the lines you do not
want to see in grub menu. You can not have recovery or mem test takes all of 30 seconds.

Alt/F2
type in gksudo nautilus the open file system it will say "root" which lets you make changes.
go to etc to default to grub. Then uncomment which ever line you want by taking away the # in front of line. Then have to save.

Now go to [www.ubuntupocketguide.com]("http://www.ubuntupocketguide.com") and it will give you a good pdf file  reference quide to read up on. 

Go to link below and bookmark your ubuntu OS and you will have the manual to read.

[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

---

