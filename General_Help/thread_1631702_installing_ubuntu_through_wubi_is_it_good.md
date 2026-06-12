---
title: "installing ubuntu through wubi is it good?"
date: 2010-11-27
forum: General Help
---

### Post by jxgreat on 2010-11-27
I want to know Installing Ubuntu through Wubi has a performance loss or anything else or is it good idea?

---

### Post by wilee-nilee on 2010-11-27
> **jxgreat said:**
> I want to know Installing Ubuntu through Wubi has a performance loss or anything else or is it good idea?

Has it plus and minus parts what do you want in the end? and how much do you know about a open source OS?

---

### Post by ssulaco on 2010-11-27
I had real good luck with Wubi,it was fast enough for me,solid performance,I highly recommend Wubi for someone that wants to start using Ubuntu,and its easy to remove,use add/remove programs in Windows.
[http://psychocats.net/ubuntu/wubi](http://psychocats.net/ubuntu/wubi)

---

### Post by wilee-nilee on 2010-11-27
> **ssulaco said:**
> I had real good luck with Wubi,it was fast enough for me,**solid performance**,I highly recommend Wubi for someone that wants to start using Ubuntu,and **its easy to remove**,use add/remove programs in Windows.
[http://psychocats.net/ubuntu/wubi](http://psychocats.net/ubuntu/wubi)

So is a real dual boot, unless you get grub dumped to the mbr and have no recovery cd/reader, and want to wait probably at the least 24 hours for help on this forum for the one person who knows this installation quite well.

I'm not anti wubi I am anti making it much harder to fix and a OS inside a OS, which well has it's own problems.

---

### Post by jxgreat on 2010-11-27
Finally installed Ubuntu using Wubi after defragging the harddisk and works great no performance loss.

---

### Post by wilee-nilee on 2010-11-27
> **jxgreat said:**
> Finally installed Ubuntu using Wubi after defragging the harddisk and works great no performance loss.

So that is great, just don't accept any grub updates. You have a grub menu to boot in but it's a different setup take my word on this.

---

### Post by ssulaco on 2010-11-27
> **wilee-nilee said:**
>  You have a grub menu to boot in but it's a different setup take my word on this.
its called Windows bootloader

---

### Post by dabomb1022 on 2010-11-27
> **ssulaco said:**
> its called Windows bootloader
Haha! That made me laugh. Yes, you're right though, its not grub when you install wubi. It's just Windows bootloader.

---

### Post by bcbc on 2010-11-27
wilee-nilee is right. Don't accept any grub updates - when update manager prompts you uncheck grub-pc and grub-common. Wubi uses grub, just not in the MBR.

---

