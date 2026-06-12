---
title: "Stuck on boot (Cant turn computer on) Help!"
date: 2010-07-26
forum: General Help
---

### Post by CyphVx on 2010-07-26
Well, gotta ubuntu up and running. installed updates and drivers and went to reboot my computer. After i chose "Ubuntu" from the boot menu i ran into this..

error: no such device: 7db32040-ebld-489d-af6e-09e6e02cd475
grub rescue>

I can type stuff after the grub rescue: 
but i have no idea what to type to fix this or bypass it, i have tried everything and i cant bypass it to get my computer to start..

Help me!

---

### Post by bcbc on 2010-07-26
How did you install ubuntu? If it was within Windows (WUBI) then see this thread: [http://ubuntuforums.org/showthread.php?t=1539675](http://ubuntuforums.org/showthread.php?t=1539675)

Bypass the grub rescue commands. They did nothing. If this is not your problem, please post back with some more detailed info.

---

### Post by CyphVx on 2010-07-27
Yes, i installed it with wubi.

i ran

>bootfix (not sure if that is the command actually, kinda forgot.)

and >bootmbr

got XP back up, does this mean i am going to have to reinstall ubuntu?

---

### Post by prodigy_ on 2010-07-27
Wubi isn't meant for permanent setups. Download a LiveCD of 10.04 and reinstall from it.

---

### Post by bcbc on 2010-07-27
> **CyphVx said:**
> Yes, i installed it with wubi.

i ran

>bootfix (not sure if that is the command actually, kinda forgot.)

and >bootmbr

got XP back up, does this mean i am going to have to reinstall ubuntu?

Try ubuntu - it should still work.

---

### Post by de Bacon on 2010-07-27
I have the same problem, > error: no such device: 7db32040-ebld-489d-af6e-09e6e02cd475
grub rescue>
I installed from a live disc months ago.  
I have several hdds on this box, one has the hardy version on it.  But i disconnected that.  I can run it by getting to some odd selector screen at boot.  I don't know what it is called, it give the option to start from, with a list.  I select hard drive, then select the correct hard drive and it starts right up. That is nonsense though.

I did think to start a new thread but... this is the same problem in terms of its definition, and stated better than I could!

Thanks,

---

### Post by bcbc on 2010-07-27
> **de Bacon said:**
> I have the same problem, 
I installed from a live disc months ago.  
I have several hdds on this box, one has the hardy version on it.  But i disconnected that.  I can run it by getting to some odd selector screen at boot.  I don't know what it is called, it give the option to start from, with a list.  I select hard drive, then select the correct hard drive and it starts right up. That is nonsense though.

I did think to start a new thread but... this is the same problem in terms of its definition, and stated better than I could!

Thanks,

I don't think this is wubi-related. This particular error can occur for different setups and the fix is different. It may be related to the same grub-pc update (I've seen this problem already in the past couple of days). So if you're not wubi, you need to reinstall the grub bootloader to your MBR. If you're wubi you need the windows bootloader.

---

### Post by bcbc on 2010-07-27
> **prodigy_ said:**
> Wubi isn't meant for permanent setups. Download a LiveCD of 10.04 and reinstall from it.

I don't recall the OP saying this was a permanent setup, and I don't recall you seeing if he/she knew how to partition or even if it was possible (e.g. maybe OP has 4 primary partitions already). If you're trying to help, then help. If you just want to do a drive-by bashing of wubi, don't.

---

