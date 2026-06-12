---
title: "Serious filesystem corruption 9.10 64bit"
date: 2010-04-28
forum: General Help
---

### Post by JohnDewey on 2010-04-28
Hi all,

I have installed Ubuntu 9.10 on a brand-new i7 920 with Asus P6T Deluxe v2 motherboard and 6 GB RAM, ATI 5870 GPU. The harddisk has a device model number ST31000528AS according to GSmartControl (a Barracuda 7200.12 SATA 1TB?) with Ext4 on the Ubuntu partition. It is set up to dual boot Windows 7 and Ubuntu. Kernel 2.6.31.20.

Everything worked in the past 3 months, but I've noticed occasional filesystem corruption after reboot. Now this seems to have aggravated (kernel update?) and I've realized that when I leave the machine on overnight in order to make a large Jungledisk backup, the backup will fail and the filesystem invariably gets corrupted and switches to read-only. Many inodes and blocks need to be fixed when this occurs.

This is, of course, really troubling me, as I use this machine for everything and first and foremost for regular work. (I log in via remote desktop.)

What I have done so far:

- switched on ACHI mode: HD freaked out, had to switch it off immediately

- checked the HD with GSmartControl: no problem detected

- made a backup of the most important files to an external harddisk

- tried out linux-image 2.6.34 RC1 via manual install: mouse cursor didn't show up and so I didn't use it again

Does anyone know how to troubleshoot this? Are there any known issues to which this problem might be related?

I've been using Ubuntu 9.04 and 8.04 on other machines with Ext3 for years without troubles, so I wonder whether I should use Ext3 instead?

---

### Post by klemes on 2010-04-28
I have no clues as to what it might be causing this file-system data corruption but my assumption is that it was present from day one but not all that noticeable perhaps since this is a relatively fresh installation.
I faintly remember one similar case reported in an other forum years before in which the only solution that was found was to repeat the installation with a newly downloaded ISO after a md5sum was performed to it and confirmed that it was intact.Just mentioning it though unless someone has a better understanding for the basis of your problem.

---

### Post by El Zoido on 2010-04-28
Even while SMART doesn't seem to report any problems, can you be sure it's not caused by a faulty HDD?

Any problems on the windows partition?

---

### Post by JohnDewey on 2010-04-28
Not a single problem on the Windows partition in the past 3 months. I'll buy another HD and install it on the weekend, but somehow I doubt the HD is the problem.

In the meanwhile I'd be glad about advice on what else I could try or ideas how to locate the source of the problem. Having to work with a system that you can't really trust is kind of frustrating, especially since it took me a long time to configure the fresh install to my needs. :(

---

### Post by dino99 on 2010-04-28
i guess you have some logs with the backups crashes, look at them and maybe run a testdisk.
If you have enough free space, recreate an other partition.

---

### Post by john newbuntu on 2010-04-28
Just to add to what dino99 mentioned, have a look at the logs in /var/log/ such as syslog, kern.log, dmesg etc for any errors.
Also, I take it that when inodes/blocks need to be fixed, you are using e2fsck (or fsck) after booting from a liveCD.  Does your partitioning scheme look ok (sudo fdisk -l)?  Sorry if I am just asking for the basics here.

---

### Post by JohnDewey on 2010-04-29
Thank you all for your help so far! Just for the record, here is what I did:

[LIST]
[*]Booted from LiveCD instead of using fsck on reboot.
[*]This time, the gsmartcontrol applet said that there where about 1000 bad sectors after 44 hours running time. I suppose this indicates that the HD is soon to fail entirely, is that right? 
[*] Ran e2fsck -c -c /dev/sda5 where sda5 is the ext4 root partition
[/LIST]

So you were right, the drive seems to have been crap from the start and it just wasn't noticeable because not much space was used. I'll buy a replacement disk this evening, which hurts because a >=1TB disk is hard to get and almost twice as expensive in shops than if you order it where I live (Portugal). 

Perhaps I'll put 10.04 on it. If not, is there a way to clone the faulty HD to the new one without cloning disk errors too? Or should I rather reinstall everything from scratch? 

One more question: If I buy one drive now and another one later, will it be possible to setup some mirror RAID for higher data integrity without destroying the contents of the older drive?

---

### Post by StuartN on 2010-04-29
> **JohnDewey said:**
> So you were right, the drive seems to have been crap from the start

There is a bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981) with similar symptoms, and some related bugs with suspend / resume failure, filesystem remounted readonly etc, all introduced in Ubuntu 9.10 and all unresolved.

I have two identical Dell laptops that occasionally remount the filesystem readonly and fsck on reboot. They work absolutely perfectly with Ubuntu 8.10 and earlier, but not 9.10 or 10.04.

Perhaps yours is a hardware failure, but it would be interesting to see if a replacement hard disk produces the same symptoms.

---

### Post by john newbuntu on 2010-04-29
Just to confirm the health of the disk, run it by Seagate disk check utility (seatools?) before you throw away the drive.

---

### Post by JohnDewey on 2010-04-29
> **StuartN said:**
> There is a bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981) with similar symptoms, and some related bugs with suspend / resume failure, filesystem remounted readonly etc, all introduced in Ubuntu 9.10 and all unresolved.

I've seen this thread and the symptoms on my machine are indeed exactly the same. What is a bit troubling is that Windows 7 has not complained about the windows partition at all so far, even though many more files have been created and deleted.

 I'll definitely report back in this thread in case similar problems occur with the new disk. 

Meanwhile, what about ext3? Would there be a disadvantage if I put ext3 instead of ext4 on the new root partition? Is ext3 "safer"?

---

### Post by dino99 on 2010-04-29
some thinkings:

- about your hdd: no trouble with windows but ubuntu, so we can exclude hardware problem, only partition issue

- so , install partedmagic ([http://partedmagic.com/](http://partedmagic.com/) ) on cd or usbstick and boot with it to examine the ubuntu partition(s) ( stupid question but you have checked that any partition is not full indeed)

- after that, if you have not found where the problem is, few decisions can be taken:
1) find a corrupt package with install -f or/and dpkg --configure -a, then reinstall the deb package ( i suppose you have not exotic packages from third party or ppa other than the trusted one)

2) reformat then reinstall from scratch a nice new Lucid  :P

---

### Post by StuartN on 2010-04-29
> **JohnDewey said:**
> Meanwhile, what about ext3? Would there be a disadvantage if I put ext3 instead of ext4 on the new root partition? Is ext3 "safer"?

I have tried a clean install with ext3 and with ext4. I currently have the Lucid release candidate with ext4 / and ext3 /home, with the same problems - until someone points to a definitive cause, there will not be a definitive solution. I will try the suggested upstream kernel when I have installed 10.04 final, but I have not seen any reason why it would resolve these symptoms.

My only certain resolution is to return to Ubuntu 8.10, but there are several packages I want to use on the ;aptop that are several versions behind in 8.10 and a pain dependency-wise.

---

