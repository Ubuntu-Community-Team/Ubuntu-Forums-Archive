---
title: "Lost GRUB When A Dual-Boot Partition Deleted"
date: 2011-05-30
forum: General Help
---

### Post by Chriske on 2011-05-30
Hi,

I'm having a  problem involving GRUB going missing.

I have Ubuntu as my main distro, but sometimes I might install another (Mint, Puppy, etc) alongside for research purposes.

When I install those second distros they install a new (active) GRUB.

When I want to get rid of them and delete the partition (using Gparted from the live CD) I of course lose GRUB, can't boot and usually end up reinstalling Ubuntu just to get it back.

What should I be doing to ensure that the Ubuntu GRUB is actually there after I finish deleting that partition? Reinstall it I guess, but the most efficient way?

This is what I have now, Ubuntu on sda5, Mint on sda7:
[FONT=Courier New]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           8        1313    10485760    7  HPFS/NTFS
/dev/sda2            1313       38914   302027777    5  Extended
/dev/sda5            1313       32296   248869421   83  Linux
/dev/sda6           38388       38914     4227072   82  Linux swap / Solaris
/dev/sda7           32296       38143    46966784   83  Linux
/dev/sda8           38143       38387     1961984   82  Linux swap / Solaris[/FONT]


Many thanks.

---

### Post by hal8000 on 2011-05-30
Whenever you add another distribution, always choose custom partioning, this gives you full control.

There is always an option not to install a bootloader, but often it is hidden or not obvious. Sometimes its unticking a box or you could choose
to install grub on a floppy /dev/fd0. If the device does not exist an error pops up and you can continue.

If the OS does install grub (or grub2) then it should pick up your other distributions, and you should not have to delete any partitions.

You can use the same /swap partion for all multi boot systems and even the same /home partition (although same /home is more complicated).
I choose separate / and /home for each distribution and control overall booting by grub legacy.

For me, grub2 offers no real advantage and its far easier to edit menu.lst
then go through  grubs 2's scripts.

There are other ways of multi booting too, but so as not to confuse systems try not to install the bootloader.
Picking up alternate distros with grub2 is actually easier, running 
update-grub will do this. With grub legacy you have to manually edit
/boot/grub/menu.lst to boot the newly installed system.

Hope that helps, I can post my menu.lst if you want to see it.

---

### Post by Chriske on 2011-05-30
Many thanks hal8000 for the helpful reply.

I do choose custom partitioning for these secondary distros, but I must have missed the option to not install the bootloader. I'll definitely look for that next time.

On installation the new GRUB2 picked up all the distros - that bit was fine.

So, taking things as they are, I still have this issue where, if I delete my MINT partition, I'm going to be left with no GRUB2 and a rescue prompt.

---

### Post by YesWeCan on 2011-05-30
The way Grub2 works is a little unintuitive.
It is actually in 3 parts, one of which is inside the OS partition itself. This means that when you delete the OS you delete part of Grub and it won't work.

What you actually want is Grub2 in its own partition so that you can install and remove OS's without affecting it. I am not sure this is possible, I am looking in to it myself.

So you have to decide which OS will last the longest and use it's Grub2 to boot all the other OS's too. And as hal8000 says you need to prevent a new Grub2 being installed when you install a new OS. When you boot, the original Grub2 menu will not show the new OS until you have booted the old OS and run 'sudo update-grub'.

---

### Post by YesWeCan on 2011-05-30
> **Chriske said:**
> So, taking things as they are, I still have this issue where, if I delete my MINT partition, I'm going to be left with no GRUB2 and a rescue prompt.
You need to boot into an different linux OS, then do 'sudo grub-install /dev/sdx' where x is the drive you want the Grub2 MBR on, and this will reinstall Grub2 using this OS. Then you can delete Mint and it won't affect Grub. To remove the Mint entry from the Grub menu run 'sudo update-grub' using this OS.

---

### Post by Chriske on 2011-05-30
Thanks YesWeCan.

Yes, that's exactly it. If I could manage to get an "independent" GRUB in future, that would nail the issue.

Right now I have a GRUB with a nice MINT splashscreen behind it on boot. :(

But, in the background (somewhere) the Ubuntu GRUB is still lurking as I can see it via startup-manager (and it has the correct entries). So, that's the one I would keep and use to control the other distros...if I were able to! :)

So, to your last point then: how would I boot into Ubuntu when the GRUB rescue prompt pops up after I delete MINT?

---

### Post by YesWeCan on 2011-05-30
Before you delete Mint, boot Ubuntu. Then do 'sudo grub-install /dev/sda' and this will make your bios use the Ubuntu Grub instead of the Mint Grub (it over-writes the Mint Grub MBR and 1st sector files). Then you can delete Mint. Then boot Ubuntu again and do 'sudo update-grub' to remove the Mint entry from the Grub boot menu.

I have just discovered Mint. This Unity debacle has caused me to explore alternative distros. My initial impression of Mint is really good. It looks very well organized and better documented, and Mint 12 will come with Gnome Shell as standard, so I read.

---

### Post by Chriske on 2011-05-30
OK, done that installation of the Ubuntu GRUB and it now appears at boot, thanks very much.

But, I think what's going to happen is that GRUB will still fail with an error like "can't find partition/OS", if I delete MINT. But maybe I can recover then with a GRUB rescue disk?

MINT is nice, lovely interface, but it's still unstable (for me anyway). I keep getting applets not loading error messages on startup (clock, etc) and sometimes applications just freeze and I have to use force quit to exit (e.g. exaile).

From a stability and footprint point of view Puppy is very good, IMHO.

---

### Post by dragonfly41 on 2011-05-30
This old thread suggests installing a separate /boot partition for Grub loader

[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)

so there would be

/ ... partition
/boot  ...  partition
/home ...  partition

I haven't tried this yet.

---

### Post by YesWeCan on 2011-05-30
> **Chriske said:**
> But, I think what's going to happen is that GRUB will still fail with an error like "can't find partition/OS", if I delete MINT. But maybe I can recover then with a GRUB rescue disk?
It will be fine :)

If you ever end up at the rescue prompt again, you can boot Ubuntu manually. Assuming sda5 is your Ubuntu root partition:

```
rescue> set prefix=(hd0,5)/boot/grub
rescue> insmod (hd0,5)/boot/grub/linux.mod
rescue> set root=(hd0,5)
rescue> linux /vmlinuz root=/dev/sda5 ro
rescue> initrd /initrd.img
rescue> boot
```

Then do 'sudo grub-install /dev/sda'

---

### Post by YesWeCan on 2011-05-30
@dragonfly41 - thanks.

---

### Post by Chriske on 2011-05-30
> **YesWeCan said:**
> It will be fine :)


And, of course, it was! :D

Fantastic advice, thank you, and noted for future reference.

[Brilliant forum. Where else could you get a successful resolution to such a problem so quickly!?]

---

