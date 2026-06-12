---
title: "Reinstall GRUB"
date: 2012-08-14
forum: General Help
---

### Post by sienile on 2012-08-14
I'm running low on disk space and I was going to cannibalize my Ubuntu testing install to make more space for my current Ubuntu install. Only problem is, my testing install has GRUB on it. If I remove it without first reinstalling GRUB, I will be unable to boot into Ubuntu.

To further complicate things, I have Windows 7 installed on the same physical disk as the primary partition. So the way it currently works is it loads Windows BCD which then loads GRUB on my testing install (since it was installed first).

What's the procedure for reinstalling GRUB to a different partition? Or can I install it along-side Windows BCD?

---

### Post by krytorii on 2012-08-14
There'll be a more precise, proper way of doing tihs but a boot-repair livecd has been an invaluable tool for me.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ubume2 on 2012-08-14
If I am understanding you correctly, you have a Windows install (up to 3 partitions), one Ubuntu "testing" partition, and one regular Ubuntu partition, and possibly a swap partition.

I think you can install grub on your regular Ubuntu install FROM the testing install. 

Edit: Before trying this read post 4 and 5. You can do it this way, but why make it hard. To delete the unwanted partition and expand the desired distro is another issue. 

From terminal
```
$ sudo fdisk -l
```

to determine the partition of the regular Ubuntu install.

Once you determine the partition:

```
$sudo mount /dev/sdax /mnt     
      $sudo mount --bind /dev /mnt/dev
      $sudo mount --bind /proc /mnt/proc
      $sudo mount --bind /sys  /mnt/sys
      $sudo chroot /mnt

```

Now you are in the desired partition [hopefully]

```
#grub-install /dev/sda
      #update-grub
```

After you update grub you should see your testing, regular Ubuntu, and Windows in your grub.

then exit chroot
```
#exit
```

then unmount
```
$sudo umount /mnt/sys
      $sudo umount /mnt/proc
      $sudo umount /mnt/dev
      $sudo umount /mnt    
```

Hopefully, you now have grub install on the Ubuntu you want to expand. I think you will need to boot from a livecd or liveusb to delete the testing partition, and expand the regular Ubuntu partition with unallocated space. (Note: Only expand the partition to the right).

You may also do all of the above from a livecd or liveusb.

Good luck

---

### Post by cottfcfan on 2012-08-14
the easiest way I have found, Thanks to another forum member, is just to boot into the distro you want to control Grub. The Ubuntu one in your case, and then run:
```
sudo dpkg-reconfigure grub-pc
```
and reboot.
Your Windows partition should then be accessible from the Grub screen.

---

### Post by ubume2 on 2012-08-14
> **cottfcfan said:**
> the easiest way I have found, Thanks to another forum member, is just to boot into the distro you want to control Grub. The Ubuntu one in your case......

Yes, if you can boot into the ubuntu distro, it's much easier.

I do it this way:

Make sure /etc/grub.d/30_os-prober is executable. To do that:
$sudo chmod +x /etc/grub.d/30_os-prober
$sudo grub-install /dev/sda
$sudo update-grub

And hopefully after you update you will now see the 3 distros and be able to boot into either Windows, Ubuntu testing, or Ubuntu.  Installing grub on the Ubuntu partition should not effect The Windows partition(s)

---

### Post by sienile on 2012-08-14
I still want to retain the Windows BCD so that I can perform repair tasks to Windows when necessary. Will these methods do that, or overwrite it?

To give everyone a better idea of my setup, here's the partition list for my physical disk:

[LIST=1]
[*]Windows 7 - NTFS
[*]Ubuntu "testing install" - ext4
[*]SWAP partition
[*]Ubuntu install - ext4
[/LIST]

Currently GRUB2 is on partition #2 and configured to launch partition #4 by default.

---

### Post by cottfcfan on 2012-08-14
When you run the command it takes you through several windows.
The last window asks if you want to install Grub on sda or the partition Ubuntu is on.
 I would think the 1st option would wipe out the Windows BCD, but the option to install Grub onto its own partition should be safe.
 I would wait for someone else's opinion on this though.

---

### Post by sienile on 2012-08-15
Currently there is a GRUB install on both Ubuntu partitions, but the one that actually gets loaded is the one on the partition that I want to get rid of (#2 in list above).

The way my PC currently boots is to go into Windows BCD, which then loads GRUB. The program I used to configure it this way (EasyBCD, a Windows tool) does not have an option to pick the partition that it loads GRUB from. Is there a way to change the BCD target partition? I'm fine with having to do this from Windows if it's not possible in Ubuntu or just much easier.

---

### Post by ubume2 on 2012-08-16
Edit:  you are apparently booting Ubuntu roundabout.  Since I know nothing about "BCD" my solution above might complicate things.  Sorry I didn't read your posts more carefully. Good luck

[deleted]

---

### Post by YannBuntu on 2012-08-16
> **krytorii said:**
> There'll be a more precise, proper way of doing tihs but a boot-repair livecd has been an invaluable tool for me.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

+1
Boot-Repair will reinstall GRUB.
Alternatively, you can indicate us your [Boot-Info URL]("https://help.ubuntu.com/community/Boot-Info") so that we have more information about your system.

---

### Post by sienile on 2012-08-23
After I cleared off some space to get the Ubuntu Secure Remix ISO, I finally got around to running Boot-Repair... or trying to. It stuck on the "Scanning systems." dialog, both using the LiveCD and when I installed it on my main install. I haven't tried running it from my testing install yet, which is where GRUB is installed.

From the screenshots I've seen it seems like it would be a great tool to have, if I could ever get it to work. Anyone know how to get it going?

---

### Post by sienile on 2012-08-23
Boot-Repair finally decided to work after a few reboots and GRUB reinstalls.

Here's the Boot-Info:
[http://paste.ubuntu.com/1163769/]("http://paste.ubuntu.com/1163769/")

---

### Post by YannBuntu on 2012-08-24
You have 2 Ubuntu: one on sdd2, the other on sdd6.

You are not using BCD any more (but that's not a problem, you can do what you want with GRUB).

**- If sdd6 is the Ubuntu you want to keep,** your boot is ok now. You can delete sdd2.
**- OR if the Ubuntu you want to keep is sdd2,** boot into this sdd2 Ubuntu, then run Boot-Repair's Recommended repair from the sdd2 session. Reboot the PC and check that sdd2 is the default OS on the top of the GRUB menu. If ok, you can delete sdd6.

---

