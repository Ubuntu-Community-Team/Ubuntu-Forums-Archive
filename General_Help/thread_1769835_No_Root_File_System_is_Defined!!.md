---
title: "No Root File System is Defined!!"
date: 2011-05-28
forum: General Help
---

### Post by loybanks on 2011-05-28
I'm a bit bamboozled with installing 11.04. Windows Vista is main OS on this machine. It has it's own physical drive.

This is installing Ubuntu 11.04 to a separate physical drive of 40Gb. The drive is partitioned as follows...sdc1 at 41mb, then sdc2 I want to set as the swap file at 12Gb and the final partition is sdc5 at 27Gb, which I want to use for the OS file system which would be ext2, I believe. Would ext2 be correct file system? Is this making sense so far?

Now when I click on Forward to setup with the above specifics I'm getting the message "No Root File System is Defined". So this is where I'm totally lost. I don't see anything that specifically allows me to set up what it's asking for.

So I need some help here. All suggestions are appreciated. many thanks.

Loy Banks
[email]basecorner@gmail.com[/email]

---

### Post by wgarcia on 2011-05-28
As first comments: 

12 GB for Swap seems excessive, how much RAM do you have?

The first 41MB partition, what is it for?

Usually the swap partition is put as the last partition, but this does not matter for the installation, it can be anywhere.

As for the "root system", one of the options of the partitioner (I believe you are choosing to partition manually) should be to set the root system (" / "), but I don't remember exactly now how this is offered in the installer.

---

### Post by jocko on 2011-05-28
> **loybanks said:**
> sdc1 at 41mb
What for? That's a tiny partition.

> **loybanks said:**
> then sdc2 I want to set as the swap file at 12Gb
That's a lot of swap. Unless you have a laptop with 12 Gb ram and need to be able to use suspend to disk that's not going to be necessary. How much swap you need depends very much on how much RAM you have and what you do with your computer.

> **loybanks said:**
> and the final partition is sdc5 at 27Gb, which I want to use for the OS file system which would be ext2, I believe. Would ext2 be correct file system? Is this making sense so far?The size should be more than enough, but ext4 should be safer.
> **loybanks said:**
> Now when I click on Forward to setup with the above specifics I'm getting the message "No Root File System is Defined". So this is where I'm totally lost. I don't see anything that specifically allows me to set up what it's asking for.
When you set up the partitions, you have to specify their mount points. The root file system should have the mount point "/" (without the quotes).

---

### Post by loybanks on 2011-05-28
Thanks for the replies, however I'm still having issues.

I can reformat or change to one 40Gb drive. Then let's say partition to 20Gb as the Primary Partition for Ubuntu.

But when I try that I'm still getting the message about no root file system. I've tried, without success to setup first as /boot, then as /home, but both without success.

I'm getting with the other message to "please correct this from the partitioning menu". But this isn't accomplishing anything for me.

Someone else mentioned I should use Ext4, which I can do!.

Can someone perhaps provide me with a step by step for this problem? Right now I'm going around in circles by friends. At 71 years old circles make me dizzy! :)

Thanks so much for your help.

---

### Post by prodigy_ on 2011-05-28
> **loybanks said:**
> But when I try that I'm still getting the message about no root file system. I've tried, without success to setup first as /boot, then as **/home**, but both without success.
You don't need either. (Storing /home on a separate partition or disk is generally a good idea but it's not necessary for the OS to work.) What you absolutely need though is a partition for which you specify slash (**/** symbol) as the mount point. This is the root file system.

More info here: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by loybanks on 2011-05-28
> **prodigy_ said:**
> You don't need either. (Storing /home on a separate partition or disk is generally a good idea but it's not necessary for the OS to work.) What you absolutely need though is a partition for which you specify slash (**/** symbol) as the mount point. This is the root file system.

More info here: [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)


Thanks again. In the meantime I did get the OS installed on the separate physical drive. And yes I did figure finally the / root would be at this symbol.

