---
title: "Windows 8 Mistake"
date: 2012-10-02
forum: General Help
---

### Post by Wagzle on 2012-10-02
Ok guys, I messed up. I installed Windows 8 on an open partition of my Linux machine without reading up on it at all and now I can't see my Ubuntu partition through the new UEFI boot junk. I'm not seeing any solutions online, other than reinstalling Ubuntu 12.04 now that I have Windows up and running. 
 
The trouble is that I still have 4/5th of my hard drive in my Linux partition that the Windows boot menu doesn't see. I don't even want/need Windows on my machine, I just thought it would be nice, so I would rather wipe the Windows partition and get back to what I had before.
 
I even installed GRUB 2 for Windows hoping I would be able to get to Ubuntu through there, but even that only showed windows as an option.
 
So here's my question. To make a partition for Windows on my HD, I used a live USB to run GParted and I was wondering if there was something like that that I could do now to get rid of Windows. Is the UEFI business just on the windows partition, (and that's why it can't see my previous Ubuntu installation) so it would go away once I deleted that partition, or will I still be in trouble even if I am able to wipe it?
 
Thanks in advance for your guidance Ubuntu Community,
Wagzle

---

### Post by sandyd on 2012-10-02
Can you post the output of the boot info script please?
```

wget -O bootinfoscript.sh http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz?r=http%3A%2F%2Fbootinfoscript.sourceforge.net%2F&ts=1349153743&use_mirror=iweb
chmod +x bootinfoscript.sh
sudo ./bootinfoscript.sh partitions.txt

```
Post the contents of partitions.txt

Thanks!

---

### Post by oldfred on 2012-10-02
Do not run any repairs from this just yet. Just post link to the BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If Windows installed in UEFI mode it may have converted drive from MBR to gpt and we have to be careful that your Linux partitions are still there.

---

### Post by Wagzle on 2012-10-03
SOLVED!!! Thanks for your quick feedback guys, but it looks like all I needed to do was manually enter my linux partition into my grub menu (which I should have seen right there in the manual, silly me).. The boot process takes much longer, but I can get to everything I need to. Ah, sweet relief, I have my Ubuntu back.

Thanks,
Wagzle

---

