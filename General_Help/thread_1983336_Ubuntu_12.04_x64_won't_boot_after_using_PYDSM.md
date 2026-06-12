---
title: "Ubuntu 12.04 x64 won't boot after using PYDSM"
date: 2012-05-20
forum: General Help
---

### Post by morningstar.fallen on 2012-05-20
...the noob I am!!!

Last night I've decided to add an extra data drive to my desktop. My normal setup is one 1TB drive divided into a 100GB ext4 system partition, 16GB swap space and circa 850GB NTFS partition with all my media. The largest part is a remnant of my previous Windows installation, which I never had time to convert to ext4. This NTFS partition was normally automatically mounted on boot using PYDSM setting. After adding the addional drive (which still contained Windows system files from my old laptop), my original NTFS partition failed to boot automatically. After that I have formatted the new drive as ext4 and for some silly (noob) reason went to play with PYDSM. I've set all available partitions (except swap) I could find on both sda and sdb (I think there was only sda before) to mount automatically on boot and to allow all users mount and unmount partitions at will. From then on my memories are a bit foggy but I think I remember wondering why was PYDSM displaying my original NTFS partition as sdb instead of usual sda.

Then after reboot the system went through GRUB but no further. Did not display the OS loading logo, only flashing cursor in upper left corner. I could hear some disk activity but that ceased after a moment and then nothing.

I've tried to change SATA settings in bios from AHCI to IDE and back. Tried to remove the new drive and connect the old one to a different controller, but no joy. I did a boot from the boot-repair-disc and attempted the 'recommended' repair and then also tried to specify which partition to boot from but without any success. I don't think it's a hardware failure because both drives show as healthy and I can se all my files from the boot-repair-disc file manager. Also when I boot to recovery from GRUB and try to work with existing partitions, I get lots of access denied errors.

So far it looks that I have the only (rather painful) option of reinstalling the whole system :'(

Does anybody have any good ideas how to avoid that?

---

### Post by soumoks on 2012-05-20
> **morningstar.fallen said:**
> ...the noob I am!!!

Last night I've decided to add an extra data drive to my desktop. My normal setup is one 1TB drive divided into a 100GB ext4 system partition, 16GB swap space and circa 850GB NTFS partition with all my media. The largest part is a remnant of my previous Windows installation, which I never had time to convert to ext4. This NTFS partition was normally automatically mounted on boot using PYDSM setting. After adding the addional drive (which still contained Windows system files from my old laptop), my original NTFS partition failed to boot automatically. After that I have formatted the new drive as ext4 and for some silly (noob) reason went to play with PYDSM. I've set all available partitions (except swap) I could find on both sda and sdb (I think there was only sda before) to mount automatically on boot and to allow all users mount and unmount partitions at will. From then on my memories are a bit foggy but I think I remember wondering why was PYDSM displaying my original NTFS partition as sdb instead of usual sda.

Then after reboot the system went through GRUB but no further. Did not display the OS loading logo, only flashing cursor in upper left corner. I could hear some disk activity but that ceased after a moment and then nothing.

I've tried to change SATA settings in bios from AHCI to IDE and back. Tried to remove the new drive and connect the old one to a different controller, but no joy. I did a boot from the boot-repair-disc and attempted the 'recommended' repair and then also tried to specify which partition to boot from but without any success. I don't think it's a hardware failure because both drives show as healthy and I can se all my files from the boot-repair-disc file manager. Also when I boot to recovery from GRUB and try to work with existing partitions, I get lots of access denied errors.

So far it looks that I have the only (rather painful) option of reinstalling the whole system :'(

Does anybody have any good ideas how to avoid that?
Shouldnt have used PYSDM in the first case,itseems to be an old app with no official support,i also had trouble with it,but the forum members solved it(thank god!!!),i am sure they will come to ur rescue also,wait for some time..

---

### Post by morningstar.fallen on 2012-05-20
Is there any tool that could manage the setting of a dead OS? Mainly the mounting and permissions options?

---

### Post by morningstar.fallen on 2012-05-21
Or anything I could do to avoid having to reinstall the whole system?

---

### Post by YannBuntu on 2012-05-21
Hello
PYDSM is very old ([last version]("http://sourceforge.net/projects/pysdm/files/") is 2006), i am not sure why it is still available in the Ubuntu Software Center.

I prefer to use Disk-Manager instead. It's last DEB is here,: [https://launchpad.net/disk-manager/+download](https://launchpad.net/disk-manager/+download) (see also [https://bugs.launchpad.net/ubuntu/+source/disk-manager/+bug/1002281](https://bugs.launchpad.net/ubuntu/+source/disk-manager/+bug/1002281) )


Please could you indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1")?

---

### Post by Morbius1 on 2012-05-21
> From then on my memories are a bit foggy but I think I remember  wondering why was PYDSM displaying my original NTFS partition as sdb  instead of usual sda.Because PySDM, mountmanager, disk manager, whatever else is out there left the building before the memo got out about using UUID's instead of /dev/sdxy.

I would suggest using templates instead. For ntfs:
```
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```For ext4:
```
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
```** To find the correct UUID for your partitions:
```
sudo blkid -c /dev/null
```** You will have to create the mount point yourself, for example:
```
sudo mkdir /media/WinD
```** Then add the template with the correct UUID and mount point to fstab:
```
gksu gedit /etc/fstab
```** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot.  You will know before you reboot if something is amiss. :
```
sudo mount -a
```[COLOR=Blue]*If there are no errors it just comes back to the prompt.*[/COLOR]

