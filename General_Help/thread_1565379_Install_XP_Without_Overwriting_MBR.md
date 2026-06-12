---
title: "Install XP Without Overwriting MBR?"
date: 2010-08-31
forum: General Help
---

### Post by moore.bryan on 2010-08-31
I already have numerous Linux distros installed on partitions and I want to make a new partition, format it NTFS, and install XP on it; however, I don't want XP to overwrite the MBR with GRUB on it... is that even possible?

---

### Post by jmc1987 on 2010-08-31
You don't.  You have to install windows and then use your grub utility

---

### Post by Mark Phelps on 2010-08-31
> **moore.bryan said:**
> I already have numerous Linux distros installed on partitions and I want to make a new partition, format it NTFS, and install XP on it; however, I don't want XP to overwrite the MBR with GRUB on it... is that even possible?

Sorry ... no.  MS Windows installations, unlike Linux installations, do NOT provide you any flexibility regarding whether or not to mess with the MBR.

---

### Post by aeronutt on 2010-08-31
Unless you install Windows in VirtualBox. :)

---

### Post by zaphod777 on 2010-08-31
It's not as pretty but may be worth it to save you the time. 
Install a spare HDD and set you BIOS to prompt the boot device and then install windows to the second HDD. 

It will add an extra step in your bootup process but it may be worth it to save you the time and energy.

---

### Post by oldfred on 2010-09-01
It is not all that difficult just to reinstall grub to the MBR. You need a liveCD and know which partition your main install is one.

If you have multiple installs you should learn to use this tool to record what is installed where. I run it before making any system changes.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by linux18 on 2010-09-01
if you have a floppy drive:
-dd if=/dev/sda of=dev/fd0 bs=512 count=1 
-then install windows
-then from a live cd:
-dd if=/dev/fd0 of=dev/sda bs=512 count=1

this way you maintain all of your linux installation locations

---

### Post by moore.bryan on 2010-09-01
Wow, guys... thanks for all the responses. I actually thought this was going to languish for a while!

@linux18: Would this work with a USB stick?

@jmc1987: Hmm... could I put the GRUB rescue disk on a USB?

---

### Post by oldfred on 2010-09-01
While you can use unetbootin or pendrive to install one ISO to a USB flash drive, you can set it up to save some data and it works great with 1GB or even 2GB flash drives.

Allows extra space on flash to be used
[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

But if your flash is larger it is a waste of space. I installed several copies of Ubuntu, system rescue, gparted and a couple of other ISOs all on one 4GB flash drive.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

Or a script to do it all:
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)

---

### Post by linux18 on 2010-09-01
> **moore.bryan said:**
> Wow, guys... thanks for all the responses. I actually thought this was going to languish for a while!

@linux18: Would this work with a USB stick?

@jmc1987: Hmm... could I put the GRUB rescue disk on a USB?
yes, just replace /dev/fd0 with /dev/sdb (its usually sdb, but if you have 2 hard drives it's usually pushed to sdc)
you will have to update grub to include the windows entry

p.s. I hope that windows copy is n-lite remixed

---

### Post by borth92 on 2010-09-01
even if it does overwrite mbr, you can just pop in a live cd and restore grub...

---

### Post by moore.bryan on 2010-09-02
Thanks, all... you've put my mind at rest!

---

### Post by moore.bryan on 2010-09-03
So I guess I marked this "SOLVED" too soon... it turns-out there's **no way** of installing XP to a *specific*, already prepared partition. You need to delete **all** partitions on a disk, install XP, then reinstall Linux. Not worth my time... I'll just live with XP in VirtualBox.

---

### Post by oldfred on 2010-09-03
XP should install to a partition. But it needs to see a NTFS partition with the boot flag (active partition) and it has to be a primary partition. Or you can have unallocated space and a available primary partition. 

Windows will not install to a logical partition unless you have a primary partition with windows already installed and then it moves the boot files to the primary so the install in the logical can only be booted thru the primary partition.

---

### Post by moore.bryan on 2010-09-03
> **oldfred said:**
> XP should install to a partition. But it needs to see a NTFS partition with the boot flag (active partition) and it has to be a primary partition. Or you can have unallocated space and a available primary partition. 

Windows will not install to a logical partition unless you have a primary partition with windows already installed and then it moves the boot files to the primary so the install in the logical can only be booted thru the primary partition.

Interesting... thanks for the insight. Now the issue is GParted won't let me set my former NTFS partition as a primary one. Any ideas there?

---

### Post by oldfred on 2010-09-03
If you have used all four primary or three primary and one extended then your have to totally reconfigure.

---

### Post by reiki on 2010-09-03
I have XP in a ViertualBox VM. It was just a whole lot easier than the whole multiboot thing and I can have Ubuntu and XP running at teh same time if I want. :)

---

### Post by moore.bryan on 2010-09-04
> **oldfred said:**
> If you have used all four primary or three primary and one extended then your have to totally reconfigure.
I don't... only two primary.

> **reiki said:**
> I have XP in a ViertualBox VM. It was just a whole lot easier than the whole multiboot thing and I can have Ubuntu and XP running at teh same time if I want. :)
It looks like this is what I'm going to have to stick with...

---

### Post by rewyllys on 2010-09-04
> **moore.bryan said:**
> I already have numerous Linux distros installed on partitions and I want to make a new partition, format it NTFS, and install XP on it; however, I don't want XP to overwrite the MBR with GRUB on it... is that even possible?
I concur in the recommendations that you use XP in VirtualBox.  It works just fine for me.  

