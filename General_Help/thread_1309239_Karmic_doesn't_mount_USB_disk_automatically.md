---
title: "Karmic doesn't mount USB disk automatically?"
date: 2009-11-01
forum: General Help
---

### Post by tubunu on 2009-11-01
After a clean install of Karmic I am unable to mount my USB disk at all. It used to be mounted automatically in Jaunty and the files would pop up in Nautilus. I cannot mount it manually either. I've done 

```
sudo mount /dev/sdc /mnt/disk
```

and nothing happens. Any clues?

---

### Post by peculiar penguin on 2009-11-01
Works for me. Check the logs for error messages?

---

### Post by half-life on 2009-11-01
Same problem here. With usb hdd, pen and dvd's.
I have to reboot so that the hdd appears and can be mountend.

---

### Post by tubunu on 2009-11-01
I even installed most of the mount applications from the Synaptic and still no go.. :(

---

### Post by tubunu on 2009-11-01
OK, so I can see my USB disk being mounted in Palimpsest Disk Utility (System>Administration>Disk Utility). It is listed as /dev/sdc and the filesystem as /dev/sdc1. 

QUESTION: How can I open the folders on that disk for viewing? It's not mounted automatically.

---

### Post by tubunu on 2009-11-01
Anyone else, please?

---

### Post by Uncle Spellbinder on 2009-11-01
Strange. I have 2 external terabyte hard drives and 1 external 200gig hard drive. Recognized and mounted automatically. I didn't have to do anything.

:-k

---

### Post by Magnes on 2009-11-01
Yesterday Karmic didn't mount USB disk for me either. But today it's OK. Maybe the bug was fixed (I installed all updates meanwhile).

---

### Post by tubunu on 2009-11-01
I also installed all the updates but it doesn't seem to want to work.

---

### Post by crjackson on 2009-11-01
Karmic on 4 machines here and so far no problems.

---

### Post by Odemia on 2009-11-01
Working fine here too, on multiple machines multiple pen drives.  Perhaps if there was some more info, we could be more helpful.

What is the output of "ls -al /media" and "ls -al /media/disk"?
Output of "lsusb" (with pen drive plugged in)?
What does your /etc/fstab look like?
Output of "tail /var/log/messages".
What format is the pen drive?
This is probably obvious but have you tried "sudo mount /dev/sdc1 /mnt/disk"?

---

### Post by TheStagesmith on 2009-11-01
I tried this with several FAT16 pen drives, and only one of them was automatically mounted. Everything else was normal; the drive was detected by lsusb, I was able to manually mount it as well. I'm guessing then that the problem is in the hotplug utility. It's still an annoyance, though, since it's much nicer to make a startup usb drive using the built-in startup disk creator than to do so manually, among other things.

---

### Post by sayyidhassan on 2009-11-02
i could mount sda cards,usb's on the fly in Jaunty(and very fast),but after a fresh install of Karmic,nothing can be mounted.

---

### Post by SirBismuth on 2009-11-02
Just checked, and it works the same as it did in jaunty for me... sorry I can't be of any more help.

B

---

### Post by funacide on 2009-11-02
I am having the same problem, since going 9.1, any info appreciated?

---

### Post by eborigene on 2009-11-02
> **Odemia said:**
> Working fine here too, on multiple machines multiple pen drives.  Perhaps if there was some more info, we could be more helpful.

What is the output of "ls -al /media" and "ls -al /media/disk"?
Output of "lsusb" (with pen drive plugged in)?
What does your /etc/fstab look like?
Output of "tail /var/log/messages".
What format is the pen drive?
This is probably obvious but have you tried "sudo mount /dev/sdc1 /mnt/disk"?

External drive that was stripped out of an old ThinkPad does not work. Thouhg it is recognised in Windows. Filesystem is ntfs. Label is EXTINTO
Output of suggested commands bellow:

Output of ls -al /media
adsm@vdmcm:/dev$ ls -al /media
total 28
drwxr-xr-x  5 root root  4096 2009-11-02 09:48 .
drwxr-xr-x 21 root root  4096 2009-11-01 21:59 ..
lrwxrwxrwx  1 root root     6 2009-11-01 21:28 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2009-11-01 21:28 cdrom0
lrwxrwxrwx  1 root root     7 2009-11-01 21:28 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2009-11-01 21:28 floppy0
drwx------ 38 adsm adsm 12288 1970-01-01 01:00 KINGSTON

Output of tail /var/log/messages
adsm@vdmcm:/dev$ tail /var/log/messages
Nov  2 10:32:32 vdmcm kernel: [ 2683.975946] __ratelimit: 1 callbacks suppressed
Nov  2 10:32:32 vdmcm kernel: [ 2683.978049] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  2 10:32:32 vdmcm kernel: [ 2683.978054] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Nov  2 10:32:32 vdmcm kernel: [ 2683.978058] sd 4:0:0:0: [sdb] Add. Sense: Invalid command operation code
Nov  2 10:32:32 vdmcm kernel: [ 2684.322172] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  2 10:32:32 vdmcm kernel: [ 2684.322179] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Nov  2 10:32:32 vdmcm kernel: [ 2684.322183] sd 4:0:0:0: [sdb] Add. Sense: Invalid command operation code
Nov  2 10:32:32 vdmcm kernel: [ 2684.323051] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  2 10:32:32 vdmcm kernel: [ 2684.323054] sd 4:0:0:0: [sdb] Sense Key : Illegal Request [current] 
Nov  2 10:32:32 vdmcm kernel: [ 2684.323057] sd 4:0:0:0: [sdb] Add. Sense: Invalid command operation code
adsm@vdmcm:/dev$

output of sudo ls -al /media/disk

adsm@vdmcm:/dev$ sudo ls -al /media/disk
ls: não consigo aceder a /media/disk: Ficheiro ou directoria inexistente [roughly translated from portuguese: no access to /media/disk: File or directory does not exist]

Output of lsusb
adsm@vdmcm:/dev$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0951:1613 Kingston Technology 
Bus 002 Device 002: ID 04cf:8818 Myson Century, Inc. USB2.0 to ATAPI Bridge Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Outuput of sudo mount /dev/sdc1 /mnt/disk

adsm@vdmcm:/dev$ sudo mount /dev/sdc1 /mnt/disk
mount: mount point /mnt/disk does not exist
adsm@vdmcm:/dev$ 

Thanks for your help.
I am using Ubuntu Karmic Koala (updates made today)

---

### Post by zeus.jay on 2009-11-02
Hi I have noticed the same thing.

I also noticed it seems like Karmic is almost doing a filesystem check on the usb drive before mounting i.e. something that is looking at the smart drives output.

Anyway to manually mount.

ls -lrt /dev/disk/by-id

lrwxrwxrwx 1 root root  9 2009-11-02 15:20 usb-ST315003_9VS22GMC_22229632217C-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2009-11-02 15:20 usb-ST315003_9VS22GMC_22229632217C-0:0-part1 -> ../../sdb1


this should give you the device that was most recently attached (alternatively run dmesg will show you entries like this)


168283.396883] sd 23:0:0:0: Attached scsi generic sg2 type 0
[168283.410501] sd 23:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[168283.411242] sd 23:0:0:0: [sdb] Write Protect is off
[168283.411249] sd 23:0:0:0: [sdb] Mode Sense: 00 38 00 00
[168283.411255] sd 23:0:0:0: [sdb] Assuming drive cache: write through


