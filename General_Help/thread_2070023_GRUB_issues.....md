---
title: "GRUB issues...."
date: 2012-10-11
forum: General Help
---

### Post by arandomstring on 2012-10-11
Hey, everyone. I currently have a dual-boot setup with Windows 7 and Ubuntu 12.04

Whenever I start my computer after booting windows previously I'm presented with a different GRUB than usual. I recently downloaded and installed linux kernel 3.6.0 and made some changes to GRUB using GRUB customizer. So I have been doing some tweaking with those files. This leads me to believe that for some reason Windows is causing GRUb to load a previous grub.cfg (This one lists ubuntu with the 3.2 kernel only). When I power down after encountering this issue (I can't boot into Ubuntu from this old GRUB [gives me some error like ELF Magic: press any button to continue]) and restart the correct GRUB appears. 

So overall I feel I somehow have GRUB installed in two places and would like to remove the old version. I don't know if this is even possible without a fresh install though. I have already tried boot-repair with custom options selected.

Thanks for your help!

---

### Post by oldfred on 2012-10-11
From Boot_Repair run BootInfo and post link to report it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by arandomstring on 2012-10-11
Alright, my bootinfo can be found [here.]("http://ubuntuforums.org/paste.ubuntu.com/1274141/")

Thanks!
[]("http://ubuntuforums.org/paste.ubuntu.com/1274141/")

---

### Post by oldfred on 2012-10-11
Correct pastebin - you have some extra characters. 
[http://paste.ubuntu.com/1274141/](http://paste.ubuntu.com/1274141/)

You only have one grub.cfg or the menu. You have two MBRs and it looks like both are the same version of grub booting the same sda5 partition. (script may say same drive, but it is not).

Grub menu shows new 3.6 kernel & older 3.2 kernels. 

It looks like you have one of the new Intel Smart Response like these:

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

But they installed to the SSD and broke the RAID. I do not understand how RAID with an SSD really speeds thing up much.
You may need to install the RAID drivers in Ubuntu but the Boot-Repair may have done that already.
sudo apt-get install mdadm

Are you hibernating in Windows? Or does the Intel SRT auto hibernate like the new Windows 8?

---

### Post by arandomstring on 2012-10-12
I don't hibernate but I see the hibernation file when mounting the windows partition so I'm assuming that SRT is auto hibernating it. Is there any way to fix this? I'll try installing the RAID drivers and get back to you.

---

### Post by YannBuntu on 2012-10-12
> **oldfred said:**
> You may need to install the RAID drivers in Ubuntu but the Boot-Repair may have done that already.

It hasn't, because AFAIK there is no clue in blkid (or else) suggesting the presence of RAID.
FYI, if it had enabled RAID, we would have seen it in the log between 
```
ADDITIONAL INFORMATION :
```and

```
=================== os-prober:
```

@madkristoff: please try Oldfred's suggestion anyway

---

### Post by arandomstring on 2012-10-12
Alright, I did sudo apt-get install mdadm, is there anything I need to configure to use it?

---

### Post by oldfred on 2012-10-12
I do not see any evidence of RAID either, but I thought that was how Intel configured it. Maybe it also is a setting in BIOS?

Normally with RAID you cannot use gparted, but have to use the RAID tools to edit partitions. I do not know RAID enough to know more.

---

### Post by arandomstring on 2012-10-12
Shouldn't deleting the extra MBR fix this issue? Is there any way to do that?

Because I tried a fresh install earlier today and the problem persists...

EDIT: The bootinfo says I have GRUB installed on sdb as well as sda. I should just remove the GRUB installation from that hard drive (an SSD) and this should be cleared up. Anyone know how I could go about that?

---

### Post by oldfred on 2012-10-12
It should not matter. If you do not use a boot loader in a MBR it does not make any difference that it is there. Only the one you set in BIOS needs to be up to date.

But I prefer to install different operating systems in each drive and have that operating system's boot loader in the MBR of the same drive. With your configuration I am not sure if that does work. The links I posted were users that broke the RAID, and just installed Ubuntu in the SSD. Last link was a user with Ubuntu on the same drive but reimplemented the Intel RST system.

---

### Post by arandomstring on 2012-10-12
Yeah, I had a previous issue and worked through it using your links. Anyway, would uploading images of the different GRUBs I'm being presented help?

---

### Post by oldfred on 2012-10-12
Glad to look at them just to see what issue may be.

---

### Post by oldfred on 2012-10-12
Another user just posted this:

[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.


---

### Post by arandomstring on 2012-10-13
For me to try that fix, would I need to reinstall Ubuntu *again*? Or could I just disable it, recreate the GRUB.cfg and then re-enable it? Anyway,  [here]("http://imgur.com/a/n2yEO") are the images of the 2 different GRUBs that are being loaded in different situations. I took those pictures with my phone so they aren't the greatest haha.

Also, here is my new bootinfo file:[ Here.]("http://paste.ubuntu.com/1276119/")

---

### Post by oldfred on 2012-10-13
Script is not picking up the new grub2 2.00. Your first entry is from grub2 1.99 which is probably from the MBR of sda. Is system somehow switching which MBR to boot from? But I do not understand why you get different menus?

But you have only one install, so I do not see how you can have two versions of grub at the same time.

Post this:

#show versions
grub-install -v
uname -a

It may be just easier to make sure you have the same version of grub2 in both MBR or you may need to purge & reinstall grub.

Your first pastebin was 12.04, but now you show 12.10? Have you decided to test the version being released in a few days? Until it is released you are a tester.

---

### Post by arandomstring on 2012-10-13
> **oldfred said:**
> Script is not picking up the new grub2 2.00. Your first entry is from  grub2 1.99 which is probably from the MBR of sda. Is system somehow  switching which MBR to boot from? But I do not understand why you get  different menus?

Yeah, I think that is what is happening as well. I'll try your commands out.

Also, I realize I'm running 12.10, I did a fresh install to try to correct the problem and thought I'd use the soon to be released 12.10.


Here is the output of the commands:
```
:~$ grub-install -v
grub-install (GRUB) 2.00-7ubuntu10
:~$ uname -a
Linux Joshua 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```Should I use boot repair to purge and reinstall GRUB?
If I do use it, should I select to install it on the SSD as well when I'm given [this screen?]("http://imgur.com/LKRME")


FINAL EDIT: You're going to hate me for wasting your time haha, but I solved the issue. What I did was used boot-repair to purge and reinstall GRUB on sda (Main Harddrive) then booted into windows. Once I was in Windows I disabled Intel Rapid Storage Technology thing and then rebooted. The problem was gone so I went to Ubuntu, ran ```
 sudo update-grub 
``` and rebooted again into Windows to re-enable the Intel RST. The problem was gone after this. Thanks for your help Old Fred and speedy replies!!!

---

### Post by oldfred on 2012-10-13
Glad you got it sorted out.

Something about the Intel RST. But I do not fully understand how it works. :)

---

