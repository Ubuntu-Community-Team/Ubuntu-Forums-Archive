---
title: "GRUB2 error: no such device: grub rescue UUID doesn't exist"
date: 2011-11-01
forum: General Help
---

### Post by dannyboy79 on 2011-11-01
I have a very similar situation and instead of making my own I figured I resurect this thread, hope that's ok. 

Back story first, I have 1 internal hard drive (40GB) which has Ubuntu 10.04 which was booting from grub legacy. sda1 is /, sda2 is swap, and sda3 is /home. I have 2 external USB drives. 200GB is /dev/sdb1 and is FAT32 and is only for storage (is never removed). 1000GB is /dev/sdc, it was originally 1 large ext4 partition. I recently used gparted (from within lucid if that matters) to shrink it and make a 19GB primary partition formatted as ext4 and a 1GB primary partition for swap. I installed Ubuntu Studio 11.04 onto the 19GB partition which is sdc2. When it came time to install grub2, I left it blank thinking it didn't matter because I would just add an entry to my legacy grub menu.lst to boot into Studio. I tried desperately to manually add an entry into my menu.lst to no avail. SO I decided to upgrade my legacy grub to grub2 from within my 10.04 install. It said it was successful. So I boot the computer and grub legacy menu is there, at the top it has the chainload to grub2 (or whatever it is) and I choose that and sure enough it takes me to grub2 menu. The 10.04 ubuntu grub2 entry works great BUT the Ubuntu Studio 11.04 entry doesn't work. It returns 3 errors as follows; no such device, no such partition, and you need to load the kernel first. So since that didn't work I did not run the final command for converting to grub2 from grub legacy (upgrade-from-grub-legacy). So then I tried installing grub2 in the MBR of /dev/sdc and it still won't boot. It's like due to it being a USB drive maybe the usb modules are being loaded or something like that? I am at a loss of how to get Ubuntu Studio 11.04 booted? My ideal situation would be to have grub2 installed in the MBR of sda because that hard drive will never be removed whereas it's possible that I disconnect the sdc drive since it's a USB drive,

