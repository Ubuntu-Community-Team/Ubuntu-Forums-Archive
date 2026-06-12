---
title: "Windows doesn't load after resizing partitions"
date: 2009-10-30
forum: General Help
---

### Post by Gonchos on 2009-10-30
I re-sized and deleted some partitions and the result is a 40GB Win 7 and a 40GB Ubuntu. After updating Grub, Ubuntu boots smoothly and with it's new 40GB space to play around.

But 7 is not so comfortable as it won't boot. It says the device doesn't meet the system requirements and to solve it, asks me to use the win CD an run "repair".

I'm using Grub2 on Karmic

Thanks!

---

### Post by sliketymo on 2009-10-30
> **Gonchos said:**
> I re-sized and deleted some partitions and the result is a 40GB Win 7 and a 40GB Ubuntu. After updating Grub, Ubuntu boots smoothly and with it's new 40GB space to play around.

But 7 is not so comfortable as it won't boot. It says the device doesn't meet the system requirements and to solve it, asks me to use the win CD an run "repair".

I'm using Grub2 on Karmic

Thanks!

:popcorn: Yep,do what it says.You'll have to fix your windows boot first,then pop in your Ubuntu CD,(if you have one),and re-install grub.

---

### Post by theozzlives on 2009-10-30
> **Gonchos said:**
> I re-sized and deleted some partitions and the result is a 40GB Win 7 and a 40GB Ubuntu. After updating Grub, Ubuntu boots smoothly and with it's new 40GB space to play around.

But 7 is not so comfortable as it won't boot. It says the device doesn't meet the system requirements and to solve it, asks me to use the win CD an run "repair".

I'm using Grub2 on Karmic

Thanks!

You're supposed to use the Disk Manager in 7 to resize your 7 partition.

---

### Post by darkksyde on 2009-10-30
Your partitions may have gone corrupt, I hope you solve your problem

---

### Post by abrahmm on 2009-10-31
I'm having  a very similar problem. I have two hard drives, one had just Windows XP on it, the other had Ubuntu and Windows 7. I deleted the ubuntu partition and expanded 7 to take up the whole drive, while shrinking the XP partition and creating two new ones for Ubuntu and Kubuntu. Grub2 initially gave me a Windows 7 and a Windows XP option, the XP one booted fine, and the 7 one wouldn't boot. Following instructions, I put the Windows 7 disk in and ran repair, then updated grub.
At this point it says Windows 7 for both Windows entries, but 7 still won't boot and XP boots fine. I run Windows 7 repair again, this time Windows 7 boots but XP won't. I run XP repair and now XP boots but 7 Won't. And on and on and on. 

Any advice? Thanks, appreciate it!

---

### Post by Gonchos on 2009-10-31
but I've already resized my Win 7 partition... what will the "repair" really do? 

I have important data on my Ubuntu partition and I hardly ever use 7, so I don't want to take any risk to save windows.

---

