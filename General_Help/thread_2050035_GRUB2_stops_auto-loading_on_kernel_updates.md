---
title: "GRUB2 stops auto-loading on kernel updates"
date: 2012-08-29
forum: General Help
---

### Post by derekcentrico on 2012-08-29
I'm running Ubuntu 12.04 x64.  For the past three months, the system will not automatically start-up.  GRUB2 hangs waiting for a selection.  This reoccurs every time I upgrade the kernel.

I checked to ensure that timeout settings were there so that it would load the preset default.  It still fails each time.

My only solution is to purge and reinstall GRUB2 after each kernel upgrade.  This is very much an annoyance.

Any advice on this matter would be great.

---

### Post by oldfred on 2012-08-30
Post this which should show where grub2 is reinstalling its boot loader. Really just need the one line on install_devices.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

Post this to see if something looks mis-configured. Grub will pause boot on errors on previous reboot. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by derekcentrico on 2012-08-30
> **oldfred said:**
> Post this which should show where grub2 is reinstalling its boot loader. Really just need the one line on install_devices.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

Post this to see if something looks mis-configured. Grub will pause boot on errors on previous reboot. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Thanks for the response.

Here's the output of the two commands above:
> root@HomeServer:/home/derek# sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-ST2000DL003-9VT166_6YD24NT8, /dev/disk/by-id/ata-ST3300822AS_5NF1MJDY, /dev/disk/by-id/ata-ST3300822AS_5NF1MJDY-part1, /dev/disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5804429
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
  grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
* grub-pc/install_devices_failed: true
  grub-pc/install_devices_disks_changed:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10

root@HomeServer:/home/derek# sudo grub-probe -t device /boot/grub
/dev/sdb1


Also, I started using Boot-repair.  It fixes the current installation by re-installing GRUB, but it does not offer a permanent resolution as the issue reoccurs when another kernel update is installed.

