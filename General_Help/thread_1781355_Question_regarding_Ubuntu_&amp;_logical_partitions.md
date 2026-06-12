---
title: "Question regarding Ubuntu &amp; logical partitions"
date: 2011-06-13
forum: General Help
---

### Post by rich52x on 2011-06-13
Okay, so when I got my new laptop, it came with all 4 primary partitions in use, and I wanted to dual boot, so I was advised to delete a partition (HP TOOLS) and create an extended one in which to install ubuntu. That worked and I type here from ubuntu. But. I got the BSOD when starting Windows today out of nowhere, and in the HP recovery manager it gives me the option to restore my laptop to 'Out of the box condition'
Will this restore the HP TOOLS partition I deleted to make way for Ubuntu, if it does, you can imagine the mess. But I do need that Windows install

Btw: Windows 7 Home Premium 64bit
Ubuntu 11.04 64bit
Laptop model- HP G56-116A

---

### Post by mikewhatever on 2011-06-13
It might, depending on how the OEM had implemented the restore procedure. On the other hand, if the restore program needs the HP TOOLS partition, the process might fail. In short, many options, all of them open.

---

### Post by doas777 on 2011-06-13
well, the recovery option (out-of-box) will likely repartition your system, replacing the extended with a primary again. sometimes you get more options over your partitioning when rerunning the oem setup stuff though, so it might work out. just be sure to backup your content first, as your windows install will be reset to default as well. 

as for the bsod, I would probably boot up in safemode (if available), and try to determine the piece of software that is misbehaving and remove it. that it causes a bsod may imply that it is related to a driver. what is the text of the bsod, and what do you get if you google it?

---

### Post by rich52x on 2011-06-13
Thanks for replying

I was under the impression that HP TOOLS contained tools such as access to BIOS through windows and such. But the separate RECOVERY partition is still intact.

@doas777 i shall check now, but the blue screen disappears after a few seconds, ill take a pic

---

### Post by rich52x on 2011-06-14
Backed up data onto memory stick, used hp recovery from system repair options, left ubuntu intact after it finished but it wouldnt load grub
Being lazy I just put in my 11.04 disc, and selected 'Erase 11.04 and reinstall'. Not the most conventional solution, but never mind.

Thanks for the replies guys, solved

---

### Post by doas777 on 2011-06-14
> **rich52x said:**
> Backed up data onto memory stick, used hp recovery from system repair options, left ubuntu intact after it finished but it wouldnt load grub
Being lazy I just put in my 11.04 disc, and selected 'Erase 11.04 and reinstall'. Not the most conventional solution, but never mind.

Thanks for the replies guys, solved

glad you are happy with your fix. next time though, if you reinstall/recover windows and you can't get to grub, try this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

the issue is that your MBR was overwritten by the recovery, and so it no longer points to grub.

---

