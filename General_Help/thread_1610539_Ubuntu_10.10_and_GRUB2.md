---
title: "Ubuntu 10.10 and GRUB2"
date: 2010-10-31
forum: General Help
---

### Post by cat2005 on 2010-10-31
Hi,

Currently I have a dual boot setup:

a) 1st SATA hdd - Ubuntu 9.04 (32 bit)
b) 2nd SATA hdd - Windows 7 Home (64 bit)
c) Boot Loader is original GRUB
d) 4.00 GB ram
e) Intel Core i3 540 @ 3.07 GHz

This setup easily lets me select either OS upon boot.  Both OS work well.

However, I setup this system well over a year ago.  Consequently, I don't recall all the specific setup details but I do specifically remember selecting the original GRUB over GRUB2.  At that time, GRUB2 had trouble with dual setups such as mine.

Unfortunately, it was so long ago that I don't remember exactly "what" GRUB2 failed to do.  I just remember that the original GRUB was the way to go.  I think the problem had to do with the Windows side of the setup.

_My question:  _
*Has GRUB2 matured enough to easily let me select either OS upon boot as easily as I do now?*

I can provide more information upon request but unfortunately I setup my computer so rarely, and last did so long ago, so I don't remember all my setup details.

Thank you!

---

### Post by 73ckn797 on 2010-10-31
Grub2 has worked fine on all of my computers (3).
Go here for info:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2)

---

### Post by drs305 on 2010-10-31
You may have been trying Grub 1.97-beta at the time.

In the past year there have been some improvements to Grub 2. Many of the changes have gone toward allowing G2 to work better with more formats and OS's.  

For the normal user, I would say that G2 has not had significant gains in that time. What *has* changed is that the knowledge base has expanded tremendously and many more people now understand how G2 works and how to fix it when it breaks. And there is a lot more 'unofficial' documentation as well (check my signature line for some of it).

On most standard installs of Ubuntu and Windows, Grub2 works very well. And when it doesn't, we can now help!

---

### Post by oldfred on 2010-11-01
One of the remaining issues is windows 7 software that corrupts grub2. Not grub2 issue but Dell & HP's applications. But if you have 2 drives you have no issue as you keep the win7 boot loader on the windows drive and grub2 on the the Ubuntu drive. You set the Ubuntu drive to boot from BIOS and choose either Ubuntu or windows. If you ever have major issues you still can in BIOS switch and direct boot windows from the win drive. I have had XP on one drive and Ubuntu on my other drives since soon after grub2 came out and not had any issues that will some help from the forum did not solve.:)

drs305 has good instructions on totally uninstalling grub & grub2 and cleanly installing grub2.
If you can boot your Ubuntu, you do not have to chroot from a liveCD, but just run the commands to uninstall & reinstall.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by 73ckn797 on 2010-11-01
> **oldfred said:**
> 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

I will bookmark these links to pass around to others as the need arises. Thanks.

---

### Post by cat2005 on 2010-11-09
> **oldfred said:**
> One of the remaining issues is windows 7 software that corrupts grub2. Not grub2 issue but Dell & HP's applications. But if you have 2 drives you have no issue as you keep the win7 boot loader on the windows drive and grub2 on the the Ubuntu drive. You set the Ubuntu drive to boot from BIOS and choose either Ubuntu or windows. If you ever have major issues you still can in BIOS switch and direct boot windows from the win drive. I have had XP on one drive and Ubuntu on my other drives since soon after grub2 came out and not had any issues that will some help from the forum did not solve.:)

drs305 has good instructions on totally uninstalling grub & grub2 and cleanly installing grub2.
If you can boot your Ubuntu, you do not have to chroot from a liveCD, but just run the commands to uninstall & reinstall.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)



What you described sounds much like what I have now.  I have my 1st SATA as Ubuntu and that is where GRUB legacy is found.  I have my 2nd SATA as Windows 7 and that is (of course) where the Windows boot loader is found. 

Upon power up, my screen shows the GRUB menu, allowing me to select which OS (hdd) I wish to use.

Is GRUB 2 developed enough to now handle that with the same smoothness as GRUB legacy?

Thank you!

---