The problem isn't occurring right now as I already repaired this current kernel install to GRUB.  But, here's the output requested above from Boot-repair:  [http://paste.ubuntu.com/1176022/](http://paste.ubuntu.com/1176022/)

Any thoughts would be appreciated.

---

### Post by oldfred on 2012-08-30
It looks like you have it set to reinstall grub2 to three places?

This is mine:
```
* grub-pc/install_devices: /dev/disk/by-id/ata-SSD_G2_series_64GB_10000000000000000251

```

Yours:
```
* grub-pc/install_devices:  /dev/disk/by-id/ata-ST2000DL003-9VT166_6YD24NT8,  /dev/disk/by-id/ata-ST3300822AS_5NF1MJDY,  /dev/disk/by-id/ata-ST3300822AS_5NF1MJDY-[COLOR=Red]part1[/COLOR],  /dev/disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5804429
  
```

I did not even know it could have more than one entry. You only show two drives and one is gpt. It will only install correctly to a gpt drive if you have a bios_grub partition. So you really should only be installing to the sdb or 300GB drive.

This should reset it, choose just the 300GB drive:
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Then rerun to confirm that it only shows the 300GB drive.
sudo debconf-show grub-pc

---

### Post by derekcentrico on 2012-08-30
> **oldfred said:**
> It looks like you have it set to reinstall grub2 to three places?

This is mine:
```
* grub-pc/install_devices: /dev/disk/by-id/ata-SSD_G2_series_64GB_10000000000000000251

```

Yours:
```
* grub-pc/install_devices:  /dev/disk/by-id/ata-ST2000DL003-9VT166_6YD24NT8,  /dev/disk/by-id/ata-ST3300822AS_5NF1MJDY,  /dev/disk/by-id/ata-ST3300822AS_5NF1MJDY-[COLOR=Red]part1[/COLOR],  /dev/disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5804429
  
```

I did not even know it could have more than one entry. You only show two drives and one is gpt. It will only install correctly to a gpt drive if you have a bios_grub partition. So you really should only be installing to the sdb or 300GB drive.

This should reset it, choose just the 300GB drive:
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Then rerun to confirm that it only shows the 300GB drive.
sudo debconf-show grub-pc

Alright.  I ran the above command and used default (blank).  I selected only /dev/sdb.

Here's the output of the latter command:
> root@HomeServer:/home/derek# sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-ST3300822AS_5NF1MJDY
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
* grub-pc/install_devices_failed: true
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10


I'll have to wait for another kernel upgrade to see what goes wrong I guess, if it does it as usual.

---

### Post by oldfred on 2012-08-30
Looks better, hope that solves it.

---

### Post by derekcentrico on 2012-09-01
> **oldfred said:**
> Looks better, hope that solves it.

Unfortunately, it stopped working again.  It sits on the GRUB screen waiting for a selection.

>   grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-ST3300822AS_5NF1MJDY
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
* grub-pc/install_devices_failed: true
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10

Anyway, so I did what I always do at this point.  I used Boot Repair to fix it sort of.

Before repair, I generated the report:  [http://paste.ubuntu.com/1179815/](http://paste.ubuntu.com/1179815/)

After repair report can be found here:  [http://paste.ubuntu.com/1179819/](http://paste.ubuntu.com/1179819/)

---

### Post by oldfred on 2012-09-01
Do not know if the issue we are seeing with larger / (root) partitions may be an issue. Usually grub just does not work and a reinstall then does not work either. May also be related to BIOS settings. What are drives set to? Should be AHCI, not IDE.

The issue is on some hardware grub will not boot from large (over 100) GB / partitions when some of the boot files are low in hard drive and some high in hard drive. You now have that. But both boot script show that:

```
=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 148.515598297 = 159.467409408  boot/grub/core.img                             1
 170.278476715 = [COLOR=Red]182.835122176 [/COLOR] boot/grub/grub.cfg                             1
  11.834510803 = 12.707209216   boot/initrd.img-3.2.0-30-generic               1
  50.513412476 = 54.238363648   boot/vmlinuz-3.2.0-30-generic                  1
  11.834510803 = [COLOR=Red]12.707209216[/COLOR]   initrd.img                                     1
  50.513412476 = 54.238363648   vmlinuz                                        1


```We have used two solutions for that issue but again not sure if you have this or not. One is the small /boot at the beginning of the drive, or a smaller / (root) and separate /home or other data partition to use the rest of the space you want for Ubuntu.

You can test just by shrinking / to about 100GB since it has 67GB used. But I would not leave that much used or move some data from / to another partition. I use only 25GB for / but am very aggressive about moving data to other partitions.

---

### Post by derekcentrico on 2012-09-01
> **oldfred said:**
> Do not know if the issue we are seeing with larger / (root) partitions may be an issue. Usually grub just does not work and a reinstall then does not work either. May also be related to BIOS settings. What are drives set to? Should be AHCI, not IDE.

The issue is on some hardware grub will not boot from large (over 100) GB / partitions when some of the boot files are low in hard drive and some high in hard drive. You now have that. But both boot script show that:

```
=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 148.515598297 = 159.467409408  boot/grub/core.img                             1
 170.278476715 = [COLOR=Red]182.835122176 [/COLOR] boot/grub/grub.cfg                             1
  11.834510803 = 12.707209216   boot/initrd.img-3.2.0-30-generic               1
  50.513412476 = 54.238363648   boot/vmlinuz-3.2.0-30-generic                  1
  11.834510803 = [COLOR=Red]12.707209216[/COLOR]   initrd.img                                     1
  50.513412476 = 54.238363648   vmlinuz                                        1


```We have used two solutions for that issue but again not sure if you have this or not. One is the small /boot at the beginning of the drive, or a smaller / (root) and separate /home or other data partition to use the rest of the space you want for Ubuntu.

You can test just by shrinking / to about 100GB since it has 67GB used. But I would not leave that much used or move some data from / to another partition. I use only 25GB for / but am very aggressive about moving data to other partitions.

How would I create a new /boot/ partition without redoing my installation?  I haven't attempted such an activity before.

I could shrink the partition using GParted, but I'd prefer not to.

EDIT: Is this still valid for 12.04?  [https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)  Is there some better/easier method available now?

---

### Post by oldfred on 2012-09-01
LInk on creating /boot looks good.

You have to use gparted to shrink first partition enough for /boot - 200 to 300MB. Then move it right to create unallocated for the new /boot partition. Copy boot files/folders and edit fstab and reinstall grub2. 

I might just try shrinking / first and see if that helps. I am not a fan of separate /boot but in some cases they seem to be required. I prefer a smaller / (root) and separate /home or data partitions for user data.

---

### Post by derekcentrico on 2012-09-01
I'm attempting the shrink & move to the right activity now.  It's going to take a couple of hours it says...  This kind of makes me apprehensive.  I hope Linux data movement is a lot more stable than ole MicroSoFt.

---

### Post by oldfred on 2012-09-01
The more data you  have and the large the partition the longer it takes. As long as there are no power failures or other interruptions, you should be fine.

Of course good backups before any major change is a good idea. (Day late and dollar short with this reminder).

---

### Post by derekcentrico on 2012-09-02
Well it took about 6 hours to do the partition shrink and move to the right.  That worked fine.

Following, I did the above procedure to create the boot partition and copy the files.  It booted the first time around, but stopped booting doing the maintenance to remove the original /boot/ directory.

I was receiving this error in Grub2:
> error: file not found 
you need to load the kernel first

I booted the Live CD again and installed boot-repair.  After going through that process the system is now back online with the boot partition only.  The boot repair log is available at [http://paste.ubuntu.com/1180833/](http://paste.ubuntu.com/1180833/).

Time will tell if this resolves it.  We'll see with the next apt kernel update...

---

### Post by derekcentrico on 2012-09-03
Unfortunately, the problem reappeared this morning.  The RTC timer didn't bring it back from sleep, so I powered on the monitor to see it stuck at the GRUB2 menu.

Here's the Bootinfo before running the repair:  [http://paste.ubuntu.com/1183725/](http://paste.ubuntu.com/1183725/)

And, here's the Bootinfo after running the "recommended repair" option:
[http://paste.ubuntu.com/1183727/](http://paste.ubuntu.com/1183727/)

Any thoughts out there?

---

### Post by oldfred on 2012-09-03
You have this:

Before:
  set timeout=-1
And the other has this:
set timeout=10

The timeout at -1 is set to keep grub menu until you click on something. The other is the standard 10 sec timeout.

Not sure if boot repair changed it or did you?

Are you having Boot-Repair only reinstall to sdb?

It looks like boot repair ran an update and system is saying to uninstall some nVidia files. Are you using nVidia?

---

### Post by derekcentrico on 2012-09-03
> **oldfred said:**
> You have this:

Before:
  set timeout=-1
And the other has this:
set timeout=10

The timeout at -1 is set to keep grub menu until you click on something. The other is the standard 10 sec timeout.

Not sure if boot repair changed it or did you?

Are you having Boot-Repair only reinstall to sdb?

It looks like boot repair ran an update and system is saying to uninstall some nVidia files. Are you using nVidia?

I haven't manually set anything such as the timeout above.  I've only used Boot Repair to do the work since this thread began and about a month prior as well.

I did the recommended repair which didn't allow me to select any extra options this time.  Normally, I do the Advanced and make sure it's SDB as per your information above.

I do have an nVidia graphics card and I'm sure that some of their drivers are installed as I was playing with it as a media center back in May...

---

### Post by YannBuntu on 2012-09-03
Hello

> **derekcentrico said:**
> And, here's the Bootinfo after running the "recommended repair" option:
[http://paste.ubuntu.com/1183727/](http://paste.ubuntu.com/1183727/)

After this, what do you observe at reboot? do you see the GRUB menu?


> **oldfred said:**
> Not sure if boot repair changed it or did you?

 here is the default in GRUB:
```
  set timeout=-1
else
  set timeout=10
```

The "Unhide boot menu: X seconds" option of B-R forces these values to:

```
  set timeout=X
else
  set timeout=X
```

So that we are sure the GRUB menu is not hidden by the "-1" (there was an old bug about it in 10.04, i think it has been solved since, but i keep this workaround in B-R for fixing 10.04 installs).

> **oldfred said:**
> Are you having Boot-Repair only reinstall to sdb?


If you look at the bottom of the 2nd URL, you will see:
```
**Reinstall the GRUB of sdb1 into the MBR of sda**
grub-install (GRUB) 1.99-22ubuntu1
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.
grub-install --recheck /dev/sda: exit code of grub-install /dev/sda:1

**Reinstall the GRUB of sdb1 into the MBR of sdc**
grub-install (GRUB) 1.99-22ubuntu1
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.
grub-install --recheck /dev/sdc: exit code of grub-install /dev/sdc:1

**Reinstall the GRUB of sdb1 into the MBR of sdb**
grub-install (GRUB) 1.99-22ubuntu1
grub-install --recheck /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0
```

install fails in sda and sdc, that's why their MBR haven't changed:
```
 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.
```

(remark: B-R executes BIS at the very end of its operations, but its output is displayed at the beginning of the Boot-Info URL)

---

### Post by derekcentrico on 2012-09-03
> **YannBuntu said:**
> Hello
After this, what do you observe at reboot? do you see the GRUB menu?

The reboot went just fine after doing the above repair.  I've rebooted four times now just for the heck of it.  Each time it does the 10 seconds countdown and then loads the default option.

This is normally what happens.  But at some point, it would lose its settings and would just hang on the GRUB menu until a selection is made.  As above, I found it to be related to new kernel update releases and after they were installed.  

Per instructions, I made a /boot/ partition and moved to it yesterday so that the boot files weren't split so far apart in the harddrive.  This didn't win the game as of yet...

---

### Post by oldfred on 2012-09-03
If it does not boot again, use liveCD or after you get it to boot look at log files. You want to find the one that did not work and see if something was recorded. I look at dmesg first but there are many log files. I look for errors, driver not loading and error message, repeated trys at loading something or very long times between entries.

If booted you can use Log File Viewer. It may help to look at current log files to see if anything is reported, but by-passes it and then does work.

---

### Post by YannBuntu on 2012-09-03
The diff between the 2 logs is very small. It's just:

```
=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.157279968 = 0.168878080    grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1
```

and
```
set timeout=-1
```
Next time you get the problem:
- gather the files asked by OldFred,
- then replace "timeout=-1" by "timeout=10" in sdb3/grub/grub.cfg, and check if it fixes the problem

---

### Post by derekcentrico on 2012-09-03
> **YannBuntu said:**
> The diff between the 2 logs is very small. It's just:

```
=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.157279968 = 0.168878080    grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1
```

and
```
set timeout=-1
```
Next time you get the problem:
- gather the files asked by OldFred,
- then replace "timeout=-1" by "timeout=10" in sdb3/grub/grub.cfg, and check if it fixes the problem

Will do the above and report at the next instance which I assume will happen eventually...

While we wait, is it an issue that the above grub.cfg is listed as "??" in the first column?  Like, it didn't exist?  Currently, I do see it in the /boot/grub/ path as it should be.

---

### Post by derekcentrico on 2012-10-06
> **derekcentrico said:**
> Will do the above and report at the next instance which I assume will happen eventually...

While we wait, is it an issue that the above grub.cfg is listed as "??" in the first column?  Like, it didn't exist?  Currently, I do see it in the /boot/grub/ path as it should be.

Unfortunately, this occurred again.  It happened after it went to sleep just past midnight on 29 September.  I'm out of town and had to wait for someone to swing by and boot it up again for me.  It was hung on the Grub bootloader.  They rebooted it and it would stay on the Grub bootloader awaiting a command to proceed with the selection.

The only thing I did was update a bunch of packages with apt-get a few hours before this point so that it would be fully updated before leaving.

I reviewed all the log files in /var/log/ that had anything written to them 28 September or 05 October (when it was rebooted for me)...  Nothing popped out as an error whatsoever.  

I changed the -1 to 10:
> terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi

I guess now it's time to wait to see if this affects anything.

---

### Post by derekcentrico on 2012-10-23
Even with 12.10 installed, the issue persists.

Here are the Boot-Repair logs:
before repair - [http://paste.ubuntu.com/1300086/](http://paste.ubuntu.com/1300086/)
after repair - [http://paste.ubuntu.com/1300090/](http://paste.ubuntu.com/1300090/)

However, this time the standard Boot Repair did not resolve it.  This is the first time I used Boot Repair with 12.10 and the first time it has failed to resolve the GRUB issue.

Again, the system freezes on the GRUB bootloader and will not proceed to auto-load as it used to do and should do.

---

### Post by YannBuntu on 2012-10-23
Hi
Some new problems appeared with 12.10 (which includes GRUB2.00).
Please try Boot-Repair --> Advanced options --> GRUB options tab --> tick "GRUB Legacy" --> Apply
Tell us the new URL that will appear. Reboot and tell us what you observe.

---

### Post by derekcentrico on 2012-10-23
> **YannBuntu said:**
> Hi
Some new problems appeared with 12.10 (which includes GRUB2.00).
Please try Boot-Repair --> Advanced options --> GRUB options tab --> tick "GRUB Legacy" --> Apply
Tell us the new URL that will appear. Reboot and tell us what you observe.

Prior to the above response, I temporarily resolved the matter by using Grub Customizer to re-enable the timeout period and to set what to boot.

Now, I've completed the Legacy Grub instructions.  The information link provided is:  [http://paste.ubuntu.com/1300585/](http://paste.ubuntu.com/1300585/)

The reason this is such a pain is that I have the system set to automatically go into sleep mode with the sleep data written to the hard-drive rather than into memory every evening.  It automatically wakes up in the morning.  So, it keeps losing its setting and just sits on the Grub screen until someone physically presses a key to load.

---

### Post by YannBuntu on 2012-10-23
> **derekcentrico said:**
> I've completed the Legacy Grub instructions.  The information link provided is:  [http://paste.ubuntu.com/1300585/](http://paste.ubuntu.com/1300585/)

Can you boot Ubuntu now?

---

### Post by derekcentrico on 2012-10-23
> **YannBuntu said:**
> Can you boot Ubuntu now?

Yes, Ubuntu is booting fine at the moment.

I'm skeptical that it'll last.  The next kernel update, or update that modifies anything related to boot-up, will probably kick me back down in the dirt.  :(

---

### Post by YannBuntu on 2012-10-23
It shouldn't break now.
But you should report the bug ( [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug) ) , else you will have the same problem with next Ubuntu versions.

---

### Post by derekcentrico on 2012-10-23
Any suggestion on what exactly to report?

I have no clue what's going on except that Boot Repair is needed to get it to auto boot.  I guess the use of Grub Customizer indicates that it's either the loss of the timeout setting or unable to select Ubuntu to boot...

But, I'm ignorant on this.

EDIT:  I reported what I could.  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1070534](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1070534)

---

### Post by YannBuntu on 2012-10-23
The problem is that we don't have your Boot-Info after you used GRUB-Customizer, so we don't know what it did exactly.

If i were you, i would:
1) reinstall GRUB2 (via Boot-Repair --> Recommended Repair), check if you can reproduce the bug and its fix, if yes report it.
2) Then reinstall GRUB Legacy the same way you did before.

---

### Post by derekcentrico on 2012-10-23
> **YannBuntu said:**
> The problem is that we don't have your Boot-Info after you used GRUB-Customizer, so we don't know what it did exactly.

If i were you, i would:
1) reinstall GRUB2 (via Boot-Repair --> Recommended Repair), check if you can reproduce the bug and its fix, if yes report it.
2) Then reinstall GRUB Legacy the same way you did before.

Yeah, sorry about the G.C. issue.  I had to get the thing working again so I'd be out of the dog house.

I'll do those steps if, "once," it starts screwing up again.  Give it a week or two to see me reporting back.  I'm sure some update will be out that touches upon the boot area.

---

### Post by derekcentrico on 2012-12-08
Well, it happened again today.

The problem is most certainly the grub.cfg reverts back to:

> set timeout=-1
else
set timeout=10

Where "set timeout=-1" causes the problem.

I'm uncertain why this keeps happening.  Anyway, changing it to set "timeout=10" resolves it temporarily until some update redoes the grub.cfg.

---

### Post by YannBuntu on 2012-12-10
thanks for the feedback!

---

### Post by derekcentrico on 2012-12-10
> **YannBuntu said:**
> thanks for the feedback!

No worries.  Also as a note, I can confirm that at least twice Boot Repair did not resolve my problem including this last time.  I manually changed that variable.

Not sure what the hang up is or whatever, but it would be cool if Boot Repair would be able to check for and replace a -1 should it be in existence.

---

### Post by YannBuntu on 2012-12-10
By default, Boot-Repair systematically replaces the -1 by 10 (or the value the user chooses for the "Unhide boot menu" option)

[http://pix.toile-libre.org/upload/img/1335263156.png]("http://pix.toile-libre.org/upload/img/1335263156.png")

If it doesn't, that's a bug, and you can help me fixing it by telling me the log where it failed.

---

### Post by derekcentrico on 2012-12-10
> **YannBuntu said:**
> By default, Boot-Repair systematically replaces the -1 by 10 (or the value the user chooses for the "Unhide boot menu" option)

[http://pix.toile-libre.org/upload/img/1335263156.png]("http://pix.toile-libre.org/upload/img/1335263156.png")

If it doesn't, that's a bug, and you can help me fixing it by telling me the log where it failed.

Allright.  I didn't save the link to the output honestly.  Normally I do, but didn't think to.  Are they stored somewhere locally as well?  I can grab it for you that way.

I don't mind helping out.  ;)

---

### Post by YannBuntu on 2012-12-11
you can find the log history via Boot-Repair --> Advanced options --> "Backup partitions tables..." button --> save the ZIP somewhere --> attach the ZIP to your reply.

---

### Post by derekcentrico on 2012-12-11
> **YannBuntu said:**
> you can find the log history via Boot-Repair --> Advanced options --> "Backup partitions tables..." button --> save the ZIP somewhere --> attach the ZIP to your reply.

The file's way too large for this place at 3.3MB.

I'm emailing it to you at the boot.repair address.

---

### Post by YannBuntu on 2012-12-12
Thank you!
Your log confirms the bug. 
I created a bug report: [https://bugs.launchpad.net/boot-repair/+bug/1089646](https://bugs.launchpad.net/boot-repair/+bug/1089646)
I'll try to fix it asap.

---

### Post by derekcentrico on 2012-12-12
> **YannBuntu said:**
> Thank you!
Your log confirms the bug. 
I created a bug report: [https://bugs.launchpad.net/boot-repair/+bug/1089646](https://bugs.launchpad.net/boot-repair/+bug/1089646)
I'll try to fix it asap.

Glad I could be somewhat useful.  :p

---

### Post by derekcentrico on 2012-12-24
This has just gotten crazy.

For the past six days, the grub.cfg reverts to -1 every other day.  So, the system does not wakeup from suspend every other day.

No updates are being installed at all.  It just randomly changes.  I cannot figure out what the heck is going on.

Any thoughts?

---

