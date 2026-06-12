---
title: "system won't boot, boot-repair didn't solve - help"
date: 2012-07-08
forum: General Help
---

### Post by F W Adams on 2012-07-08
Hi,

I think while trying to install a MS-DOS on a usb drive I accidentilly wrote an MBR in the wrong place. Now the system won't boot.

I tried boot-repair automatic solution, I believe it wrote back the MBR record but rather than pointing to the first parttion, sda1, my boot partition, it pointed to sda3. See the record of what was done here, at the bottom:
[http://paste.ubuntu.com/1081322/](http://paste.ubuntu.com/1081322/)

There is a working pen drive system on sdc that I'm using at the moment and also an unbootable one on sda. The files on /BOOT look fine.

I tried using boot-repair again to point to sda1 rather than sda3 but it didn't fix the problem. See here
[http://paste.ubuntu.com/1081410/](http://paste.ubuntu.com/1081410/)

The symptoms I'm getting, I suppose from the bios as it seems not to getting as far as grub.

> Missing operating System

Reboot and select proper boot device or insert bootable media in selected boot device and press a key

Need help as I'm just not sure what to try next.

Thanks

---

### Post by oldfred on 2012-07-08
I believe the missing operating system is due to the Windows (like) boot loader that boots from the partition with the boot flag. Without a boot loader in the PBR partition boot sector then it cannot boot.

You need to get grub2's boot loader installed to the MBR of sda and use /boot from sda1 and the encrypted partition as /. But it seems to be showing issues with the encryption. Not sure if it can mount the encrypted partitions to let you correctly install or not. I have not used encryption, so I do not know the details of getting grub2 installed.

It does show this not sure Boot_Repair can mount encrypted partition to correctly install:

> /boot detected. Please check the options.Did you tick the box to include that in the repair?

Edit, I found this in my notes:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)

---

### Post by ajgreeny on 2012-07-08
I have no idea whether or not the disk encryption is having any effect on your problem, but the one thing I can see is that you do not have grub installed on any disk, as far as I can make out, but syslinux instead, about which I know nothing.

I am tempted to suggest that you simply make use of a live CD/USB to restore grub to the mbr of sda, or have another try with boot-repair and this time let it install grub, if that is one of its options.  I have never used boot-repair so I really think it better for you to wait until another forum member with a bit more knowledge than me about it comes along.

---

### Post by F W Adams on 2012-07-08
I haven't tried anything yet though I'm feeling ( without my computer ) almost as if my legs have been cut off.

Just to clarify things a bit, sda1, the /boot partition, is not encypted. The error is occurring before the password for the encryption is asked for ( entered through the kb ) so obviously where the error is occurring can have nothing to do with encypted data.

The problem seem to be that it's not reaching grub, or not at least executing anything in /boot? The grub was originally installed by the alternate CD and not touched since.

ajgreeny
I know that boot-repair mentioned sys-linux but my machine is definately using grub. I don't have any partiality to boot-repair, I was just looking to try and find a solution.

There is a file /boot/grub/grub.cfg on my machine and the contents are in [http://paste.ubuntu.com/1081322/](http://paste.ubuntu.com/1081322/) as mentioned above. But it seems to be generated from within /etc which is an an encrpted area.

oldfred
Yes, it's possible in theory to get at encypted data on a broken machine if you have the password. I've never actually tried it yet. EDIT: I've actually got that to work now

---

### Post by oldfred on 2012-07-08
If Boot-repair cannot find an Ubuntu install it defaults to a Windows like (syslinux) boot loader.

With a separate /boot you have to tick the box for that but not sure if Boot-Repair can mount and see the encrypted root to install correctly as to reinstall grub you have to mount both /boot & / (root) or full chroot into system but that would also require mounting the encrypted partition.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by F W Adams on 2012-07-08
Well, I tried boot-repair again, I must have done it just as you were posting. And this time it did come up with [HTML]/boot detected. Please check the options.[/HTML] Then, almost to my horror it said it was re-installing grub. I knew this wouldn't work as it ( as you said ) needed access to /root. It certainly couldn't get it as it didn't have the password. After all, the encryption would serve no purpose if the data could be accessed without the password.

It did work, everything is fine now. Perhaps it just did something with /boot/grub/grub.cfg on it's own which it could access, In short I just don't know.
It's late now and am very tired, need to get some sleep. Thanks for help. In the morning I'll look at the links and try to see what happened and mark the thread as solved.

---

### Post by YannBuntu on 2012-07-10
Hello

There is currently no detection of encrypted partitions in Boot-Repair, that's why it thought there was no OS.
I will try to add this feature in next versions of Boot-Repair. EDIT: done.
Please follow [this]("https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory") to open your encrypted partition before using Boot-Repair.

---

### Post by F W Adams on 2012-07-10
Well, it managed to fix it in any case. I noticed all the /boot files had new date and time stamps, were they just the same files as before?

Of course with a different problem I can see that you would need access to root to correct it.

I'll mark as solved.

---------------------

Just a word of warning about unlocking encrypted systems for people not in the US. If you've using a US system keyboard ( as the ubuntu CD relaeased in the UK ) to unlock your system then you may need to allow for that when you key your password. Of course you see nothing wrong as you type.

---

