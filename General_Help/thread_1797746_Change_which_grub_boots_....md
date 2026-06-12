---
title: "Change which grub boots ..."
date: 2011-07-05
forum: General Help
---

### Post by Bucky Ball on 2011-07-05
Hi all,

I have a Toshiba Satellite Pro L510 with Windows 7, Ubuntu 10.10 and a 10.04 LTS minimal install. All booting fine with 10.10 grub at boot.

I installed Xubuntu 11.04 on another partition, all went great ... BUT ... I was in a bit of a rush and when I got back to the machine and rebooted for the first time, 11.04 had installed a grub and taken control of boot. That is fine, everything boots okay, but I really didn't want this.

10.10 is my production install (10.04 just never played nice with this machine or I'd be using that, naturally) and is stable, tweaked to perfection, and staying where it is; 10.04 and 11.04 are 'experimental' for me and likely to be replaced or tweaked into oblivion anytime. Therefore, I want 10.10 to control grub, as it was doing before, which gives me the freedom to explore the other two installs without fear of bricking the machine.

How can I now take control away from the 11.04 grub and give it back to the 10.10 install at boot? All ideas appreciated ... in the meantime I shall keep digging ... ;)

---

### Post by DawieS on 2011-07-05
If you have all those installations on 2 or more disks, you need to control the boot disk from the BIOS.

To select the correct boot partition on a specific disk, you can use **Gparted** to select the boot flag on the partition you want to boot from.

If it is required to repair your **Grub** boot-loader, the following **Howto** by forum member **talsemgeest** will point you in the right direction::smile:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Elfy on 2011-07-05
Reinstall grub - [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

Tell it the right partition when needed - the 10.10 one :)

Should work fine. IF 10.10 was ok booting grub - you could make sure to copy the original 10.10 grub.cfg file juts in case you need to refer to it.

I've used this (just to see) to good effect. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


> If you have all those installations on 2 or more disks, you need to control the boot disk from the BIOS.Why?

---

### Post by Bucky Ball on 2011-07-05
Nope, one disk in a laptop:

```
shointer@chunks:~$ sudo blkid
[sudo] password for shointer: 
/dev/sda1: LABEL="System" UUID="3E10BBBF10BB7C89" TYPE="ntfs" 
/dev/sda2: LABEL="S3A8406D004" UUID="7060EA3E60EA0B24" TYPE="ntfs" 
/dev/sda4: LABEL="HDDRECOVERY" UUID="8AD8245BD82447B1" TYPE="ntfs" 
/dev/sda5: LABEL="root" UUID="93f00b46-2cf5-4b46-83be-f708cf831675" TYPE="ext4" 
/dev/sda6: LABEL="home" UUID="0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1" TYPE="ext4" 
/dev/sda7: UUID="63d86782-bff4-41c1-924f-37d093fbe371" TYPE="swap" 
/dev/sda8: LABEL="Mini1" UUID="d015570f-cd27-4a23-8db7-3eb4d685b48d" TYPE="ext4" 
/dev/sda9: UUID="5b20be62-a948-4693-b6c9-a8b11eb2d271" TYPE="ext4" 
/dev/sda10: LABEL="Misc" UUID="6B8E2F2A62CEE191" TYPE="ntfs"
```sda2 = Win7
sda5 = 10.10 stable install;
sda6 = /home for all three Ubuntu installs;
sda8 = 10.04 LTS Xubuntu minimal install;
sda9 = 11.04 Xubuntu install;
sda10 = NTFS partition for sharing files with Win7.

sda1 and sda4 are Toshiba/Windows recovery partitions. Grub I guess is running from sda9 but was running from sda5 unless it was on the MBR and has been overwritten by the 11.04 grub on the MBR.

All OSs are booting fine from the grub that 11.04 installed, but that install may not last long as I want to keep that partition free to experiment, so how do I make it boot from the grub that exists in 10.10 as before is the question.

Both 10.10 and 11.04 have perfectly functioning grubs so don't think I need to reinstall grub, forestpiskie; I'm just booting from the wrong one ...

---

### Post by oldfred on 2011-07-05
All of the above will let you reinstall grub2's boot loader to the MBR of sda. But if you can boot into the install you want to be first on the menu, just boot into it and install grub from there. It is really only one line:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=Red]sudo grub-install /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by Bucky Ball on 2011-07-05
Thanks oldfred, but I think we're slightly missing the issue.