But now my problem is how do I access the Ubuntu OS? This was installed on a separate drive on a Windows 7 OS Desktop machine. 

I have the Ubuntu installed along side Windows Vista on a desktop machine in  another part of the house. 

I just thought maybe the system would give me the choice of booting to either system, same as it does with the other system along side windows. But, this one just boots into Windows. Nothing there on boot up to access the new Ubuntu Drive.

So I'm still needing more help help. Again my thanks.

---

### Post by 3rdalbum on 2011-05-28
If Ubuntu is installed to the external hard disk, then you probably need to tell the computer to look at the external hard disk BEFORE looking at the internal hard disk when trying to find an operating system to boot up.

I assume you're already familiar with your computer's BIOS setup or boot order screen, because you've booted the Ubuntu CD. Set up the computer to look at the external hard disk FIRST and then it should find the Ubuntu bootloader that will give you the menu to choose between Windows and Ubuntu.

---

### Post by loybanks on 2011-05-29
> **3rdalbum said:**
> If Ubuntu is installed to the external hard disk, then you probably need to tell the computer to look at the external hard disk BEFORE looking at the internal hard disk when trying to find an operating system to boot up.

I assume you're already familiar with your computer's BIOS setup or boot order screen, because you've booted the Ubuntu CD. Set up the computer to look at the external hard disk FIRST and then it should find the Ubuntu bootloader that will give you the menu to choose between Windows and Ubuntu.

Thanks for the help, but I'm still having problems...and why didn't I think of the BIOS? Old age I suppose. 

By the way the physical HD is an Internal, not External. This machine has Sata Drives as follows on Motherboard..1 Position) CDRom Drive: 2 Position) WD Internal: 3 Position) WD Internal and 4 Position is a 40Gb Seagate for the Linux Partition at 20Gb)

Anyhow, the original boot priority, before my changes, was 1) CDROM 2) Removable 3) HD and 4) Disabled.

So now I've momentarily changed Boot Priority to 1,2 and 3 positions are all HD and Last 4 Boot is the CDRom Drive. I don't see anyplace in the Bios where I can specify to a particular HD!

However, even with all the HD's in those first positions I'm still just getting Windows Boot manager showing Windows 7 only. Nothing about Ubuntu Linux.

So I'm still needing help here my friends. Thanks to all.

---

### Post by wildmanne39 on 2011-05-29
> **loybanks said:**
> Thanks for the help, but I'm still having problems...and why didn't I think of the BIOS? Old age I suppose. 

By the way the physical HD is an Internal, not External. This machine has Sata Drives as follows on Motherboard..1 Position) CDRom Drive: 2 Position) WD Internal: 3 Position) WD Internal and 4 Position is a 40Gb Seagate for the Linux Partition at 20Gb)

Anyhow, the original boot priority, before my changes, was 1) CDROM 2) Removable 3) HD and 4) Disabled.

So now I've momentarily changed Boot Priority to 1,2 and 3 positions are all HD and Last 4 Boot is the CDRom Drive. I don't see anyplace in the Bios where I can specify to a particular HD!

However, even with all the HD's in those first positions I'm still just getting Windows Boot manager showing Windows 7 only. Nothing about Ubuntu Linux.

So I'm still needing help here my friends. Thanks to all.
Hi, this is a guide just for installing ubuntu on a different drive then windows. [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by loybanks on 2011-05-29
> **wildmanne39 said:**
> Hi, this is a guide just for installing ubuntu on a different drive then windows. [http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")


Thanks again. I will get on to reading all this information.

---

### Post by wildmanne39 on 2011-05-29
> **loybanks said:**
> Thanks again. I will get on to reading all this information.
Your welcome have fun and learn something.

---

### Post by oldfred on 2011-05-29
To see what is installed where and if grub2's boot loader is correctly installed in the MBR of the 40GB drive:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