Here are the results from running the Boot Script Info bash script.
[http://pastebin.com/512tajWK](http://pastebin.com/512tajWK)

Any help would be appreciated.

---

### Post by oldos2er on 2011-11-01
Post moved to its own thread.

---

### Post by drs305 on 2011-11-01
I would probably take this in two steps - installing Grub 2 to sdc and then after it boots correctly installing it to sda. Grub 2 is currently not installed on either MBR. On the plus side, Grub 2 has identified both Ubuntu installations, if you can get them to boot.

Boot the 11.04 LiveCD. Mount / and then install Grub 2 to the sdc MBR. Just check Nautilus or use the terminal to confirm the drive is still labeled 'sdc' before you begin. Don't use the partition number in the second command.

```
sudo mount /dev/sdc2 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
sudo umount /dev/sdc2

```

Make sure the BIOS is set to boot sdc first, then boot. You should see menu entries for both installations. Try booting each one- try 10.04 first. Then reboot back to 11.04 and if it boots properly, run:
```
sudo grub-install /dev/sda
```

---

### Post by dannyboy79 on 2011-11-01
In my research I have found that grub2 possibly has issues booting kernels that are located on an ext4 partitions which is evident by the error I am getting when grub2 tries to boot the ubuntu studio kernel located in the /boot/ folder on /dev/sdc2. I also think there may be an issue with booting because of a BIOS limitation? /dev/sdc2 is located at the way end of the 1TB drive, does that matter?

I would like to add that I am very confused why it says that I have grub legacy installed on /dev/sdc. If I tell my bios to open a boot device menu and I choose to boot the /dev/sdc USB Hard Drive Grub2 pops up. Doesn't really matter at this point.

Steps I am in the process of making
1. Delete partitions /dev/sdc2 and /dev/sdc3
2. Shrink /dev/sdc1 from 931.51 GB down to 892.45 GB (to allow a larger space for Ubuntu Studio)
3. Move /dev/sdc1 such that it leaves unallocated space in the beginning of the drive
4. Create an ext3 partition about 37 GB in size at the start of /dev/sdc disk
5. Create a /swap partition about 2 GB in size between the 37 GB partition and the 892.45 GB partition
6. Not sure, will I have to reorder the partitions or will Gparted do that on it's own? Meaning it would now be /dev/sdc1 (ext3 37 GB) /dev/sdc2 (swap 2 GB) /dev/sdc3 (ext4 892.45 GB)
7. Install Ubuntu Studio 11.04 onto /dev/sdc1 and install Grub2 during install onto /dev/sdc (MBR)
8. Finish the installation of Grub2 on /dev/sda and pray that it can boot my Lucid Lynx install as well as the Ubuntu Studio 11.04 on /dev/sdc1


Thank you for your suggestions thus far. I will keep you updated as it's already been around 15 hours to move /dev/sdc1 further down the disk and GParted says it has another 12 hours to go. LOL

---

### Post by drs305 on 2011-11-02
> **dannyboy79 said:**
> In my research I have found that grub2 possibly has issues booting kernels that are located on an ext4 partitions which is evident by the error I am getting when grub2 tries to boot the ubuntu studio kernel located in the /boot/ folder on /dev/sdc2. I also think there may be an issue with booting because of a BIOS limitation? /dev/sdc2 is located at the way end of the 1TB drive, does that matter?
Grub 2 doesn't have a problem with ext4, but the BIOS (and subsequently Grub 2) can have a problem seeing files deep on a disk.

The way to check is to go to the Grub prompt (press 'c' at the Grub menu) and then use the "ls" command to determine if Grub can 'see the files (example: ls (hd2,2)/boot/ ). If it can't located them, it could be a BIOS limitation.

> 
I would like to add that I am very confused why it says that I have grub legacy installed on /dev/sdc. If I tell my bios to open a boot device menu and I choose to boot the /dev/sdc USB Hard Drive Grub2 pops up. Doesn't really matter at this point.

Don't know, although your sdc2 is missing the /boot/grub/core.img file, which would be one reason for Grub 2 not booting.

> 
Thank you for your suggestions thus far. I will keep you updated as it's already been around 15 hours to move /dev/sdc1 further down the disk and GParted says it has another 12 hours to go. LOL
A clean install would be a lot quicker.  ;-)

One minor thing -  your sdc2 fstab lists two swap partitions. You only need one, and you should check all the UUID's after you complete your current operations to ensure the correct swap UUID is still valid.

---

### Post by dannyboy79 on 2011-11-03
> **drs305 said:**
> Grub 2 doesn't have a problem with ext4, but the BIOS (and subsequently Grub 2) can have a problem seeing files deep on a disk.

The way to check is to go to the Grub prompt (press 'c' at the Grub menu) and then use the "ls" command to determine if Grub can 'see the files (example: ls (hd2,2)/boot/ ). If it can't located them, it could be a BIOS limitation. Don't know, although your sdc2 is missing the /boot/grub/core.img file, which would be one reason for Grub 2 not booting.
Yeah, I noticed that ext4 boot support was added to grub2 version 1.97. Maybe the usb module wasn't being loaded soon enough. This WAS the entry that os prober added:

menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdc2)" {
        insmod ext2
        set root='(hd2,2)'
        search --no-floppy --fs-uuid --set 52585a55-3fba-4a05-a5a6-ea4346c76460
        linux /boot/vmlinuz-2.6.38-8-generic root=UUID=52585a55-3fba-4a05-a5a6-ea4346c76460 ro quiet splash vt.handoff=7
        initrd /boot/initrd.img-2.6.38-8-generic

BUT for whatever reason I was getting 3 errors, no such device, no such partition, and you need to load the kernel first. Who knows and at this point it doesn't matter anymore.

> **drs305 said:**
> A clean install would be a lot quicker.  ;-)Well, like I said, I wanted to create the partition that would hold Ubuntu Studio 11.04 at the beginning of the disk, and that 800 whatever GB partition had tons of data on it, so I needed to do the move so that I could access space at the front of the 1TB drive. You'll see later why it doesn't matter anymore also. LOL

> **drs305 said:**
> One minor thing -  your sdc2 fstab lists two swap partitions. You only need one, and you should check all the UUID's after you complete your current operations to ensure the correct swap UUID is still valid.If you notice, that one of those swap it WAS showing is the swap space for my Lucid Lynx install, it's /dev/sda2. I am not sure why the Ubuntu Studio 11.04 install picked that up and put it in its fstab file. 

