---
title: "Grub2 configuration"
date: 2011-04-03
forum: General Help
---

### Post by linux_trojan on 2011-04-03
I used the dd command to copy windows XP from one computer and load it onto an existing partition on my Ubuntu 10.4 laptop.  However, I cant get Grub to see windows as a bootable operating system.  How can I set up dual boot?

---

### Post by techunit on 2011-04-03
in linux run ```
sudo update-grub
```

---

### Post by linux_trojan on 2011-04-03
that definitely helped.  After doing update-grub, I got a black and white screen that allowed me to choose Ubuntu or XP.  I chose XP and just got a black screen, nothing.

Previous to using your recommendation, I used cfdisk to lable my windows partition as bootable.  I dont think that hurt anything right?  At first I thought that was the solution until I read your post.

---

### Post by techunit on 2011-04-03
You should be fine. I've been working something like 5 grub problems today and yours was the first that was solved quickly and painlessly.

---

### Post by drs305 on 2011-04-03
The partition must be bootable but the issue for you is probably the cloning. I don't know a lot about Windows but have read posts indicating that a cloned Windows installation can have problems. I think the bootloader looks at the partition sectors and if they disagree it won't boot.

Do a search on these forums; I've seen this issue addressed within the past week.

---

### Post by techunit on 2011-04-03
> **drs305 said:**
> The partition must be bootable but the issue for you is probably the cloning. I don't know a lot about Windows but have read posts indicating that a cloned Windows installation can have problems. I think the bootloader looks at the partition sectors and if they disagree it won't boot.

Do a search on these forums; I've seen this issue addressed within the past week.
I believe the problem was actually solved. So many Grub problems today.


Linux-Trojan can you mark this thread as solved if it is?

---

### Post by drs305 on 2011-04-03
I got the impression he now had the Windows option available in the Grub menu, but then when it was selected it booted to a black screen.
> **linux_trojan said:**
> that definitely helped.  After doing update-grub, I got a black and white screen that allowed me to choose Ubuntu or XP.  I chose XP and just got a black screen, nothing.


Guess we'll find out soon enough.

@ linux_trojan,

If this is solved, please mark it so via the 'Thread Tools' link at the top right of the first post (to avoid my confusion if for no other reason ;-) ).

---

### Post by techunit on 2011-04-03
> **drs305 said:**
> I got the impression he now had the Windows option available in the Grub menu, but then when it was selected it booted to a black screen.


Guess we'll find out soon enough.

@ linux_trojan,

If this is solved, please mark it so via the 'Thread Tools' link at the top right of the first post (to avoid my confusion if for no other reason ;-) ).
Oh I must have missed that! He marked a bootable partition as bootable again possibly making unbootable.

I don't know how he would fix it but I guess booting a live cd and opening gparted and using that to mark the WinXP partition as bootable again might work.

---

### Post by linux_trojan on 2011-04-03
Its basically solved.  I tried to install windows from CD on this pc and even though I created a NTFS partiion, the CD says it cant detect any hard drives.  I think something is wrong with the hardware or the bios, not sure.  I dont know how I am ever gonna get windows on this pc but the grub problem was fixed.

---

### Post by techunit on 2011-04-03
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

This should help for dualbooting windows and ubuntu and installing Windows after the fact.

---

### Post by oldfred on 2011-04-03
Windows has to have a NTFS primary partition with the boot flag (active partition in windows). Grub does not use boot flag to boot or to boot windows, but windows needs it to boot, install or to do repairs.

Some BIOS (Intel for one) also check for a boot flag on a primary partition and do not let you boot unless you have one. So sometimes we have to put boot flag on a primary partition just to have one.

---

