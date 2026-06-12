---
title: "The file /boot/grub/stage1 not read correctly. during revertion to grub"
date: 2012-02-10
forum: General Help
---

### Post by onineko on 2012-02-10
Good day!

When I installed the current server lts on a thinkserver rd240 I didnt think much could go wrong, what with the server being ubuntu-certified and the installation running without a hitch. Then, after the reboot into the new system grub2 told  me "error: out of disk." 
I tried the rescue as told in the community-article on grub2. it didn work, any way I tried, so I said, alright then, lets go back to when I could just edit menu.lst and be done with it.

enter [https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)
I chroot into the installed system and everything is fine up to step 5) were the answer to "grub-install /dev/sda" (the system is on sda2) is this: 
The file /boot/grub/stage1 not read correctly.

well, great. I tried grub-install --recheck /dev/sda, but still the same.
The guided install made 3 partitions: sda1 was 2MB grub_bios (?), then sda2 (the entire system) and sda3 for swap.
in the meantime, as I tried more and more crazy things, I deleted sda1.

Does anyone have a clue as to what might be the cause for grub-install to not be able to read stage1? Or rather, what might lead to it being able to install? 

the /etc/fstab reads thus:
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=88494588-4487-4e7a-bea2-131d9756c272 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda3 during installation
UUID=fa401f59-f2d5-42da-a1df-d38e9605984c none swap sw 0       0


thank you in advance for any hints and help =)
silvana

---

### Post by oldfred on 2012-02-10
If you have a grub_bios partition, do you not have gpt partitioning?

And if you got gpt partitioning automatically it means the drive is over 1TB as that is what Ubuntu will default to.

There was(is) a bug in grub that it does not work from very large partitions. Generally for desktops I suggest a separate /home and a small system partition at the start of the drive of about 25GB. With a server you may need different system partitons or sizes which I do not know for sure. Then the other option may be a separate /boot of 500MB at the beginning of the drive. You need to keep the bios_grub partition if gpt.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by onineko on 2012-02-14
thanks, it was the size-bug that did it =)
now sporting a nice little boot-partition and everything works. I still reverted to the old-school grub, just like it better and don need the "improved" fuctions of the new one =)

---