### Post by oldfred on 2010-11-10
From day 1 I have had no issues with grub2 other than learning curve as it is different. I used chainbooting & grub2 does not like to be installed to a partition. But grub2 finds other systems and directly boots them so chainbooting is not required.

I have seen an occasional user with Ubuntu on drive 0 and windows on drive1 have issues. The other way around where windows is the first drive almost never has issues. There maybe some  issue about drive order and passing boot (grub chainboots windows as windows has some of its boot in the windows partition boot sector).

---

### Post by shashank.sa.sa on 2010-11-10
In my system,40_custom file cant be edited and no file can be added to grub.d folder. Accidentally i have copied file from /boot/grub/grub.cfg to /etc/grub.d/40_custom. I want to edit 40_custom. Plz suggest me a solution

---

### Post by drs305 on 2010-11-10
> **shashank.sa.sa said:**
> In my system,40_custom file cant be edited and no file can be added to grub.d folder. Accidentally i have copied file from /boot/grub/grub.cfg to /etc/grub.d/40_custom. I want to edit 40_custom. Plz suggest me a solution

shashank.sa.sa,

Welcome to the Ubuntu forums.

Since this is a system file, you must open it as 'root'. Use this command. When entered, it will ask for a password. Enter your user password.

```
gksu gedit /etc/grub.d/40_custom
```

Here is an explanation of 'root':
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by efflandt on 2010-11-10
shashank.sa.sa, to add or edit any system files, you have to precede your commands with **sudo**, to do that as root.  Just be careful what you do when using sudo (especially with any wildcards like *).

I don't know why grub2 goes into a tantrum and stomps its feet when you try to put it on a partition (you have to --force it).  That has always worked fine for me with standard Windows mbr, putting grub on a primary Linux partition, and marking that partition as the boot partition.  I had to do that after something Dell in Win7 stepped on grub2 in the mbr.  Fortunately I had a bootable USB hard drive, and grub2 on that could boot Ubuntu on my main hard drive, making fixing it easy.  After I installed grub2 on sda4, I did **bootrec /FixMbr** from a Win7 boot DVD, then used gparted to mark sda4 as boot.

Maybe part of the dire warning is because you should NOT put grub on a Windows system partition, you have to know to mark that partition with grub as the boot partition, and I do not know if that works if grub is put on an extended or logical partition.  I know that lilo used to work on an extended partition, but not on a logical partition.  So maybe lilo's mbr could boot grub on an extended partition itself if a Windows mbr does not.  I still wouldn't try putting grub on a logical partition unless you are adventurous and know how to change that if it does not work.

---

### Post by cat2005 on 2010-11-18
> **efflandt said:**
> shashank.sa.sa, to add or edit any system files, you have to precede your commands with **sudo**, to do that as root.  Just be careful what you do when using sudo (especially with any wildcards like *).

I don't know why grub2 goes into a tantrum and stomps its feet when you try to put it on a partition (you have to --force it). 


What if you are placing GRUB 2 on your / partion in a "linux only" hdd?  In other words, what if I place GRUB 2 on my linux hdd and windows on a separate hdd.

Is that what you are describing?  Or, are you describing 1 hdd with both linux and windows on it?

---

### Post by oldfred on 2010-11-19
I believe efflandt is discussing installing grub2 to a partition. I used to do that with old grub legacy to chainboot. Grub2 is slightly larger and to fix it has to use something called blocklists which it considers less reliable. I gather is is hard coded addresses of the grub files so if they get moved on the hard drive it breaks the boot. As long as you know that you can reinstall grub after files get moved.

If you have two drives you have two MBRs and can easily install two boot loaders without having to install any to the PBR or partition boot sector.

---

### Post by cat2005 on 2010-11-19
> **oldfred said:**
> I believe efflandt is discussing installing grub2 to a partition. I used to do that with old grub legacy to chainboot. Grub2 is slightly larger and to fix it has to use something called blocklists which it considers less reliable. I gather is is hard coded addresses of the grub files so if they get moved on the hard drive it breaks the boot. As long as you know that you can reinstall grub after files get moved.

If you have two drives you have two MBRs and can easily install two boot loaders without having to install any to the PBR or partition boot sector.


That is what I thought.  Thank you for confirming.

---