BTW, an easy way of sharing files between XP in VBox and your Linux distros is to install Dropbox; it's free (up to 2GB of storage) and works in Linux, Windows, and MacOS.

---

### Post by linux18 on 2010-09-04
> **rewyllys said:**
> I concur in the recommendations that you use XP in VirtualBox.  It works just fine for me.  

BTW, an easy way of sharing files between XP in VBox and your Linux distros is to install Dropbox; it's free (up to 2GB of storage) and works in Linux, Windows, and MacOS.
guest additions are in the repository and they allow you to do that and more, faster.

I would share my super fast xp vdi, but I can't (copywrite, Microsoft, rules, too busy with DNF news) but I can get a list of tweaks (nlite + registry)

---

### Post by moore.bryan on 2010-09-04
> **rewyllys said:**
> I concur in the recommendations that you use XP in VirtualBox.  It works just fine for me.
It works *fine* for me, too, but I was looking to use XP in a more standard way. VB is pretty amazing stuff, just runs a bit slow.

> BTW, an easy way of sharing files between XP in VBox and your Linux distros is to install Dropbox; it's free (up to 2GB of storage) and works in Linux, Windows, and MacOS.
Good advice. I already use a trio; basically, I have ~100gb of my hard drive devoted to sharing files between all my installed Linux distros, I use Dropbox, and I operate a web server I mount with SSHFS. By the way, SSHFS is a *beautiful* thing.

> **linux18 said:**
> guest additions are in the repository and they allow you to do that and more, faster.
I already installed the "closed source" VB to get USB functionality, as--apparently--it's not available in the OSE version.

> I would share my super fast xp vdi, but I can't (copywrite, Microsoft, rules, too busy with DNF news) but I can get a list of tweaks (nlite + registry)
I'd absolutely *love* the tweaks, please. My VB XP install runs well, but I'd like to get more speed out of it.

---

### Post by linux18 on 2010-09-04
I had a huge list of tweaks, but I hit refresh and lost it (I hope there is a FF addon to save that stuff)

use google when unsure

step 1: create the ISO
Use n-lite to remaster the windows ISO and shrink it. remove almost everything and get the iso to ~ 170MB.

step 2: tweak the installation
after making an ISO, and installing there are a few tweaks to speed things up
-disable drive indexing
-launch folder view in a separate process
-don't scan for network folders and printers in My Computer
-load the kernel into ram [http://www.tweakxp.com/article37016.aspx](http://www.tweakxp.com/article37016.aspx)
-tweak the install [http://www.tweakxp.com/tweakutility/](http://www.tweakxp.com/tweakutility/) uninstall after your done tweaking
-use the classic theme and menu
-use ccleaner [Download CCleaner 2.35.1223 - FileHippo.com]("http://www.filehippo.com/download_ccleaner/")
-auslogics registry cleaner [http://www.auslogics.com/en/software/registry-cleaner/download/](http://www.auslogics.com/en/software/registry-cleaner/download/) run a few times then uninstall
-type msconfig, choose selective startup, only check the services checkbox, and disable all services (except essential, upnp, msi installer, and ethernet config)
- goto c:\windows\fonts, select all, press delete
-disable swap file if you've allocated more than 1024MB of ram   

step 3: programs
-only use portable applications when possible [http://portableapps.com/](http://portableapps.com/)
-remove application uninstallers and copy them to an external drive when convenient
-use ubuntu's gufw and your router firewall instead of a windows firewall
-only use antivirus weekly or monthly and never let it start it's own service when your not using it

with all of these tweaks you should use 27 - 37 MB of ram on startup and when idle plus you should be able to restore a Vb snapshot in about 4 seconds

---

### Post by moore.bryan on 2010-09-06
I can use n-lite in VB?

---

### Post by linux18 on 2010-09-06
yes, but you need to install guest additions to get the iso out of virtualbox to use as the boot disk.

---

### Post by moore.bryan on 2010-09-06
Hmm... I'll have to play around with this. I've already installed Guest Additions. Any wiki I can reference?

---

### Post by linux18 on 2010-09-06
n-lite is very easy and self explanitory "remove printer drivers? ", "remove themes? " 
you only need to use google "as needed"

for virtualbox this is a very definative manual:
[http://wiki.archlinux.org/index.php/VirtualBox](http://wiki.archlinux.org/index.php/VirtualBox)

---

### Post by moore.bryan on 2010-09-06
But how do I select the ISO?

---

### Post by linux18 on 2010-09-06
1-install xp in the virtualbox
2-install n-lite
3-remaster the install iso 
4-copy the remastered iso out of virtualbox
5-re-install xp using the remastered iso

Where are you going wrong

---

### Post by dcstar on 2010-09-07
> **linux18 said:**
> if you have a floppy drive:
-dd if=/dev/sda of=dev/fd0 bs=512 count=1 
-then install windows
-then from a live cd:
-dd if=/dev/fd0 of=dev/sda bs=512 count=1

this way you maintain all of your linux installation locations

Pffttt.. the first 512 bytes has **more** than the MBR, it also contains partition info. You should only work with the specific MBR area:

```
dd if=/dev/hda of=/mbr-backup bs=**446** count=1
```

---

### Post by moore.bryan on 2010-09-07
> **linux18 said:**
> 1-install xp in the virtualbox
2-install n-lite
3-remaster the install iso 
4-copy the remastered iso out of virtualbox
5-re-install xp using the remastered iso

Where are you going wrong

I'm not sure about step 3. I seemed to get things moving when I selected D:, which--I think--is where nLite sees my iso.

I'm also not sure about which networking settings are needed...

---

