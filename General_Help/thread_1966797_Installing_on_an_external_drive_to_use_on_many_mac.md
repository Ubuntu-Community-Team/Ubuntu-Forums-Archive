---
title: "Installing on an external drive to use on many machines failed"
date: 2012-04-27
forum: General Help
---

### Post by Basilios on 2012-04-27
Some time ago I installed Ubuntu 11.10 on an external USB hard drive, so that I could have only one setup that I could use on many computers, because sometimes I have to travel around and cannot always use one machine.

I installed Grub2 on the MBR of this hard drive, and disabled automatic recognition of other OSes, so I would have Linux if this hard drive was plugged in and booted from, and whatever local version Windows otherwise.

Well, it works well on a couple of desktop computers I have at home, but when I went out yesterday I found out it doesn't work with my laptop, an Asus EEE 901. I got a grub error message saying "Out of disk" and a recovery prompt.

When I went home I tried on my wife's laptop, and got a different error: "File not found". I double checked on my two machines but it runs OK, and in fact I am writing from that Linux environment right now.

I am attaching three files in the hopes they help. The file grub.txt is /etc/default/grub and the file grub.cfg.txt is /boot/grub/grub.cfg - I had to add the .txt extension to be able to upload them. The file RESULTS.txt is the output of bootinfoscript, an utility to analyze a machine's boot configuration available here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Any suggestions? I was hoping to bring this hard drive with me on holiday in a few days so I could use whatever computer I find to work.

---

### Post by oldfred on 2012-04-27
It is easier for us to review your results.txt if you just copy & paste into the message and then wrap code tags around it. You can easier add the code tags by highlighting like you would copy it and then clicking on the # in the edit panel above your message. Your grub.cfgs are inside the results.txt, so you do not need to post those also.

Some older computers only boot from the first 137GB. Those either need a separate /boot within the first 137GB or you can just have the entire / partition inside the 137GB and make the rest of the drive /home or data partition(s). I normally suggest 10 to 25GB for / if you are storing all your data in other partitions.

Some newer computers seem to act the same way if BIOS settings are set to legacy IDE or sometimes other settings. 

So I might try smaller root partition and separte /home or data partition and see it that works or not.

Your old install in sda is booting with grub legacy, but you have some entries in fstab that refer to vfat partitions in sdb that do not exist. Are you just using grub legacy to boot Windows? If so why not reinstall the Windows boot loader?

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

If you want a data partition that works with Windows it would need to be NTFS.

---

### Post by Basilios on 2012-04-27
Never had a problem with any of the computers involved about the size of the partitions before.

The reason why strange things appear with the results is that it was run after plugging in the troublesome hard drive in a computer that I got some time ago with multiple, messed up OS installations and never got around reformatting. It was the only computer I could spare at the time of writing where the troublesome installation worked. The legacy grub, the Windows install, and so on, are all going away, but I am not interested in using the external drive we're talking about only with this computer.

I am not interested in booting Windows, or in using any local partition for data; I only want to set up Ubuntu on an external hard drive, and configure Grub to boot that, and that only, and be able to use that drive on any (or a reasonably large number of) computers I might have access to on holiday.

---

### Post by Basilios on 2012-04-27
> **poonjabi said:**
> you should buy a laptop and then put your files you need on the external hdd
**No.**

---

### Post by oldfred on 2012-04-27
Smaller / (root) both is more efficient as drive does not have to try to load files from entire drive but a smaller partition and likely to work in more systems.

---

### Post by Herman on 2012-04-28
> Some older computers only boot from the first 137GB. Those either need a  separate /boot within the first 137GB or you can just have the entire /  partition inside the 137GB and make the rest of the drive /home or data  partition(s). I normally suggest 10 to 25GB for / if you are storing  all your data in other partitions.I think you're on the right track. One time I helped somebody else who had an ASUS EeePC and they installed Ubuntu in an external HDD because the EeePC's SSD had a problem. It wouldn't boot from the USB because of a BIOS HDD size limit and we got it working by creating a separate /boot in a USB flash memory stick and leaving the / (root) in the large sized external HDD.
A separate /boot essentially fences the kernel in to a partition close to the start of the drive which the BIOS can read, then once the kernel boots it has the drivers to access the remainder of the drive and find /, whatever size it may be.

The external USB HDD will very likely boot and run okay in most other computers normal modern BIOS capabilities. Booting Ubuntu in a USB is normally not a problem in most PCs but testing in some other PCs would be advisable before embarking on a trip.

---