It's a lot easier and as you have found out a lot safer to do it this way and you don't end up cluttering fstab with a lot of useless ( user ) or absurd ( users ) mount options in fstab.

But this is just my opinion :)

---

### Post by YannBuntu on 2012-05-21
(FYI Disk-Manager manages UUIDs)

---

### Post by Morbius1 on 2012-05-21
Okey dokey, I installed it on a VBox guest I have set up for this type of thing. I unleashed it on a NTFS partition since that is where the most options can be used or abused. This is the entry it created in fstab:
> UUID=40F76A4E40B0C5CB    /media/DataN    ntfs-3g    defaults,locale=en_US.UTF-8    0    0** You are correct it did get the memo about UUID

** It will also give you an error message if you add a file and then try to send it to the trash. Why? Because although permissions have been set to 777 so everyone can access the partition the partition is owned by root and it's his trash can not yours. Setting uid=1000 fixes that.

** I can add a file to that ntfs partition with a name that has "special" characters in it. Characters that a Windows OS cannot read and interpret. Adding the option "windows_names" fixes that.

** It's somewhat fixated ( just like ntfs-config was back in its day ) on ntfs vs ntfs-3g. In Ubuntu they are one in the same since one is linked to the other. But that's a minor thing.

So without any kind of adjustment that line will induce one and possibly 2 visits to the forum to explain / resolve. If I use the template approach I would have automatically eliminated both problems.

---

### Post by YannBuntu on 2012-05-21
Thanks Morbius. I suggested these options to the app devs: [https://bugs.launchpad.net/disk-manager/+bug/1002444](https://bugs.launchpad.net/disk-manager/+bug/1002444)

---

### Post by Morbius1 on 2012-05-21
Wouldn't make any sense to add it to the defaults since an application like this has to run on all installs and not all of them have uid's in the 1000 range depending on which branch of Linux is being used and how old it is.

And since it differentiates ntfs and ntfs-3g it's not clear to me that it's still being actively developed only repackaged. [COLOR=Blue]EDIT[/COLOR]: Actually I don't know if that's true. THere may be some distro out there that actually does separate the old ntfs from ntfs-3g.

What makes sense is to avoid ntfs-config, mountmanager, disk-manager ( although it's not in the repos as far as I can tell so for the average user this may never come up ), .. oh ... and PySDM and ....

---

### Post by YannBuntu on 2012-05-21
I don't know much this subject, but i think Ubuntu would benefit having a GUI to edit fstab, because auto-monting a partition is a frequent question on forums, and many users don't like CLI.
Disk-Manager seems to work well (i never had problems with EXT partitions, and for NTFS we can modify the option easily), but this could also be a feature added to Disk-Utility (which is installed by default in Ubuntu).
I have emailed the dev of Disk-Manager, let's see if the project is alive or not. If not, i'll have a look at the code if i have time.

---

### Post by morningstar.fallen on 2012-05-21
> **Morbius1 said:**
>  ...It's a lot easier and as you have found out a lot safer to do it this way and you don't end up cluttering fstab with a lot of useless ( user ) or absurd ( users ) mount options in fstab.

But this is just my opinion :)

Many thanks for this! It has helped a lot when setting the auto-mount again after the reinstall! :) Only after I've done it I realized that I should have tried to rewrite the fstab of my old system using a live cd instead of reinstalling... The procedure you have described is much more effective and foolproof than using a GUI such a pysdm and in general wasn't as painful as I previously thought. Oh well, lesson learned, thanks mate! ;-)

---

### Post by morningstar.fallen on 2012-05-21
Here's a reading of my new fstab after editing. Works like a charm! 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=b0563d50-8d39-494d-bf5b-7bc7d02f40c9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=e5a0d2f5-0ceb-4768-8a16-a766f6a92eee none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[B]UUID="AC8445C7844594AC" /media/Storage_I ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

UUID="2c501dfc-b505-4a28-adae-99d64cc98040" /media/Storage_II ext4 defaults,noatime 0 2[/B]
```

---

### Post by Morbius1 on 2012-05-21
This is good! If you don't mind if would be great if you tagged this as Solved by going to the "Thread Tools" and selecting "Mark this thread as solved". Some folks do searches and only look at those things marked as solved.

Besides we win prizes based on how many people we actually help - um .. at least I think we do :p

---

### Post by morningstar.fallen on 2012-05-21
> **Morbius1 said:**
> This is good! If you don't mind if would be great if you tagged this as Solved by going to the "Thread Tools" and selecting "Mark this thread as solved". Some folks do searches and only look at those things marked as solved.

Besides we win prizes based on how many people we actually help - um .. at least I think we do :p

All done mate! ;-) Thanks again and good luck winning the prize!!!

---

### Post by colin.p on 2012-05-22
> **Morbius1 said:**
> Because PySDM, mountmanager, disk manager, whatever else is out there left the building before the memo got out about using UUID's instead of /dev/sdxy.

I would suggest using templates instead. 

****thanks and duly copied****

It's a lot easier and as you have found out a lot safer to do it this way and you don't end up cluttering fstab with a lot of useless ( user ) or absurd ( users ) mount options in fstab.



Thanks for the easy explanation. I too had problems with pydsm (been using it since intrepid) but precise doesn't seem to like it at all. With your templates, it all works fine. I am now getting pretty good with editing fstab, since I have been playing with it for the better part of a week.;)

---