Ok that was all previous to today. Well, the power went out this morning so obviously the GParted that was moving sdc1 further down the disk got totally hosed and I lost everything in that partition, which thank god it was only a backup copy of a 500gb hdd I have in my main server.

This is where I am at thus far. I erased everything off of /dev/sdc and partitioned it leaving around 40 GB of unallocated space in the beginning and created an approx 888 GB partition to redo the backup of the 500 GB hdd I have on my server. Here is the new boot_info_script results:
[http://pastebin.com/gH0LGeFt]("http://pastebin.com/gH0LGeFt")

I used the Ubuntu Studio 11.04 installer to create an approx 40gb partition for / and 2gb for a swap space. At the end of the installer I told it to install grub2 onto the MBR of /dev/sdc. I am able to bring up the boot device menu that the BIOS has, chose the /dev/sdc USB disk, it boots into grub2. YIPPIE, I chose the Ubuntu Studio 11.04 kernel entry and it boots into it BUT it boots to a blank black screen. If I hit ctrl-alt-F7 it shows it's stuck at "*Starting AppArmor Profiles " BUT if I go to tty1, I can log in with my credentials. Most likely a graphics driver issue or something. I am not worried about that, I can work thru that.

So the last thing to do is see if I can complete the grub2 install on /dev/sda2 and hope that it boots the 11.04 install on /dev/sdc2. The thing that I never realized is that partition numbers (sdc1, sdc2, and sdc3) are controlled by WHEN they were partitioned and not where they are on the disc. So my 11.04 install is still on /dev/sdc2 BUT at least now it is ext3 and is at the beginning of the hard drive platter.

---

### Post by drs305 on 2011-11-03
> **dannyboy79 said:**
> 
So the last thing to do is see if I can complete the grub2 install on /dev/[COLOR="DarkRed"]sda2[/COLOR] and hope that it boots the 11.04 install on /dev/sdc2. 

I got a bit lost here. Did you mean [COLOR="DarkRed"]sda[/COLOR]? sda2 isn't your Ubuntu partition and it would also mean forcing the Grub install onto a partition. 

If you want to change the MBR and you can boot into 10.04 (sda1) and run the "sudo upgrade-from-grub-legacy" command. If that doesn't work you can also just purge Grub/Grub2 and reinstall Grub 2. 

> 
The thing that I never realized is that partition numbers (sdc1, sdc2, and sdc3) are controlled by WHEN they were partitioned and not where they are on the disc. So my 11.04 install is still on /dev/sdc2 BUT at least now it is ext3 and is at the beginning of the hard drive platter.
You can reorder the partitions if you wish with the fdisk command. Of course you would have to make sure your fstab contains only references to UUIDs and not device names like sdc1, sdc2, etc.

If you need help in running either the Grub2 upgrade on sda or the fdisk commands to reorder the sdc partitions (if you want to do this) just let me know.

Finally, if you don't get the video issue resolved on your own - is it a black screen with a blinking cursor, or is it a completely black with no flashing cursor?

---

### Post by dannyboy79 on 2011-11-03
> **drs305 said:**
> I got a bit lost here. Did you mean [COLOR="DarkRed"]sda[/COLOR]? sda2 isn't your Ubuntu partition and it would also mean forcing the Grub install onto a partition. OOPS, yes, I meant /dev/sda

> **drs305 said:**
> If you want to change the MBR and you can boot into 10.04 (sda1) and run the "sudo upgrade-from-grub-legacy" command. If that doesn't work you can also just purge Grub/Grub2 and reinstall Grub 2. Ok, I did the second option and Grub 2 appears to be installed on /dev/sda and no more legacy grub (I see the menu.lst is still there though, I think I read I could just delete it if I wanted). Here's the new boot_info_script:
[http://pastebin.com/CxsHhgZD]("http://pastebin.com/CxsHhgZD")

> **drs305 said:**
> You can reorder the partitions if you wish with the fdisk command. Of course you would have to make sure your fstab contains only references to UUIDs and not device names like sdc1, sdc2, etc. If you need help in running either the Grub2 upgrade on sda or the fdisk commands to reorder the sdc partitions (if you want to do this) just let me know. I will possibly do that in the future but first I need to get this darn 11.04 install to boot to a darn GUI.

> **drs305 said:**
> Finally, if you don't get the video issue resolved on your own - is it a black screen with a blinking cursor, or is it a completely black with no flashing cursor?
Ok, very strange. If I use the BIOS boot device selection menu and chose the USB HDD it sits there a while and then my computer actually restarts. WOW, huh??? Whats up with that? If I just let the computer's BIOS boot to sda I get to grub2 menu, and choose the 11.04 kernel I can get a blank black screen (no blinking cursor). I went to tty1 and login via textual interface. I did sudo apt-get update and then sudo apt-get install nvidia-current and it installed a whole mess of things. I then issued sudo nvidia-xconfig and it said it wrote the X config file to /etc/X11/XF86Config. I restart the computer and I notice that it says "Starting load fallback graphics driver         [FAIL]", not sure why that is but I also notice within dmesg its showing the following:
```
NVRM: The NVIDIA GeForce4 MX 420 GPU installed in this system is
[   12.002580] NVRM:  supported through the NVIDIA 96.43.xx Legacy drivers. Please
[   12.002582] NVRM:  visit http://www.nvidia.com/object/unix.html for more
[   12.002583] NVRM:  information.  The 270.41.06 NVIDIA driver will ignore
[   12.002584] NVRM:  this GPU.  Continuing probe...
[   12.002872] NVRM: No NVIDIA graphics adapter found!


```
I need to get it to use the old nvidia driver 96.43 legacy driver.

So I guess I do need help, any more info you need let me know. I truly appreciate this, this is why I love the Ubuntu community so much. I have been inactive really for a long time (on Ubuntu forums) as I was content with my Lucid install BUT now I want to mess around with Audio/Music creation for background music to put behind my youtube gameplay videos so I thought I'd test out Studio 11.04 with a Realtime or Preemptive kernel (using LMMS)  BUT I just can't get this booted.

---

### Post by drs305 on 2011-11-03
> **dannyboy79 said:**
> 
Ok, very strange. If I use the BIOS boot device selection menu and chose the USB HDD it sits there a while and then my computer actually restarts. WOW, huh??? Whats up with that? If I just let the computer's BIOS boot to sda I get to grub2 menu, and choose the 11.04 kernel I can get a blank black screen (no blinking cursor).
Which Ubuntu kernel is at the top of the list in the Grub menu? If it's your older sda installation it's possible the delay means the BIOS isn't able to boot the USB and is defaulting to the next option (sda).

As far as the video issue, you could try to purge the nvidia packages and then reinstall them if you can boot to the command line. Make sure you have an Internet connection (first command before purging the packages):
```
sudo apt-get update
sudo apt-get purge nvidia*
sudo apt-get install nvidia-96* nvidia-settings
```

---

### Post by dannyboy79 on 2011-11-04
> **drs305 said:**
> Which Ubuntu kernel is at the top of the list in the Grub menu? If it's your older sda installation it's possible the delay means the BIOS isn't able to boot the USB and is defaulting to the next option (sda).

As far as the video issue, you could try to purge the nvidia packages and then reinstall them if you can boot to the command line. Make sure you have an Internet connection (first command before purging the packages):
```
sudo apt-get update
sudo apt-get purge nvidia*
sudo apt-get install nvidia-96* nvidia-settings
```
my grub2 is working great from my main internal HDD (/dev/sda) so all is well there. I could care less about grub2 on /dev/sdc and actually if I knew how to remove it I would. I noticed when I installed a kernel when I was booted within my ubuntu studio 11.04 install, I thought toward the end of installing the kernel it showed it updated grub, sadly it must have updated the grub2 on /dev/sdc cause it wasnt there when i rebooted.

It turns out for whatever reason ubuntustudio-desktop wasn't even installed. LOL  WHen i installed it from tty1 it installed like 800+ packages. No idea why the iso named: ubuntustudio-11.04-alternate-amd64.iso downloaded from an official ubuntu site was a total FAIL. 

Anyway, all is well now. Thanks for all your help!!

---

