---
title: "Can I remove Ubuntu from dual install and keep GRUB?"
date: 2010-08-02
forum: General Help
---

### Post by polygnotus on 2010-08-02
Greetings. I am trying to set up a dual boot system - one for internet (Ubuntu), and one for workstation (XP Pro). These are two partitions on one drive, plus the little ram partition installed by Ubuntu.

This would have been a great setup. I love Ubuntu and I would have been able to hide and protect my workstation install. But, alas, no drivers for my audio card.

So now I am forced to use XP for my internet system as well. So I am wondering, can I just reformat the Ubuntu partition and install XP onto that - and keep the GRUB boot manager as is?

I need to be able to hide my workstation partition from the internet one. GRUB can apparently make this happen, or so I've read. I am pretty low skilled when it comes to command line functions. So I need the easiest way to switch out my Ubunto partition with an XP one that can't see my Workstation partition by, I guess, using GRUB as a boot manager.

---

### Post by Darkness Des on 2010-08-02
Boot into a LiveCD, go into the installer and erase your Ubuntu Partition, expand your XP Partition, and exit before installing.

---

### Post by polygnotus on 2010-08-03
> **Darkness Des said:**
> Boot into a LiveCD, go into the installer and erase your Ubuntu Partition, expand your XP Partition, and exit before installing.

Thanks for the response. But I'm sorry to say I have no idea what this means. I mean I get the part about using an Ubuntu install CD as a livecd and erasing the partition. I just have no idea how, otherwise, you response has any thing to do with what I wrote.\

I need to be able to hide my workstation partition from the internet  one. GRUB can apparently make this happen, or so I've read. I am pretty  low skilled when it comes to command line functions. So I need the  easiest way to switch out my Ubunto partition with an XP one that can't  see my Workstation partition by, I guess, using GRUB as a boot manager.

---

### Post by Darkness Des on 2010-08-03
That's ok. May I ask how you installed Ubuntu?

---

### Post by SunnyRabbiera on 2010-08-03
what is your audio card?
Perhaps we can make suggestions on making it work
If its a creative, you are screwed though, heck creative barely works in windows.
If it is a creative do yourself a favor and buy a realtek audio card, good for both os's

---

### Post by polygnotus on 2010-08-03
> **Darkness Des said:**
> That's ok. May I ask how you installed Ubuntu?

Certainly, and thanks again for the response.

I installed XP Pro. Then I installed Ubuntu 10.04 using an Ubuntu boot disk, which then allowed me to create two new partitions and overwrite the MBR with GRUB etc. I installed Ubuntu into one of the new partitions. 

Basically, just followed the directions.

---

### Post by polygnotus on 2010-08-03
> **SunnyRabbiera said:**
> what is your audio card?
Perhaps we can make suggestions on making it work
If its a creative, you are screwed though, heck creative barely works in windows.
If it is a creative do yourself a favor and buy a realtek audio card, good for both os's

Thanks SunnyRabbiera. I already spent 3 days trying to get 3rd party drivers to work on my MAudio card. I have no more time to invest. At least not now. Maybe later.

cheers.

---

### Post by SunnyRabbiera on 2010-08-03
well if you can give us your specs and your audio card, you can find that all out in XP.
We can teach you how if you want us to.
Having a sound card issue is unusual but it does happen, you may want to look into other linuxes as pulse might be a reason why your audio is not working.
Pulse is a sound server that ubuntu uses and on some caudio cards it does not work well.
we will help you remove it, dont just give up yet as we may be able to help.

---

### Post by polygnotus on 2010-08-03
> **SunnyRabbiera said:**
> well if you can give us your specs and your audio card, you can find that all out in XP.
We can teach you how if you want us to.
Having a sound card issue is unusual but it does happen, you may want to look into other linuxes as pulse might be a reason why your audio is not working.
Pulse is a sound server that ubuntu uses and on some caudio cards it does not work well.
we will help you remove it, dont just give up yet as we may be able to help.

Thanks Sunny, but alas I have to give up. I am on a time budget and my experimental phase is exhausted. Like I said though, I would like to pursue this later. I am over windows and ready to make the switch, at least as far as basic internet functions go. But I just don't have time to mess with it now. 

I desperately need to get my questions answered so I can proceed to setting up this system.

---

### Post by Darkness Des on 2010-08-03
Alright. When you boot into your disk, choose to install Ubuntu. When you get to the step that asks if you want a certain partition scheme, choose Manual. Delete all of your Ubuntu partitions (2, as it appears). Make your Windows partition expand to fill up all the disk space (or however much you want, your choice) and then exit the installer after that finishes. This won't touch the MBR.

---

### Post by polygnotus on 2010-08-03
> **Darkness Des said:**
> Alright. When you boot into your disk, choose to install Ubuntu. When you get to the step that asks if you want a certain partition scheme, choose Manual. Delete all of your Ubuntu partitions (2, as it appears). Make your Windows partition expand to fill up all the disk space (or however much you want, your choice) and then exit the installer after that finishes. This won't touch the MBR.

Thanks DD. One last question. If I then proceed to install a second XP on a new partition, will Grub recognize this new XP?

Thanks again. I really appreciate the help.

cheers

---

### Post by Darkness Des on 2010-08-05
No problem, I enjoy helping. Knowing the XP install process I went through about 7 times (lots of hard drive replacements) it'll rewrite the MBR. However, you can install GRUB to the MBR afterwards from your disk. I'm not quite sure how to add the new OS without having Linux installed somewhere. You could try the good ol' Grub4DOS approach, which runs off of the Windows bootloader. You can make it the default entry and give it a timeout of 1 second (just incase it breaks and you can't boot from it and you need to select regular XP), a link for it is below.

[http://sourceforge.net/projects/grub4dos/](http://sourceforge.net/projects/grub4dos/)

---

### Post by mcduck on 2010-08-05
Actually you'll need at least a small boot partition for Grub to work, as only part of it is installed on the MBR and the rest (including all the configuration files) is located in /boot.

Well, Grub *can* be installed on a FAT partitions as well, perhaps even on NTFS, so you could at least in theory install it into your windows partition. I'm not sure how well that would work in reality, though.

---

### Post by oldfred on 2010-08-05
It would be best to create a small grub (only) partition. Also when you install windows it will normally combine boots into one, so all your windows boot files will be in the active partition (boot flag).

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition")
old grub partition
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition")
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_")

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

I did experiment with installing the windows 7 repair CD to USB and then installing grub to allow booting other repair ISOs also. Worked but you have to be willing to add your own boot entries as there is no osprober.

---

