---
title: "No connections with a netbook"
date: 2010-01-26
forum: General Help
---

### Post by Bulova on 2010-01-26
Hi:

I installed 8.04 on my EeePC 2005. I use the Windows dual boot option. The netbook's hard drive was factory set with two partitions c and d.

Windows XP is on c; I put Ubuntu on d.

In Windows, I have both wireless and ethernet (sp?) working fine.

In Ubuntu, I have no wireless and no land line. The manual connection wizard pop-up shows no networks anywhere. 

How can I get Ubuntu connected? Would it be simpler to load another distro like Easy Peasy on top of Ubuntu? Or should I delete Ubuntu and start over?

Or is there an easy fix for 8.04?

Any pointers would be welcome. Thanks!

---

### Post by PhilGil on 2010-01-26
This is not really a solution to getting 8.04 to work - but why not install Karmic instead?  Sound, wireless, webcam - everything but 3 of the 4 hard buttons works perfectly out of the box on my EeePC 1000h.

---

### Post by gnack on 2010-01-26
Any reason why you chose 8.04?

What are the ethernet and wireless hardware?  If you don't know, this command is a starting place: 

lspci | grep -i net

---

### Post by sanderj on 2010-01-26
What's an EeePC 2005? When was the hardware released? 

Because if it's recent hardware, you should use a recent version of Ubuntu, ie 9.10, to recognize all hardware.

So live-boot 9.10 and see if the network works.

---

### Post by Bulova on 2010-01-26
The EeePC 2005 is an Asus Netbook. It's new in 2009.

I see now that I should have used a more recent version of Ubuntu. I'll try 9.10 netbook version.

Thanks to all who replied!

---

