---
title: "&quot;Grub Issue&quot;"
date: 2010-09-22
forum: General Help
---

### Post by sami8519 on 2010-09-22
Hi guys,

well, I am trying to avoid a problem which always encounter me!

I have 3 partitions on my HDD. One windows 7 and two ubuntu lucid. I installed Windows first which is on Sda1, first ubuntu on sda5, and the 2nd ubuntu on sda7. My problem is that whenever I delete the last partition(last ubuntu install which has the grub loade) I will end up stuck in the grub rescue upon booting(which makes me do reinstalling in order to be able to boo into my systems). So is there anything I have to do prior to deleting the last ubuntu installation without getting the grub rescue?

Thanks

Regards
Sami

---

### Post by SmokeyThePanda on 2010-09-22
I believe you need to rerun the install for the windows or second Ubuntu installation and reinstall grub boot loader to the master boot record. For, I imagine in your install, you installed grub to the master boot record for the third installation. Thus, when you delete it, you also delete the grub. O.o If that makes sense. So, like, go into an expert mode of the windows or ubuntu install cd and try to reinstall grub to the MBR. I am not 100% sure how to do it, for I haven't used Ubuntu in forever.

---

### Post by sami8519 on 2010-09-22
Thanks mate your help is appreciated but I am not that solid in linux so I would love if somebody could help me how to do it. Thanks

Regards
Sami

---

### Post by SmokeyThePanda on 2010-09-22
No worries, that's what this forum is here for. :) When I dual booted SliTaz with my Debian, I installed it to the MBR and couldn't figure out how to get it working again, so I reinstalled. :p Though, with Debian, there's an option in the one of the menus and you can repair grub. I have no idea with Ubuntu, sadly. :(

---

### Post by john newbuntu on 2010-09-22
I am assuming yours is a simple/straightforward install with part of Grub2 installed to the MBR and that you have only one disk.  So you have ubuntu on sda5 and sda7.  When you run this command from Application->accessories->terminal:
```
sudo grub-probe -t device /boot/grub
```you are likely to get /dev/sda7.  This is obviously because your last ubuntu install was on sda7, where your boot files reside.

Now, lets say, you want to get rid of ubuntu on sda7.  Make sure that the sda5 partition is mounted.  Let us say the mount point is on /media/mylinux (In general label your partitions for easy identification.  Check mounts using the command "cat /proc/mounts").  Then run the command:
```
sudo grub-install --root-directory=/media/mylinux /dev/sda
```Then reboot.  If you boot into ubuntu, run "sudo update-grub".  Also run that first command that you ran "sudo grub-probe ..." and that should now list /dev/sda5.  You are good to go.

Should you still encounter problems, use section #13 from this article by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If that does not work either, post the output of the boot_info_script using code tags at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)  Follow the instructions on this page carefully.

If everything looks good, decide on whether to make a copy of your install on sda7 or move  important files elsewhere or just nuke the entire partition.  You can do  that by booting from a liveCD.

---

### Post by sami8519 on 2010-09-22
Thanks a lot mate, everything is good now:)

Best Regards
Sami

---

