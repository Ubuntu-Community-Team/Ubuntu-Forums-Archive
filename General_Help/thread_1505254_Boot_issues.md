---
title: "Boot issues"
date: 2010-06-08
forum: General Help
---

### Post by oceano10000 on 2010-06-08
I have an old pentium 4 dell computer that I would use ubuntu on and hadn't used it in a while as my sister took my monitor. Now that I got it back i tried to boot into ubuntu, and the computer loads up to grub, and as soon as i try to boot into ubuntu it restarts. It does this reboot cycle no matter what I select. I tried booting from live cd's several of them. And resetting the bios, and nothing works. It even goes through a boot cycle when trying to boot from a live cd. Any ideas as to what may have caused this? It was running fine last time I ran it, which was around 4 months ago. Help fix? It was 9.04 by the way.

---

### Post by _khAttAm_ on 2010-06-09
Check your RAM with memtest... and see if any errors come up.

---

### Post by oceano10000 on 2010-06-09
Checked and no errors.

---

### Post by Peter09 on 2010-06-09
It could be a hardware problem, especially if it does the same with the live CD. Check the fan on the CPU, if it is not working you may be getting a overheating problem as soon as the CPU starts working hard.
 
Aslo if you have a separate graphics card and your mother board also can provide graphics, then remove the graphics card and try again.

---

### Post by oceano10000 on 2010-06-09
I'm thinking it is a hardware problem. I checked the fan, and it works. It isn't overheating. But what I do notice is it turns off as soon as the HD starts up. Its not the graphics card thing because its integrated and I haven't changed the setup at all. I removed everything and replugged them just in case something messed up in the time being. But I can't figure it out.

---

### Post by _khAttAm_ on 2010-06-10
Try booting into it with a CD-ROM or USB Drive and see if it works.. If it doesn't boot, plug out your HDD and try again.. and post the results...

---

### Post by Peter09 on 2010-06-10
I have noticed that my fan will turn off or slow down once boot starts, I think its when the BIOS or O/S gains control of the fan, so it may not be the problem. 
 
I have seen hardware faults on graphics cards do exactly this. As soon as the O/S attempts to talk to (The faulty bit of kit) a bus error (or similar occurs) this can be catastrophic and results in a reboot. 
 
Initially (as already suggested) remove on bit of H/W at a time and see if things get better (or remove all unnecessary H/W and see if it works, then add it back a bit at a time).

---

### Post by dino99 on 2010-06-10
> **oceano10000 said:**
> I have an old pentium 4 dell computer that I would use ubuntu on and hadn't used it in a while as my sister took my monitor. Now that I got it back i tried to boot into ubuntu, and the computer loads up to grub, and as soon as i try to boot into ubuntu it restarts. It does this reboot cycle no matter what I select. I tried booting from live cd's several of them. And resetting the bios, and nothing works. It even goes through a boot cycle when trying to boot from a live cd. Any ideas as to what may have caused this? It was running fine last time I ran it, which was around 4 months ago. Help fix? It was 9.04 by the way.

thats let me think that grub dont find the good path to boot, so nothing to do with hardware issues, but with uuid.

So, boot a cd and open a terminal and run either:

blkid

ls -l /dev/disk/by-uuid

take note of the output, then reboot on hdd and check the uuid inside grub, you might see some differnces with the real uuid given by the previous command, find the one to boot on, then when you have successed you need to update the grub menu with the good uuid:

sudo grub-mkconfig
sudo update-grub

---

### Post by Peter09 on 2010-06-10
Hi Dino99,
perhaps we need to confirm something.
 
Does the OP get this with a liveCD, I thought he did, but may be you are right and its only when booting the HD.
 
If he gets the same fault from the live CD then Grub isn't the problem.
 
Can the OP confirm the situation here?

---

### Post by oceano10000 on 2010-06-11
Sorry guys have been out of town! 
It doesn't boot live cd either. It goes up to the 'try ubuntu without making changes...' and when you click it, it reboots. 
Completely unplugged hard drive and replugged it. Still not working.

---

### Post by wkulecz on 2010-06-11
Try hitting F6 before running "try Ubuntu" and set the noacpi option.  (not to be confused with noapic, much more severe and probably worth retiring the MB if this is really needed) 

Something changed between 8.04 and 10.04 that makes one of my motherboards need this.   Problem was with noacpi the CD booted fine but I had no SATA drives :(

These were IDE drives using a SATA adaptor so I could rearrange things to install, and then modied /etc/default/grub to add acpi=oldboot which let the system boot and find SATA drives.

---

### Post by oceano10000 on 2010-06-11
Well at the moment im doing another memory test, but what I don't understand is how it broke just sitting here. I just used it before I gave the monitor to my sis and it was running fine, never had problems. I'm assuming this is like that time we had a lightning storm and my router got fried, even though it was through a surge protector. I mean maybe that could have done something, there have been some bad lightning storms. Or I guess something just went out on its own? Its definitely a hardware problem in my opinion i just can't figure it out. But I'll check that in a bit. Thanks.

---

### Post by bobnutfield on 2010-06-11
It may not be your issue, but I had exactly the same symptoms a year or so ago.  It turned out to be a failing power supply.  It would turn on, runt the POST, and as soon as the hard drive kicked in, it would reboot.  A new power supply solved it.

---

### Post by oceano10000 on 2010-06-11
I was actually thinking of that because i've had that problem as well, but it runs through all the memory checks etc, maybe I do need a power supply...

---

### Post by oceano10000 on 2010-06-11
Yeah did the no acpi thing and it still rebooted...
Starting to think its the powersupply.

---