At boot I was going to the grub menu of 10.10. I'm not sure where that was written to. I installed 11.04 and that overwrote the existing 10.10 grub I'm thinking now. I have no issue whatever booting into any of the OSs on the laptop.

I want to change control of the grub back to 10.10, as it was originally (if possible). I suppose I need to find out where the grub(s) are at this point. Can anyone point me to the script I've seen floating around the forums on so many occasions and have never needed to use??? ... which gives an output of disks, partitions, OSs, and grub(s)? ;)

---

### Post by DawieS on 2011-07-05
> **forestpiskie said:**
> 
Why?
It is awfully sloppy to have the boot-loader MBR portion and the primary boot partition split up between 2 disks. If ever the first disk (maybe containing only data) is removed, the system will have to be booted from Live CD or USB, and the Grub boot-loader repaired.

---

### Post by Bucky Ball on 2011-07-05
Ok, I'm in my stable 10.10 install and all the grub files seem to be there; grub.cfg and /etc/default/grub in any case. So I figure I have a functional grub if I can get the machine to boot into it rather than the grub installed by 11.04 (which is also functioning but I don't want to rely on that one, as explained).

Incidentally, the boot flag is on sda3, the extended partition ...

---

### Post by Bucky Ball on 2011-07-05
> **DawieS said:**
> It is awfully sloppy to have the boot-loader MBR portion and the primary boot partition split up between 2 disks.

Are you talking disks or partitions or virtual disks? I have *one *physical hard drive in a laptop. ;)

---

### Post by Bucky Ball on 2011-07-05
Hopefully the Gparted screenshot attached will help. ;)

Yes, it's a dog's breakfast, but it's home! I was doing a good job of wrangling it until this blunder.

---

### Post by grahammechanical on 2011-07-05
This is annoying isn't it. You might find that the last installed Grub configuration file has been copied to all the Ubuntu partitions. This happen to me. This problem will correct itself in a way when there is a kernel update. Just make sure that 10.10 is the last install to have the update run. Then the new 10.10 configuration will take effect.

This is how I use to solve this problem. Then I installed Grub Customizer in my working Ubuntu and now whenever a kernel update messes up the Grub menu (a sure sign that one of the other Grub configuration files has taken over), I load up Grub Customizer and I use save and save to the MBR to put the Grub that I want to where I want it to be.

This worked well when I was testing 11.04 beta 2 and there were kernel updates every few days.

Regards.

---

### Post by Bucky Ball on 2011-07-05
I guess this answers some of my questions. I just installed Boot-repair in 10.10, where I was hoping the grub existed that I wanted to use, and when I ran it I got the attached message.

So I may as well reinstall grub from while in 10.10 so that install is running the show and be done with it ...

Thoughts before I go ahead and do that?

---

### Post by Bucky Ball on 2011-07-05
Well, I ran Boot-repair again and when it got to 'This will install grub, do you want to continue?' I hit 'yes', rebooted, and my old grub was back running from the 10.10 install. Nothing had changed (except 11.04 had been added because I'd updated grub in 10.10). Splash the same, timeout the same, all the same. 

The fix for my issue was to install Boot-repair:

[https://help.ubuntu.com/community/Boot-Repair#Using%20Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Using%20Boot-Repair)

I'm happy. Thanks for the ideas. ;)

---

### Post by oldfred on 2011-07-05
I actually run this as part of my backup so I know what partitions are where and how it is configured.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

You can add a 40_custom entry to boot to the link that Ubuntu puts into root to the newest kernal. Then you can always boot the newest kernel from grub without having to fully boot one install to update grub when you want to reboot into the other install with a new kernel.

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img

---

### Post by Bucky Ball on 2011-07-05
Thanks oldfred. bootinfoscript is the script I was talking about. Ran it and all is now as it should be; grub on MBR and looking for sda5 /boot/grub. Not sure about this, though:

> sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v) is installed in the boot sector of 
                       sda3 and looks at sector 147279352 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.That seems the only anomoly. Any ideas? Doesn't seem to be causing any problems. Machine's running great ...

---

### Post by oldfred on 2011-07-05
PBR's partition boot sectors are used by windows and lilo. I used to install old grub legacy to partitions to chain load. But it just becomes old data that will not be used once you change how you boot. The PBR is reserved for boot info and with grub2 it is not recommended to install to a partition anyway. 

I would just leave it.

---

### Post by Bucky Ball on 2011-07-06
Thanks again, oldfred. Leave it I shall. ;)

---

