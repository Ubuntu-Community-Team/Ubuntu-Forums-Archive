---
title: "Chainloading Grub2 &gt; Grub2"
date: 2011-03-30
forum: General Help
---

### Post by feffer on 2011-03-30
I multi-boot between Win7 and 3 linux distros using GRUB. Before with grub-1, I used chainloading to simplify maintenance. That is I installed grub to the mbr and to 2 of the linux partitions. Then I altered the menu.list to reflect this. Then even when updating the kernel on one of my secondary linuxes, I didn't have to reboot to the main one and do an update-grub. This all worked fine and I seldom had to touch the menu.list or grub.

When Grub-2 came out, I tried the same thing and it worked -- sort of! But, when I tried to install grub-pc (2) to a non-mbr partition, it complained that this was unreliable and so on. I got around this by using the --force option. However, I've never really been comfortable with this. Is it OK to continue this or not? 

If not, is there a way to accomplish the same thing: 1) low maintenance and 2) get my preferred grub entries to the top of the list? For #2 I know about the custom grub file but unless I chainload, I must edit this for each new kernel :(

thx,
feffer

---

### Post by wilee-nilee on 2011-03-30
You don't really explain why you need to put the grub2 loader in a partition, you don't need to basically. Grub2 will read grub-legacy, ms, lilo, and other bootloaders leave it in the mbr or reload it when changed. Some users advise to not let a install overwrite the mbr and install the bootloader to the partition installed in. Personally I just let it load and reloaD my favored bootloader grub2 there.

I have W7, Maverick, Natty, and Archbang, arch is grub-legacy, I use Maverick as the controlling boot. When ever I change the partitions adding or removing a OS, where it changes the mbr I boot to maverick with super grub, and reload grub2 to the mbr with.
sudo grub-install /dev/sda

You can also reload grub2 with a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Not sure if this answers your question.

---

### Post by feffer on 2011-03-30
no that doesn't answer my question. Please read the first post carefully; I did explain why I wanted to do this, but perhaps I was not clear enough. > That is I installed grub to the mbr and to 2 of the linux partitions To elaborate, grub is installed BOTH in the mbr and the local partitions of each secondary linux system. Then in the primary linux system the menu.list is given entries to chainload the secondary ones -- in the same way that Windows is chainloaded. 

With this setup, rebooting to the primary linux is not necessary. Neither is using a liveCD. There is zero maintenance. I began doing this about 4 years ago when a distro dev explained that this was how he did it. 

After moving from grub-legacy to grub-pc, I successfully used the same method. However, as I said in the initial post, grub-pc does not like to be installed in a non-mbr partition and I have to use the --force option. My question: Is there really any reason NOT to do this? If so is there a way to get the same result (IE - control of the boot menu and NO maintenance).

regards,
feffer

---

### Post by wilee-nilee on 2011-03-30
> **feffer said:**
> no that doesn't answer my question. Please read the first post carefully; I did explain why I wanted to do this, but perhaps I was not clear enough.  To elaborate, grub is installed BOTH in the mbr and the local partitions of each secondary linux system. Then in the primary linux system the menu.list is given entries to chainload the secondary ones -- in the same way that Windows is chainloaded. 

With this setup, rebooting to the primary linux is not necessary. Neither is using a liveCD. There is zero maintenance. I began doing this about 4 years ago when a distro dev explained that this was how he did it. 

After moving from grub-legacy to grub-pc, I successfully used the same method. However, as I said in the initial post, grub-pc does not like to be installed in a non-mbr partition and I have to use the --force option. My question: Is there really any reason NOT to do this? If so is there a way to get the same result (IE - control of the boot menu and NO maintenance).

regards,
feffer

Always love a snippy answer to free advice, lol.

---

### Post by feffer on 2011-03-30
Didn't mean to be snippy, wilee-nilee, but I have a real question about this and have spent a few hours trying to nail this down. Most of the Grub howto sites go over chainloading, but only mention linux chainloading in the sense of going grub1 > grub2 (a transitional work-around). Yet I know quite a few experienced users have used the method I outlined. So I'm wondering is someone has solid info about doing this in grub2.

btw, I appreciate the voluntary effort of you and others to help linuxers with questions. I do it too and even moderate a forum. If you aren't really sure about this question, I understand. No problem. I was just hoping I might get a lead here.

Regards,
feffer

---

### Post by oldfred on 2011-03-31
I used to chainload a lot and still have different MBRs since I have 3 drives. I can chainload from grub2 to grub2 in another drive.

You have to decide on one main system to have in the MBR and always use it to boot.

For Ubuntu (not sure about other distributions) or Debian based, you will find a link in / to the most current kernel in /boot. 

You modify 40_custom with an entry like this:

Got this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Chain loading MBR can be confusing. The boot MBR is always 0. But I normally boot sdc, so sda then is hd1.

menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

after all changes"
sudo update-grub

---

### Post by feffer on 2011-03-31
Oldfred, thank you very much! This was very helpful. I was not aware of the "mbr confusion" you mentioned. It didn't affect my earlier, simpler setups, but it does affect my current one! 

I think I can correct my setup with this info. Can I assume that you and others who chainload between drives and partitions use the --force option to install grub-pc to non-mbr partitions? And that you are OK with it?

The example menuentrys were much appreciated especially the one that picks up the newest kernel. I had been trying to figure out how to do that. 

btw, I grew up in the NW Chicago suburbs.

Regards,
feffer

---

### Post by oldfred on 2011-03-31
Only when I was still primarily booting with old grub legacy did I install grub2 to a partition. It worked fine. But my understanding is anything that causes the boot files to move on the drive, will cause problems and you then have to reinstall grub to the PBR. As long as you know that it is usable.

Since  I really only have 3 versions of Ubuntu I am normally booting, I just install each grub to a different drive. For the occasional other install that uses old grub I usually try to install old grub to the PBR so I can chainload but grub2's os-prober finds it and I do not have to chainload. Since I do not use other installs a lot, I have not changed to chainload.

Someone posted this which I have not tried. Not sure if it then bypasses the install of the grub to the PBR?

boot another grub2
menuentry "sda5" {
        insmod ext2
        set root=(hd0,5)
        multiboot /boot/grub/core.img
}

---

### Post by feffer on 2011-04-02
@oldfred: Just had a chance to try some of these custom entries.
This worked well - as mentioned, gets the latest kernel.> Got this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
set root=(hd0,13)
linux /vmlinuz root=/dev/sda13 ro quiet splash
initrd /initrd.img
}
Haven't tried the "multi-booting" entry yet. After looking carefully at my setup, I may not bother. Probably best not to over complicate things.

thx,
feffer

---

### Post by oldfred on 2011-04-02
Glad it worked out.:)

---