Above shows the partition is sdb1

I create a mount point in /media 

sudo mkdir /media/mydrive

(don't know why but I do change ownership)

sudo chown myuser:myuser /media/mydrive

The drive in question is ntfs


so to mount

sudo mount -t ntfs-3g /dev/sdb1 /media/mydrive/

---

### Post by SSamiK on 2009-11-03
I'm having the same problem on one of my computers...  Neither my external HDD's or my USB-sticks will auto mount on my PC, but on my Notebook it's working as expected. Manually mounting works, but what a drawback...!! Have anyone reported a bug? We should get this fixed ASAP!

---

### Post by sayyidhassan on 2009-11-03
SD card automatically mounted on the same laptop while using a live Fedora12-Beta CD.

---

### Post by tubunu on 2009-11-03
OK folks.
It turned out that the reason why USB disk wasn't automatically mounted was that just right after a fresh install I uninstalled a couple of applications that I never use, apparently some of them had dependencies that got uninstalled as well and which were responsible for auto-mounting the disk. I reinstalled the applications I uninstalled and USB is mounted automatically. Cool.

What I'm wondering about though is, have the dependencies changed? I've always uninstalled applications like bluetooth, evolution, games, desktop sharing and viewing and never have I had problems with auto-mounting.

---

### Post by matthewbpt on 2009-11-03
Do you know what these are? I have the same problem, but I have no idea what to reinstall.

---

### Post by tubunu on 2009-11-03
> **matthewbpt said:**
> Do you know what these are? I have the same problem, but I have no idea what to reinstall.

Basically all the default applications that you might have uninstalled, see my previous post.

---

### Post by matthewbpt on 2009-11-03
Yea, I uninstalled bluetooth and it did delete a bunch of other stuff, and my drives stopped automounting, so I installed it again, but I don't think it reinstalled everything that was removed, because my drives still arent automounting :S ...

---

### Post by tubunu on 2009-11-03
If I can remember correctly, it was gvfs that enabled auto-mounting again. Look it up in Synaptic and try installing the files with that name. I did that.

---

### Post by sparker1 on 2009-11-03
I have the same problem. USB drives will mount if plugged in at boot time but not afterwards (but usb mouse has no problems). Palimpset also shows the drive is not mounted and is unrecognised as sdb1. An external powered HDD is recognised without problem. I had no problems with Jaunty. This is an MSI laptop, I also upgraded my desktop PC and it has no problems and mounts the same usb drive with ease. All updates have been installed. I can manually mount the drive. Nautilus is ticked to automount.

---

### Post by matthewbpt on 2009-11-03
> **tubunu said:**
> If I can remember correctly, it was gvfs that enabled auto-mounting again. Look it up in Synaptic and try installing the files with that name. I did that.

That worked! Thanx, to anyone having this specific problem, go to Synaptic, search for gvfs, and then install all gvfs packages that appear.

---

### Post by sparker1 on 2009-11-03
> **matthewbpt said:**
> That worked! Thanx, to anyone having this specific problem, go to Synaptic, search for gvfs, and then install all gvfs packages that appear.

Thanks, but didn't work for me.

---

### Post by sivlardemalle on 2009-11-04
> **sparker1 said:**
> Thanks, but didn't work for me.

If I load up gparted my usb disk comes up. I use that as a temporary work-around.

---

### Post by abdusamed on 2009-11-04
how do i keep something mount permanently? Because i have two partition, the music content which i have is on the windows hd, not the ubuntu partition. When ever i set it on scan and reboot, all my music content is gone from rhythm-box. What should i do?

---

### Post by sparker1 on 2009-11-04
> **sivlardemalle said:**
> If I load up gparted my usb disk comes up. I use that as a temporary work-around.

Thanks. I installed gparted with *sudo apt-get install gparted* but it doesn't show up in applications. I am beginning to think my installation is buggy. Perhaps I should go back to Jaunty? I can mount the usb drives with pmount but it is not a convenient solution.

---

### Post by sparker1 on 2009-11-04
I haven't tried it but here is a touted solution: 
[http://zkan.nokkok.com/2009/10/mount-usb-drive-on-ubuntu-9-10/](http://zkan.nokkok.com/2009/10/mount-usb-drive-on-ubuntu-9-10/)

[COLOR=Navy]*I write the solution for a problem that USB drive cannot be mounted automatically on Ubuntu 9.10.*[/COLOR]
 [COLOR=Navy]*Firstly, install gnome-mount.*[/COLOR]
 [COLOR=Navy]*sudo apt-get install gnome-mount*[/COLOR]
 [COLOR=Navy]*Secondly, go to System > Preferences > Startup Applications. And add this command.*[/COLOR]
 [COLOR=Navy]*gnome-mount -p xxx (change xxx to the volume label)*[/COLOR]
 [COLOR=Navy]*Finally, log out the system and it should work then. However, the problem still occurs after unmount and unplug the USB drive. To fix it, log out the system and then plug in the USB drive again. It is not a very good solution by the wa*y[/COLOR]. [IMG]http://zkan.nokkok.com/wp-includes/images/smilies/icon_sad.gif[/IMG]

edit: It works but if you unmount then you have to go through the process of logout remove drive, plug in drive and login. it's easier to manually mount.

---

### Post by sparker1 on 2009-11-05
latest updates a few minutes ago have not fixed the problem.

Hold the phone! If I upgrade udev to 147 6.1 (Karmic proposed) it fixes my problem. Hope it works for others too.

---

### Post by sayyidhassan on 2009-11-08
> **sparker1 said:**
> latest updates a few minutes ago have not fixed the problem.

Hold the phone! If I upgrade udev to 147 6.1 (Karmic proposed) it fixes my problem. Hope it works for others too.

Thanks,i enabled the proposed updates and chose to update udev only.immediately after the update i was able to use my card reader and usb without the need to reboot or logout.i hope it works for others also without undergoing any tinkering

---

### Post by wesblake on 2009-11-09
Perhaps this might help clarify the issue and find a solution?
I have the same problem, fresh install of 9.10, no removed packages.
What I've notice that has not been said though is that automount items (dvd, cd, usb drive) DO mount if it's the first thing you've put/plugged in. It's after you un-mount one of these items, then you can no longer plug/put in an item and have it auto-mount without logging out and back in. It does appear to be a bug in 9.10, sounds like a udev bug by the last couple posts so hopefully fixed soon? Not a big deal with usb drives, most of us probably don't plug them in too often, but I'm finding it to be a big pain with optical disks. I can, as mentioned, put in a dvd and have it mount and watch it, but once I eject it the second dvd I put in (or usb drive, etc) does not mount until I re-login.

---

### Post by dynaman on 2009-11-10
I too have been unable to plug usb devices and get them to auto mount 
looking at my /media folder i had many empty usb folders 
my solution was to delete these...

---

### Post by coffeecat on 2009-11-10
> **sparker1 said:**
> latest updates a few minutes ago have not fixed the problem.

Hold the phone! If I upgrade udev to 147 6.1 (Karmic proposed) it fixes my problem. Hope it works for others too.

Just to report, udev 147~-6.1 just came through for me this morning as a routine (not proposed) update. Hopefully this will fix this for those who haven't used proposed.

---

### Post by Nevermore on 2009-11-11
unfortunately i am in the same problem and the update didnt fix it...

---

### Post by no0ne on 2009-11-12
I've several usb devices always connected to my desktop and they work fine, but devices connected after boot won't mount or even show on ```
lsusb
```.

My laptop however lists and automounts everything right away.

Both of these systems are running Kubuntu Karmic i686 with kernel 2.6.31-14-generic.

I am also victim of the [ubuntu karmic & uvc webcam dilemma]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352") which effectively eliminated usb on the system until I applied the [temporary solution in post 28]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435352/comments/28").

So my take is that the detection of usb hardware added on the fly is currently in a less than favorable state, but there seems to be a hardware specific solution to most of the cases, guess I'll have to figure out one for the desktop. The desktop mobo is an Asus P6T Deluxe V2, which consists of mostly fresh intel parts.

---

### Post by chipppy on 2009-11-14
Good Evening 

I am yet another victim of this bug.
I have a slightly different scenario.

This thread has helped me fix it so big thanks for the assistance guys.

1 X Ubuntu Desktop (9.04-9.10 upgraded.  all updates installed) USB auto mount works fine
1 X Mythbuntu Front&Backend Machine (9.10 clean install with ext4, all updates installed) USB fails to auto mount.

Read through all this thread and a bit of research on the good old net.

[LIST]
[*]Did the manual mount of the drive to ensure that it works that way, and all good.  No mods to fstab
[*]left the USB hard drive plugged in and did a cold reboot and the drive was auto mounted
[*]disconnect the USB hard drive and plugged back in.  Didnt auto mount again.
[*]mod/edited fstab and added in the USB hard drive and it now mounts at logon only(as opposed to cold reboot).  If I disconnected the USB hard drive and then plugged back in it would not auto mount again.
[*][INDENT]Removed the mods to fstab so everything back to normal.[/INDENT]
[*]via synaptic package manager on Mythbuntu system 
[*][INDENT]Reinstalled ntfs-3g          - No change[/INDENT]
[*][INDENT]reinstalled gvfs only        - Problem solved.[/INDENT]
[/LIST]

I had my USB portable harddrive plugged in the whole time and as soon as the reinstall on gvfs was completed Thunar popped up with my USB harddrive files displayed.

Hope this helps someone else out.

cheers
chipppy

---

### Post by phillies on 2009-11-17
Same problem here. I was running Ubuntu Jaunty with fluxbox as desktop manager and Thunar as file explorer. It was always mounting USB drives immediately, showing them in thunar and accessable for any user.

Now, on krappy koala, the system recognizes the usb drive but does not mount it. Manually mounting using pmount works but is a pain in the ****. I upgraded as much as possible but nothing. In gnome-control-center the Removable Media option is set to Mount Automatically but is obviously ignored.

I'll play around a bit more, maybe I can find yet another workaround to post here.

Sad thing, with every release ubuntu gets 10 new useless features and loses/crashes 2-3 useful features.

---

### Post by phillies on 2009-11-17
Ok, my workaround is:

I reinstalled hal, thunar, gvfs
I installed gnome-volume-manager, gnome-mount, and gnome-device-manager

Strangely gnome-volume-manager forced brasero to be uninstalled. So I installed brasero again after I installed gnome-volume-manager which forced nautilus-cdburner to be uninstalled. Strange but I don't care. It works.

---

### Post by joshzam on 2009-11-19
> **wesblake said:**
> Perhaps this might help clarify the issue and find a solution?
I have the same problem, fresh install of 9.10, no removed packages.
What I've notice that has not been said though is that automount items (dvd, cd, usb drive) DO mount if it's the first thing you've put/plugged in. It's after you un-mount one of these items, then you can no longer plug/put in an item and have it auto-mount without logging out and back in. It does appear to be a bug in 9.10, sounds like a udev bug by the last couple posts so hopefully fixed soon? Not a big deal with usb drives, most of us probably don't plug them in too often, but I'm finding it to be a big pain with optical disks. I can, as mentioned, put in a dvd and have it mount and watch it, but once I eject it the second dvd I put in (or usb drive, etc) does not mount until I re-login.

Thanks for the clarification, wesblake. I am experiencing the same issue and I have no idea how to correct it. I've tried *all* of the "work-arounds" listed on this thread and none have helped. Also, it doesn't help if I log out and back in; I actually need to restart if I want anything (card reader, USB, etc.) to automount upon insertion. If anyone's got any other ideas on how to fix this, it'd be much appreciated!

---

### Post by swdinesh on 2009-12-08
this your workaround is still working?

My usb pens sometimes automount themselves and sometime they don´t :(
If your workaround is still working i can try for my system too
alex

---

### Post by joshzam on 2009-12-18
I performed a clean install of Karmic in the hopes that this would be solved but I'm still experiencing the same problem. Why, after a successful mount of any inserted USB device or memory card, would all subsequent devices and cards fail to automount? Anyone??

---

### Post by carnagex420x on 2009-12-27
I GOT IT! When I did a new install and deleted the bluetooth stuff, one of the dependencies was gvfs-backends, which installs obex-data-server and some other one idk atm. AFTER A RESTART it worked. I didnt have an unmounted cdrom0 in nautilus anymore either.

---

### Post by Iskendar on 2009-12-31
I'm running a minimal (gnomeless) karmic install with xbmc on my htpc, and I can't get usb disks to automount. I tried granting mounting rights to the xbmc user: 
```
sudo polkit-auth --user xbmc --grant org.freedesktop.hal.storage.mount-removable
sudo polkit-auth --user xbmc --grant org.freedesktop.hal.device.volume
```
No avail. I can mount usb disks or sticks manually, no problem there. 
Since I'm trying to keep this system minimal, I'd love to know how to set this up without having to add gnome-mount or any gui-based systems. Any ideas?

---

### Post by joshzam on 2010-01-12
I think I figured it out. I always chose to "Safely remove drive" as opposed to "Unmount" or "Eject". It took me a very long time to learn the difference between these and I suffered for a long time. I have an internal multi-card reader with a built-in USB port. After I was finished with either a media card or a USB device, I would choose "Safely remove drive". WRONG! This was actually turning off the power to the entire card reader and I was unable to subsequently mount any other cards or USB devices until I did a reboot! I acknowledge that this action is sometimes desired, but this was not what I was expecting given the "friendly" description. Let's hope they see the error of their ways and come up with a more intuitive way of performing these actions.

---

### Post by cmcanulty on 2010-05-23
I've had a constant hassle with things not mounting. But today I tried something different and burned the iso for the puppy linux and ran it in live mode and presto all my USB drives mounted easily. Now is there a way to use that information to figure out what is screwed up in my Lucid install? By the way it was also not working properly in Karmic and Jaunty.

---

### Post by phuang on 2010-12-20
I found the same problem in maverick. I found the problem is because that I installed ubuntu 10.10 from USB disk. So ubuntu installer generate a wrong /etc/fstab. It uses /dev/sdb1 (my internal harddisk) as my root fs. But after installation, the harddisk's device file will be changed to (/dev/sda1).

When I fixed the wrong dev name in /etc/fstab, the problem does not happen anymore.

---

