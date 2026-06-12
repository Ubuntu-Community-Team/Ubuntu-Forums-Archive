---
title: "Raid array does not auto start/auto mount"
date: 2010-05-01
forum: General Help
---

### Post by teeedubb on 2010-05-01
Hey all
Ive searched high and low for a solution to this problem but havent been able to solve it so I though i'd post here.

On boot I get a screen stating 'the disk for/mnt/md0 is not ready yet or not  present. Continue to wait; or Press S to skip mount or M for manual recover'. If i press M and try 'mount -a' it states that 'special device  /dev/md0 does not exist'. If I try 'mdadm --assemble --scan' it states  'no devices found for /dev/md0'. If I skip the mounting of the array,  and start the array then mount it through palimpset everything mounts as  should be (devices in array and mount location).

Some information:

server@server:~$ sudo mdadm -D -s
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=01.02 name=:raid5 UUID=02bcfe3b:44fc949f:f5f7e481:a421a2c0

/etc/mdadm/mdadm.conf

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR server

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 metadata=1.2 num-devices=4 UUID=02bcfe3b:44fc949f:f5f7e481:a421a2c0 name=md0

# This file was auto-generated on Sat, 01 May 2010 18:15:04 +1000
# by mkconf $Id$

/etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=906694f9-9425-4ae3-88cc-bd9f4161846b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=01cb5d34-e4ac-4329-95c1-e9396a414a28 none            swap    sw              0       0
#mdadm array
/dev/md0    /mnt/md0    auto    defaults    0    0

I have tried editing the mdadm.conf using this [thread]("http://georgia.ubuntuforums.org/showthread.php?p=8485557"),but the problem still persists.

Any suggestions?

EDIT: Im running ubuntu 10.04 with all updates installed.

---

### Post by coffee412 on 2010-05-01
Hi from 10.04 land!

Im not going to be alot of help but I have run into the same problem. In order for me to mount my raid I have to manually do it.

sudo mount -t ext3 /dev/md0 /mnt/raid

My fstab entry does not work and gives me the following error:

> sandy@sandy-desktop:/etc$ sudo mount /dev/md0
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or soManually mounting the raid works fine. But not thru fstab for some reason. Hopefully they can fix this soon. Its not pretty to manually have to mount the raid.

More info:
> sandy@sandy-desktop:/etc$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Apr 30 13:28:30 2010
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat May  1 10:16:39 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f00cb7c7:325e1ad0:e1af99e9:92c82b1d
         Events : 0.55

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
coffee

---

### Post by teeedubb on 2010-05-01
coffee412: So is your raid array being started automatically? Is the only problem that you have is that its not being mounted? Mine isnt being started during boot, so Im not sure if its a fstab or mdadm.conf issue, though both seem to be correct.

---

### Post by teeedubb on 2010-05-05
I have posted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/573477") as the same is happening on another machine with a raid array, although its a raid 0 array. As I posted in the bug report, I noticed this during the installation of mdadm on the new machine:

> Setting up mdadm (2.6.7.1-1ubuntu15) ...
Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst:  170: /dev/MAKEDEV: not found
failed.
Generating mdadm.conf... done.
 Removing any system startup links for /etc/init.d/mdadm-raid  ...
Could this have something to do with the array not starting?
 Here is the complete transcript of the install:
 

> The following NEW packages will be installed:
  mdadm postfix
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,642kB of archives.
After this operation, 4,248kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main mdadm 2.6.7.1-1ubuntu15 [239kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)  lucid/main postfix 2.7.0-1 [1,403kB]
Fetched 1,642kB in 8s (200kB/s)
Preconfiguring packages ...
Selecting previously deselected package mdadm.
(Reading database ... 149165 files and directories currently installed.)
Unpacking mdadm (from .../mdadm_2.6.7.1-1ubuntu15_amd64.deb)  ...
Selecting previously deselected package postfix.
Unpacking postfix (from .../postfix_2.7.0-1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 26 changed 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up mdadm (2.6.7.1-1ubuntu15) ...
Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst:  170: /dev/MAKEDEV: not found
failed.
Generating mdadm.conf... done.
 Removing any system startup links for /etc/init.d/mdadm-raid  ...
update-initramfs is disabled since running on read-only media
update-rc.d: warning: mdadm start runlevel arguments (2 3 4 5) do not  match LSB Default-Start values (S)
update-rc.d: warning: mdadm stop runlevel arguments (0 1 6) do not match  LSB Default-Stop values (0 6)
 * Starting MD monitoring service mdadm --monitor                         [ OK ]
 Setting up postfix (2.7.0-1) ...
Adding group `postfix' (GID 123) ...
Done.
Adding system user `postfix' (UID 115) ...
Adding new user `postfix' (UID 115) with group `postfix' ...
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (GID 124) ...
Done.
setting myhostname: ubuntu
setting alias maps
setting alias database
mailname is not a fully qualified domain name.  Not changing  /etc/mailname.
setting destinations: ubuntu, localhost.localdomain, , localhost
setting relayhost:
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104  [::1]/128
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
/etc/aliases does not exist, creating it.
WARNING: /etc/aliases exists, but does not have a root alias.
 Postfix is now set up with a default configuration.  If you need to  make
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix  configuration
values, see postconf(1).
 After modifying main.cf, be sure to run '/etc/init.d/postfix  reload'.
 Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                          [ OK ]
 * Starting Postfix Mail Transport Agent postfix                          [ OK ]
 Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$


---

### Post by teeedubb on 2010-05-11
Any ideas?

---

### Post by frente69 on 2010-05-12
same issue here with my raid 0 array. I'm suspecting it is an issue with the 10.04 upgrade(as it happened right after i did the upgrade and rebooted). 
Double checked my fstab and mdadm.conf and both seem fine yet for some reason when i reboot ubuntu server it says unable to mount and waits for me to press s to continue or another key to drop to shell. 

When i run mdadm --assemble --scan creates the /dev/md0 device and when i run mount /dev/md0 /mnt/raid it all mounts as it should.
 just not at bootup like normal.

Just tried apt-get remove mdadm and then apt-get install mdadm,..didn't fix it...

---

### Post by john newbuntu on 2010-05-12
Did any of you try pasting the complete string output of the following command that starts with the word "ARRAY" into mdadm.conf:
sudo mdadm -D -s
[FONT=Verdana]or
[/FONT][FONT=Verdana]sudo mdadm --detail --scan[/FONT]

I noticed a slightly different name and metadata superblock information in mdadm.conf.  Not sure on whether that info is required given the UUID.  But try keeping things simple.

---

### Post by Outbreak Monkey on 2010-05-20
> **frente69 said:**
> same issue here with my raid 0 array. I'm suspecting it is an issue with the 10.04 upgrade(as it happened right after i did the upgrade and rebooted). 
Double checked my fstab and mdadm.conf and both seem fine yet for some reason when i reboot ubuntu server it says unable to mount and waits for me to press s to continue or another key to drop to shell. 

When i run mdadm --assemble --scan creates the /dev/md0 device and when i run mount /dev/md0 /mnt/raid it all mounts as it should.
 just not at bootup like normal.

Just tried apt-get remove mdadm and then apt-get install mdadm,..didn't fix it...
--
I think this seems a different issue to the original post maybe? BUT I had similar issues because my /etc/mdadm/mdadm.conf file was still there...

Did you try to delete the file: sudo rm /etc/mdadm/mdadm.conf

then run: sudo dpkg-reconfigure mdadm (no need to uninstall/reinstall)

It should re-create /etc/mdadm/mdadm.conf 

AND should spew some messages about running update-initramfs (I don't know but it seem to use the content of mdadm.conf when building the initrd.img - can anyone confirm?)

I also found I had problems with using UUIDs in the mdadm.conf - it grabbed the device for the raid instead of the partition, so for me what finally worked is setting the content of mdadm.conf to:

ARRAY /dev/md0 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1
the same devices as I used for the create (instead of UUIDs)

THEN again ran: sudo dpkg-reconfigure mdadm
(this time because you have a valid /etc/mdadm/mdadm.conf - it does NOT get recreated, but the settings seem to be used for the initrd.img).

Now everything's coming up Millhouse for me..

Hope this helped someone - and if anyone can explain why mdadm grabs the device instead of the partition (when using UUIDs), I'd appreciate it!

Cheers,
ObM.

---

### Post by HRH_H_Crab on 2010-06-07
Its not working for me.
I've deleted the mdadm.conf recreated with dpkg-reconfigure, and I've replaced the UUIDs with device names.

On reboot the array shows as: "not running - partially assembled".

Stopping and starting it in the gui works fine, and no disks are showing as having any problems.

Any ideas?

---

### Post by HRH_H_Crab on 2010-06-07
As an aside I have two machines using RAID:

One is a raid 5 machine (array originally created under gentoo).
This one works fine. The machine is running 10.04. (metadata 0.9) 

The other machine is raid 1, it was freshly created on the previous (i forget?) ubuntu but was then upgraded to 10.04. This is the one that fails to assemble on boot. (metadata 1.2).

I noticed problems started almost immediately after upgrading to 10.04.

---

### Post by Outbreak Monkey on 2010-06-07
> **HRH_H_Crab said:**
> Its not working for me.
I've deleted the mdadm.conf recreated with dpkg-reconfigure, and I've replaced the UUIDs with device names.

Any ideas?

I had to fiddle around quite a bit to get it to work on boot, the process I followed was:
Blow away mdadm.conf, dpkg-reconfigure, EDIT the mdadm.conf to get the devices in the right order using device names etc... THEN _dpkg-reconfigure again_ (this seems to do the initramfs  update stuff using the content of mdadm.conf)..

I might add, mine is a Raid 5 array. I don't know if we're having the same problem, but I do know I had to muck around a little and it wasn't quite intuitive.

Cheers,
ObM.

---

### Post by HRH_H_Crab on 2010-06-08
Thanks.
I got there in the end basically doing what you said.
I had to do considerable hand editing of mdadm.conf, basically removing nearly everything.

The final line was: ARRAY /dev/md0 level=raid1 metadata=1.2 num-devices=2 devices=/dev/sdb1,/dev/sdc1

And there were still strange errors on doing dpkg-reconfigure mdadm to do with the run levels. :/
Anyway hopefully this saves someone else some stress.

---

### Post by pablopas on 2010-07-08
Hi Fellows!

I had the same problem and solved allright by adding the following lines in the /etc/mdadm/mdadm.conf

```

DEVICE /dev/sda1 /dev/sdc1
ARRAY /dev/md0 level=raid0 devices=/dev/sda1,/dev/sdc1

```

Regards,

Pablo

---

### Post by bosschops on 2010-07-18
I found that the process in this thread (namely create array either via mdadm or disk manager gui, manually add details to mdadm.conf, dpkg-reconfigure mdadm, reboot) accomplishes getting the array to 'start' on boot up, which is a good thing, but not to be available for fstab mounting.  The array's filesystem, however, can be mounted manually after bootup.

I have ubuntu booting from a non-raid drive sda, and sdb and sdc are the raid 1 array I am working on.

I wonder if this is a sequence problem, fstab before array startup or something like that.

---

### Post by Outbreak Monkey on 2010-07-19
> **bosschops said:**
> I found that the process in this thread ... ... accomplishes getting the array to 'start' on boot up, which is a good thing, but not to be available for fstab mounting.  The array's filesystem, however, can be mounted manually after bootup.

I have ubuntu booting from a non-raid drive sda, and sdb and sdc are the raid 1 array I am working on.

I wonder if this is a sequence problem, fstab before array startup or something like that.

I don't really know the inner workings of linux's boot process, but I have no problem with this, my raid and lvm seem to be up long before fstab is scanned.

What does your dmesg say?

Mine results in lots of spam but these two lines:
```

# dmesg | grep -E 'md:|raid'
...
[    2.830075] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
[    2.880444] raid5: raid level 5 set md1 active with 3 out of 3 devices, algorithm 2
...

```
Mean that the raid is up relatively early in the boot process, where as fstab seems to be scanned around 20 seconds later when my EXT partitions are loaded.
```

# dmesg | grep EXT
...
[   24.480814] EXT3 FS on dm-0, internal journal
[   24.480821] EXT3-fs: mounted filesystem with ordered data mode.
[   24.860944] EXT3 FS on dm-1, internal journal
[   24.860950] EXT3-fs: mounted filesystem with ordered data mode.
...

```
(I assume the dm-0 is because lvm uses device mapper or something?)

You can check the timing of the raid start, and the mounting of the filesystems by checking through dmesg's output (as above).

Also, what does your fstab look like? are you using UUIDs or device names in your fstab maybe that makes a difference, though I don't know why it should.

Cheers,
ObM.

---

### Post by bosschops on 2010-07-19
Good idea- I see what I believe is the array becoming active after fstab does its work:  fstab actions around 10 and raid activation around 11.  I'll experiment with fstab a bit after some sleep - currently using device name not UUID.


 dmesg | grep ext
...
[   10.244759] Adding 5658616k swap on /dev/sda5.  Priority:-1 extents:1 across:5658616k


 sudo dmesg | grep raid
[    1.310921] md: raid0 personality registered for level 0
[    1.333587] md: raid1 personality registered for level 1
[    2.144072] raid6: int32x1    814 MB/s
[    2.212040] raid6: int32x2    800 MB/s
[    2.280115] raid6: int32x4    500 MB/s
[    2.348030] raid6: int32x8    377 MB/s
[    2.416025] raid6: mmxx1     1487 MB/s
[    2.484027] raid6: mmxx2     2614 MB/s
[    2.552018] raid6: sse1x1    1012 MB/s
[    2.620009] raid6: sse1x2    1552 MB/s
[    2.688041] raid6: sse2x1    1623 MB/s
[    2.756018] raid6: sse2x2    2288 MB/s
[    2.756020] raid6: using algorithm sse2x2 (2288 MB/s)
[    2.773685] md: raid6 personality registered for level 6
[    2.773689] md: raid5 personality registered for level 5
[    2.773692] md: raid4 personality registered for level 4
[    2.786005] md: raid10 personality registered for level 10
[   11.556045] raid1: raid set md0 active with 2 out of 2 mirrors

---

### Post by pablopas on 2010-07-19
The Fstab line is very simple:

UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd	/media/raid	ext4	defaults	0	1

When your UUID is replacing /dev/md0, then the mounting point, and the file system type,etc.

You can find your UUID by doing "sudo blkid"

---

### Post by bosschops on 2010-07-19
Thanks for the helpful tips, lead me down the correct path - I ended up with the entry below in fstab:

/dev/md0p1 /media/raid1storage etx4 default 0 1

changing to the UUID for the array instead of device name option  I got 'serious errors checking filesystem' on bootup, and it didnt mount, but the device name above works like a champ.  It would be a treat if the gui 'Disk Utility' in 10 lts would write out to fstab for you!  (and load the mdadm conf into initd)

---

### Post by ttguy on 2010-09-09
I had the same issue with the screen stating 'the disk for/mnt/md0 is not ready yet or not present. Continue to wait; or Press S to skip mount or M for manual recover'

But thanks to the suggestions in the Outbreak Monkey [post]("http://ubuntuforums.org/showpost.php?p=9334317&postcount=8") I got it working. This ARRAY line in  /etc/mdadm/mdadm.conf  worked for me.


```
    
ARRAY /dev/md0 level=raid1 metadata=1.2 num-devices=2 devices=/dev/sdb1,/dev/sdc1 name=:RAIDArray1

```And after doing a sudo blkid to find the UUID of my new raid array I set up
  /etc/fstab to have
```

UUID=ae5f4540-59af-4e7a-84b0-ea97cc12e425  /Raid500    ext3          nodev,nosuid       0       2

```And now it is fixed. Nice

---

### Post by Santa_Claus on 2010-10-06
Hi,
Thank you for a great discussion and found that this is the best thread for me with my RAID 1+0 (RAID 10) challenge. 

I  setup new desktop machine with one 64G SSD drive, where my root  filesystem has been installed. Then I have 4x1TB drives for RAID 1+0  installation. Installation Kubuntu 10.10 went very smoothly, but when I  come to part where should I test RAID 1+0 storage I found problems. -  now spend 4 days try to solve this :)
    
Well my test is very simple - when desktop is power off I pull off  one drive's power cable. When booting I get errors "Continue to wait; or  Press S to skip mount or M for manual recovery"

### My mdadm.conf in the begining ###
    ============
DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
ARRAY /dev/md0 level=raid10 num-devices=4 metadata=00.90 UUID=396ffbe1:d0f2c182:4e3f7228:c54412eb

 ### I get errors when dpkg-reconfigure ####
 userx# dpkg-reconfigure mdadm
 * Stopping MD monitoring service mdadm --monitor                                                                                                                       [ 
Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst: 170: /dev/MAKEDEV: not found failed.
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
mdadm: metadata format 00.90 unknown, ignored.
update-rc.d: warning: mdadm start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (S)
  update-rc.d: warning: mdadm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
 * Starting MD monitoring service mdadm --monitor                                 mdadm: metadata format 00.90 unknown, ignored.
  
### when one drive power off ###
#blkid
dev/sda1: UUID="8b6bf1d4-aa06-4723-b92d-5d45d4711400" TYPE="ext4" 
/dev/sda2: UUID="9ef1a2d6-b34f-4928-be77-ff25568267cd" TYPE="ext4" 
 /dev/sdb1: UUID="396ffbe1-d0f2-c182-4e3f-7228c54412eb" TYPE="linux_raid_member" 
/dev/sdc1: UUID="396ffbe1-d0f2-c182-4e3f-7228c54412eb" TYPE="linux_raid_member" 
/dev/sdd1: UUID="396ffbe1-d0f2-c182-4e3f-7228c54412eb" TYPE="linux_raid_member" 
 
### When all drives power on ###
#blkid
/dev/sda1: UUID="396ffbe1-d0f2-c182-4e3f-7228c54412eb" TYPE="linux_raid_member" 
/dev/sdc1: UUID="396ffbe1-d0f2-c182-4e3f-7228c54412eb" TYPE="linux_raid_member" 
/dev/sdb1: UUID="396ffbe1-d0f2-c182-4e3f-7228c54412eb" TYPE="linux_raid_member" 
/dev/sdd1: UUID="396ffbe1-d0f2-c182-4e3f-7228c54412eb" TYPE="linux_raid_member" 
/dev/sde1: UUID="8b6bf1d4-aa06-4723-b92d-5d45d4711400" TYPE="ext4" 
/dev/sde2: UUID="9ef1a2d6-b34f-4928-be77-ff25568267cd" TYPE="ext4" 
/dev/md0: UUID="88f3e3fa-c8f2-4941-bbbe-a57372d1ed17" TYPE="ext4"

### /etc/fstab ###
UUID=88f3e3fa-c8f2-4941-bbbe-a57372d1ed17 /faststorage ext4    defaults        0       2

### My mdadm.conf in the end of this ###

DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 level=raid10 num-devices=4 UUID=396ffbe1:d0f2c182:4e3f7228:c54412eb

I have tested all what suggested earlier in this thread.
- Deleted mdadm.conf and generate new one with "BOOT_DEGRADED=false" to "BOOT_DEGRADED=true"
- Changed UUID and device names to /dev/sdxx
- Installed RAID two times from beginning
- Changed /etc/fstab file few times
- booted xxx times :)

Any ideas how to solve this - thanks a LOT?

---

### Post by Outbreak Monkey on 2010-10-06
Hi Santa_Claus,

I can see you're using UUIDs.  UUIDs should work just fine, But for some reason, I had all sorts of dramas using them. But as you say, you've tried device names as well..

Need some more info about the array, can you post the content of:
```
cat  /proc/mdstat
```
(paste the output of mdstat when your raid is running vs when it's degraded..)

Also, as a test, can you start the array degraded from the command line with something like:
either:
```

mdadm --assemble --force --scan /dev/md0
or
mdadm --assemble --force /dev/md0 /dev/sd[bcd] 

```

Might also be handy to get the raid specific secitons from dmesg (copy and paste them  somewhere).
```

dmesg

``` 

Cheers,
ObM.

---

### Post by manus_eiffel on 2010-10-11
I had a similar problem and the blkid helped me figured out what was wrong. Before ubuntu 10.04 my raid was /dev/sda1 to /dev/sdd1 and my root partition was /dev/sde1. After the upgrade, looks like that my /dev/sde1 was now known as /dev/sda1 and all the names had been shifted.

I edited my mdadm.conf file and manually specify the DEVICES and enumerated them in the ARRAY line. After that it booted just fine.

---

### Post by Santa_Claus on 2010-10-14
Thanks Outbreak Monkey, here are the output of what you ask:

### Raid 1+0 running ###
# cat /proc/mdstat 
Personalities : [raid10] [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] 
md0 : active raid10 sdd1[3] sdc1[2] sdb1[1] sda1[0]
      1953519872 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
unused devices: <none>

### RAID 1+0 degraded ###

#cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2](S) sdb1[0](S) sdc1[1](S)
      2930279808 blocks
       
unused devices: <none>

### RAID 1+0 degraded - manually start the array, looks working fine and mount the array and all content is there ###

#mdadm --assemble --force --scan /dev/md0
mdadm: /dev/md0 has been started with 3 drives (out of 4).


### RAID 1+0 degraded - dmesg###
# dmesg | grep raid
[    3.296855] device-mapper: dm-raid45: initialized v0.2594b
[    3.302700] md: raid0 personality registered for level 0
[    3.304759] md: raid1 personality registered for level 1
[    3.469216] raid6: int64x1   3053 MB/s
[    3.639221] raid6: int64x2   4244 MB/s
[    3.809220] raid6: int64x4   3233 MB/s
[    3.979219] raid6: int64x8   2800 MB/s
[    4.149220] raid6: sse2x1    4905 MB/s
[    4.319216] raid6: sse2x2    7954 MB/s
[    4.489216] raid6: sse2x4    9110 MB/s
[    4.489216] raid6: using algorithm sse2x4 (9110 MB/s)
[    4.493258] md: raid6 personality registered for level 6
[    4.493259] md: raid5 personality registered for level 5
[    4.493260] md: raid4 personality registered for level 4
[    4.497324] md: raid10 personality registered for level 10
[  225.181667] md/raid10:md0: active with 3 out of 4 devices

---

### Post by donarntz on 2010-10-15
I'm having the same problem as Santa Clause.  Since my clean install of 10.10, I simply can't get my raid10 to automount at boot.  I get "device not ready skip" screen.  

my mdadm.conf:

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR [email]donarntz@gmail.com[/email]

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid10 num-devices=2 UUID=74039bde:46e92cea:3a874183:b3d08388

# This file was auto-generated on Fri, 15 Oct 2010 11:11:37 -0500
# by mkconf $Id$

and fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc               nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=0f7a889c-b538-4229-9fbf-69f4e56aae5d  /            ext4               errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=30c33535-115a-4c55-93a5-9293ae966262  none         swap               sw                   0  0  
UUID=74039bde:46e92cea:3a874183:b3d08388   /media       ext4               user,defaults        0  0

I would love some help.

---

### Post by Santa_Claus on 2010-10-16
[Hi donarntz]("http://ubuntuforums.org/member.php?u=942283"),

when typed as outbreak monkey adviced

mdadm --assemble --force --scan /dev/md0 
and next boot (yesterday and this morning) my system doesn't halt any more in boot process. I think that this is a turnaround this problem, but not the final solution.  Did your machine boot without problems when you type that command and then re-boot. I also mount the filesystem manually before the re-boot.

---

### Post by donarntz on 2010-10-16
nope... not working for me.  I still get hung up and have to hit "S" to boot.

---

### Post by Santa_Claus on 2010-10-17
Can you mount raid set manually - when in one hd out of duty? What's the output when you type

> mdadm --assemble --force --scan /dev/md0 

and after that

> mount /media

?

---

### Post by donarntz on 2010-10-17
mdadm: /dev/md0 has been started with 2 drives.
sudo mount /media
special device UUID=31263be5:bf5c1508:60987f9a:c8b1731a does not exist
sudo mount /dev/md0
mount: can't find /dev/md0 in /etc/fstab or /etc/mtab

Thats what I get.  It's listed in fstab as the UUID.  When I tried listing it as /dev/md0 in fstab it wouldn't hang but when I tried to mount it, it was always "busy".

---

### Post by donarntz on 2010-10-18
Ok.  It's finally working!  Note:  It absolutely would not pass the skip screen if I used the UUID in fstab.  I changed the listing in fstab to dev/md0.  The UUID is however listed in the mdadm.conf and it is correct.  

I tried previously using dev/md0 in fstab but I was also changing the device listing in mdadm.conf to dev/md0 instead of the UUID.  That didn't work at all for me.  Oh when oh when will ubuntu come up with a gui for creating raid that also writes to fstab....

---

### Post by heheman3000 on 2010-12-15
I'm not sure if some of you are trying to assemble your arrays on boot, or mounting them in /etc/fstab, but for the former, I spent several hours wondering why I couldn't boot off my raid 5 / until I found that the kernel only auto assembles arrays with 0.90 metadata - you need an initramfs to mount the arrays otherwise.

For more information see
[https://raid.wiki.kernel.org/index.php/Autodetect]("https://raid.wiki.kernel.org/index.php/Autodetect")

Hope this helps some of you.

---

### Post by klyndt on 2010-12-20
I have to concur with what ttguy did in post 19. My array absolutely would not start (I tried some of the other suggestions here) until I changed the ARRAY callout in mdadm.conf to 
```
ARRAY /dev/md0 level=raid1 metadata=00.90 num-devices=2 devices=/dev/sdb1,/dev/sdc1
```
I did not have to change the DEVICE callout as was suggested in another post.
In fstab I changed the mount to what sudo blkid gave me for a UUID (not what mdadm gave me in the ARRAY callout after the reconfigure). It turns out that this UUID is the same UUID as the first device in my RAID 1 set.
```
# /Ghost is a raid 1 of sdb1 and sdc1 /dev/md0 UUID=d72b0282:40a01e83:9abbf870:ef93538a
UUID=9479f06e-2ad8-47ae-b1c1-d224050f25f5 /Ghost ext4 defaults 0 2
```
It also turns out that all the dmesg stuff I was looking at was a red herrirng. Until I could get the array started, dmesg gave me nothing.

*EDIT* This ultimately didn't work. See below

---

### Post by syndre on 2010-12-21
I had the same problem that is being discussed here a few weeks ago on a new machine I built. I ended up solving it by installing ubuntu with the "alternate" installation iso. The alternate install disc has everything set up natively to allow you to create a new raid array before the OS gets installed. You can then format your array and mount it as "/", then install directly onto said array. 

I didn't have to mess with trying to figure out what to put in mdadm.conf or fstab at all.


In the hopes of helping anybody reading this in the future, here are my final working mdadm.conf and fstab files:
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=1e220b20-5751-4252-9212-ef1eafee491c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=27ff341e-35ba-4a53-a8a5-cd9b0cef41e3 /boot           ext4    defaults        0       2
# /home was on /dev/md0 during installation
UUID=609da14f-69d0-4889-bfe9-124024896ca8 /home           ext4    defaults        0       2



> 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid0 num-devices=4 UUID=700e5b4f:85079565:eb201670:8b85c392
ARRAY /dev/md1 level=raid10 num-devices=3 UUID=a7b267aa:eff86c94:0acba3ba:31e95ab5

# This file was auto-generated on Mon, 13 Dec 2010 16:39:35 -0500
# by mkconf $Id$

\\:D/

---

### Post by jarcikon on 2010-12-21
I also ran into this problem using Ubuntu 10.10 Server Edition. One of the hard drives in a raid 10 array failed and I replaced it. I eventually got the array rebuilt, but it would fail on reboot saying the disk is not yet ready or not present. I tried rebuilding the partitions on the new drive, zeroing the superblock, setting metadata=0.90 in mdadm.conf, all to no avail.

It turns out that when I first rebuilt the array I did it with the drive device (/dev/sdf) instead of the partition (/dev/sdf1). I later corrected this, but it left a superblock on the drive which does not get zeroed when you do mdadm --zero-superblock /dev/sdf1. In the end, zeroing the superblock for the drive AND the partition did the trick. The array now builds fine on reboot. Might want to keep this in mind of the above solutions do not work.

---

### Post by klyndt on 2010-12-27
After a few boots I found that my raid array was having serious problems and I would end up having to reboot or just skip the array mounting.  I decided to try again.  This is what I did (and seems to work through a couple reboots).
1. installed Gparted
2. in a terminal: sudo palimpsest
 to open Disk Utility and stop the array that was in there
3. closed that and in a terminal: sudo gparted
4. deleted out the partitions that were on sdb and sdc (my raid 1 drives)
5. Closed gparted
6. sudo palimpsest again. Partitioned and formated the Raid array for ext4
7. Closed palimpsest and typed: sudo rm /etc/mdadm/mdadm.conf
8. typed: sudo dpkg-reonfigure mdadm
9. opened the new mdadm.conf file (sudo gedit /etc/mdadm/mdadm.conf) and copied the UUID. While in gedit, I opened /etc/fstab and pasted the UUID so I could mount the raid drive at boot (UUID=d72b0282:40a01e83:9abbf870:ef93538a /Ghost ext4 defaults 0 2)
10. Saved fstab and rebooted
11. Skipped mounting the raid drive because this didn't work! Damn!
12. Opened Disk Utility again and manually started the array.
13. In a terminal: sudo blkid
14. Noticed that the UUID for sdb, sdc, and the raid array have the same UUID and.... it is different from the UUID in mdadm.conf and consequently fstab.
15. sudo gedit /etc/mdadm/mdadm.conf and pasted the UUID from the blkid command into the ARRAY line (ARRAY /dev/md0 level=raid1 num-devices=2 UUID=a901b9d9-92cb-49ec-aedb-8b0654b08edb). Opened fstab while in gedit and corrected the UUID in there too (UUID=a901b9d9-92cb-49ec-aedb-8b0654b08edb /Ghost ext4 defaults 0 2)
16. Saved, closed gedit, and rebooted.
17. It works! Rebooted again. It still works!

To skip the failing steps I think I would do step 8 and then skip to step 13.  Hopefully this works this time.

Klyndt

---

### Post by tpoindex on 2011-02-08
Here is how I fixed the problem of the raid devices not starting at boot time.  
I have my root partition on a non-raid device, /home is raid1.  Symptoms were that a 
normal boot into multi-user mode would fail frequently; rebooting immediately or dropping into
single user mode to start the raid device was required.

To fix, I modified [FONT="Courier New"]/etc/init/mountall.conf[/FONT] at line 38 
to run mdadm to ensure the raid devices are started
before the mountall command.  Here is my [FONT="Courier New"]/etc/init/mountall.conf[/FONT]

```

# mountall - Mount filesystems on boot
#
# This helper mounts filesystems in the correct order as the devices
# and mountpoints become available.

description	"Mount filesystems on boot"

start on startup
stop on starting rcS

expect daemon
task

emits virtual-filesystems
emits local-filesystems
emits remote-filesystems
emits all-swaps
emits filesystem
emits mounting
emits mounted

# temporary, until we have progress indication
# and output capture (next week :p)
console output

script
    . /etc/default/rcS
    [ -f /forcefsck ] && force_fsck="--force-fsck"
    [ "$FSCKFIX" = "yes" ] && fsck_fix="--fsck-fix"

    # set $LANG so that messages appearing in plymouth are translated
    if [ -r /etc/default/locale ]; then
        . /etc/default/locale
        export LANG LANGUAGE LC_MESSAGES LC_ALL
    fi

    # - make sure md devices are up
    mdadm --assemble --scan
    exec mountall --daemon $force_fsck $fsck_fix
end script

post-stop script
    rm -f /forcefsck 2>dev/null || true
end script

```

---

### Post by phelan-kell on 2011-02-15
Hi everyone,

Brilliant thread going here! Unfortunately it hasn't helped me (if it had I wouldn't be posting!) ;-)

I have just installed 10.10, with 1x 320gb drive (Ubuntu installed here), 4x 2tb drives (three with RAID5, one as a backup until I'm happy). I created the raid array with Disk Utility through the gui. I'm not 100% sure my problems match what others are experiencing.

When I start Disk Utility, the array is not running and it is partially assembled and capacity is reported as 0k. I have to select Stop RAID Array and then Start RAID Array to get the array to start. I then have to mount the partition by clicking mount partition.

I want to autostart and automount the array on boot, but to begin with I'd just be happy with autostarting the array. I've followed the instructions here with no luck. Can someone please tell me what's going wrong and the commands to fix it?

My array uses /dev/sda1, /dev/sdb1, and /dev/sdc1, and as of right now reckons it's degraded, but all disks report as being healthy(?!?!)

Any help will be greatly appreciated! Perhaps I'm just being stupid?

Info as follows is from the array mounted, array degraded

```
root@HTPC:/home/media/Desktop# sudo mdadm -D -s
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=01.02 name=:Array UUID=559b0f9b:13306bf7:c45d6113:750b927c
```

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/Array level=raid5 metadata=1.2 num-devices=3 UUID=559b0f9b:13306bf7:c45d6113:750b927c name=:Array

# This file was auto-generated on Tue, 15 Feb 2011 20:05:46 +1300
# by mkconf $Id$

```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# swap was on /dev/sda5 during installation
UUID=a46edf1b-1bdd-4cf3-8ce5-98ca344a8eee none            swap    sw              0       0
```

```
root@HTPC:/home/media# sudo blkid
/dev/sda1: UUID="559b0f9b-1330-6bf7-c45d-6113750b927c" LABEL=":Array" TYPE="linux_raid_member" 
/dev/sdb1: UUID="559b0f9b-1330-6bf7-c45d-6113750b927c" LABEL=":Array" TYPE="linux_raid_member" 
/dev/sdc1: UUID="559b0f9b-1330-6bf7-c45d-6113750b927c" LABEL=":Array" TYPE="linux_raid_member" 
/dev/sdd1: LABEL="Backup" UUID="39bb2373-96d6-4e89-a0dd-01eef0976a4c" TYPE="ext4" 
/dev/sde1: UUID="1c3513eb-6ae0-4b1f-a817-054f57bf7f4a" TYPE="ext4" 
/dev/sde5: UUID="a46edf1b-1bdd-4cf3-8ce5-98ca344a8eee" TYPE="swap" 
/dev/md0p1: LABEL="Data" UUID="fb3523d0-72e7-4f5e-b8e0-fd448d5c875f" TYPE="ext4"
```

```
root@HTPC:/home/media# cat   /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[1] sda1[3]
      3907028824 blocks super 1.2 level 5, 4k chunk, algorithm 2 [3/2] [_UU]
      bitmap: 5/466 pages [20KB], 2048KB chunk

unused devices: <none>
```

---

### Post by pitstop2001 on 2011-02-16
I followed tpoindex (thank you!) suggestion and modified:

/etc/init/mountall.conf

to include:

mdadm --assemble –scan

ahead of this line:

exec mountall --daemon $force_fsck $fsck_fix

and it WORKED!!

Try it.

---

### Post by phelan-kell on 2011-02-19
> **pitstop2001 said:**
> I followed tpoindex (thank you!) suggestion and modified:

/etc/init/mountall.conf

to include:

mdadm --assemble –scan

ahead of this line:

exec mountall --daemon $force_fsck $fsck_fix

and it WORKED!!

Try it.

Yeah that killed my machine. On boot I'd get a blinking cursor. Just having to figure out editing that file to remove the code while booting from disc.
Seriously thinking of changing OS. I know everyone reading this forum has thought this - how can it be so hard for Ubuntu when it's so easy on Windows.

---

### Post by barrynz on 2011-02-23
This worked for me:

DEVICE /dev/sdb /dev/sdc
ARRAY /dev/md0 level=raid1 devices=/dev/sdb1,/dev/sdc1

Note that in the DEVICE line, is sdb and sdc, while in the ARRAY line we have sdb1, sdb2 (ie the physical partition name)

---

### Post by AllGamer on 2011-03-16
***"that was easy"***

so i followed outbreak suggestions to use:

sudo rm /etc/mdadm/mdadm.conf

sudo dpkg-reconfigure mdadm 

and it did re-create /etc/mdadm/mdadm.conf 

with this extra parameters that were not in there previously

ARRAY /dev/md0 level=raid5 num-devices=4 UUID=1cd3c907:5ebd7927:310b5b34:c3d51354


now after a reboot, the server automatically starts the RAID and mounts it too :D

---

### Post by bitwhys on 2011-04-26
Here's what worked for me.

fstab and mdadm.conf use two different formats of UUID.

First, of course, I mounted the array manually then...

To got the UUID in needed for fstab by navigating to /dev/disk/by-uuid and found the one it had to be (by process of elimination since the other two were already IN fstab - convenient).  A quick right-click copy in Nautilus then a paste to a blank gedit got me the snippet I needed to build a:

```
UUID=7c57bc3a-192b-44d1-bad7-b4c03cb85daa /<mountpoint>  ext4    defaults          0       0
```entry for fstab

For mdadm.conf, in Terminal I entered

```
sudo mdadm -Es
```got me the other UUID.  Copy and paste out of terminal and I could build the

```
ARRAY /dev/md0 UUID=37aea0e4:a2e49cde:0b51d9b2:b8c813a2
```entry I needed for mdadm.conf.

came up clean on reboot so hopefully it wasn't just a fluke and somebody else can use it.

Guess it got renumbered on the upgrade.

b

---

### Post by donarntz on 2011-04-26
I finally gave up and turned one disk into media storage and the other into backup.  What a farking pain.  I wasted days on this problem.

---

### Post by jwdonal on 2011-05-25
> **teeedubb said:**
> On boot I get a screen stating 'the disk for/mnt/md0 is not ready yet or not  present. Continue to wait; or Press S to skip mount or M for manual recover'.
I had this exact same problem (except mine was complaining about /dev/md4). I'm using Ubuntu 10.04.  My fix was as follows.

First, and most importantly, I have discovered that there are 2 different UUIDs for each disk:
One UUID is from: ```
ls -l /dev/disk/by-uuid/
```Another UUID is from: ```
sudo blkid
```The UUID from the 'ls' command will ONLY work (i.e. be available) _after_ the RAID array has been started by mdadm! This means that you can _not_ use the UUID from the '/dev/' directory for the mdadm.conf file because mdadm wont recognize it.  For the mdadm.conf file you _must_ use the UUID from the 'sudo blkid' command!

For my system, I added the following line to /etc/mdadm/mdadm.conf:
```
ARRAY /dev/md4 level=raid1 num-devices=2 UUID=24155045:87d6badb:17b079cf:931fd724
```**Also note how the UUID syntax for the mdadm.conf file uses colons instead of dashes.  The UUID output from the 'blkid' command uses dashes so you will need to change it to use colons (and the colons are not in the same location as the dashes!)**

Then add the following to /etc/fstab to make the RAID mount at startup (remember, you can't
mount the raid until it is started by mdadm! so you MUST add the line to the mdadm.conf file (above)!!). **Note that the UUID in the fstab file should come from the 'ls /dev/' command above.**
```
UUID=a0dd46f8-ea6f-4452-8529-5983053752b4 /mnt/VMware_Disk ext4 defaults 0 2
```Also, make sure that the mount point directory actually exists.  In my case, /mnt/VMware_Disk

---

### Post by BrooklynOutdoor on 2011-07-10
One thing I had to do was make sure the array line was at the start of mdadm.conf.  Doing that seemed to solve the problem:

```
#
# Please refer to mdadm.conf(5) for information about this file.
#

# definitions of existing MD arrays
ARRAY /dev/md0 metadata=1.2 name=thoth:0 UUID=42930826:a8d3264b:af76e6f5:14e3613f

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions
```

I think the problem is that the default config file is scanning partitions BEFORE assembling the arrays unless the order is changed.  A clue besides the failed mount at boot was that my raid kept changing from md0 to md127 on restart.

---

### Post by ttguy on 2011-10-15
So back on Maverik I had this same issue and I was able to fix it using Outbreak Monkeys suggestion of using the device names rather than UUIDs in the /etc/mdadm/mdadm.conf
I first built my Raid on Lucid and the problem of the raid not assembling happened when I upgraded to Maverik (clean install).

So I was worried I would have to go throught the whole problem again when I upgraded to Natty. But ... it looks like we may have made some progress on this issue with Natty.

I did a clean install of natty and after the instal finished my raid device did not mount. However dmraid and mdadm were not installed. After installing them and rebooting my raid device started and mounted. The mdadm.conf file that was automatically created has UUIDs in it.  I was then able to move my /home to my raid and still have it auto start auto mount.

So hooray for the *Natty Narwhal*.

---

### Post by not_for_you on 2011-10-25
Had the same problem and found the easiest fix was to use the nobootwait option in fstab.  Works everytime and didn't matter if I used UUID, LABEL or /dev/mdXpX.

---

### Post by joikabollefinn on 2011-11-21
> **Outbreak Monkey said:**
> I had to fiddle around quite a bit to get it to work on boot, the process I followed was:
Blow away mdadm.conf, dpkg-reconfigure, EDIT the mdadm.conf to get the devices in the right order using device names etc... THEN _dpkg-reconfigure again_ (this seems to do the initramfs  update stuff using the content of mdadm.conf)..

I might add, mine is a Raid 5 array. I don't know if we're having the same problem, but I do know I had to muck around a little and it wasn't quite intuitive.

Cheers,
ObM.

Thanks! This saved me too :) I have created 1 raid0 and 2 raid1 arrays, but none would start nor mount at boot.

After deleting mdadm.conf and then dpkg-reconfigure mdadm, it worked! Didn't have to change to device-names instead of UUID either.

edit: I'm using 10.04 LTS.

/jokke

---

### Post by tpak on 2012-01-21
I was pulling my hair out on this over on an EC2 instance today. I found 10 examples of how to set everything up, some even recent, but not one was followed with a reboot or the authors surely would have run into this. 

[apologies in advance - a long post- but trust me, probably worth the read if you are having this issue]

Noticing the dmesg chatter earlier in this thread made it click for me at least in EC2 land. The newer linux kernels load the devices as /dev/xvdXX instead of /dev/sdXX - but over on EC2 at least you can create them any way you want --  using the Amazon AMI at least they show up both ways and you can create your raid device using the old naming convention which is exactly what I did. If on EC2 you use the console to create volumes it mentions the new naming convention as a warning. And of course I didn't pay much attention at the time.

When I ran dmesg got this (I have 8 EBS volumes in a raid 10 originally mounted as /dev/sdh1-8):

```
[ec2-user ~]$ dmesg | grep -E 'md:|raid'
[    0.408331] md: bind<xvdh1>
[    0.412267] md: bind<xvdh2>
[    0.418602] md: bind<xvdh3>
[    0.433205] md: bind<xvdh4>
[    0.458456] md: bind<xvdh5>
[    0.465828] md: bind<xvdh6>
[    0.499950] md: bind<xvdh7>
[    0.554412] md: bind<xvdh8>
[    0.563213] md: raid10 personality registered for level 10
[    0.563595] md/raid10:md127: active with 8 out of 8 devices
[    0.951121] md: md127 stopped.
[    0.951203] md: unbind<xvdh8>
[    0.951282] md: export_rdev(xvdh8)
[    0.951494] md: unbind<xvdh7>
[    0.951550] md: export_rdev(xvdh7)
[    0.951728] md: unbind<xvdh6>
[    0.951814] md: export_rdev(xvdh6)
[    0.952024] md: unbind<xvdh5>
[    0.952077] md: export_rdev(xvdh5)
[    0.952229] md: unbind<xvdh4>
[    0.952239] md: export_rdev(xvdh4)
[    0.952346] md: unbind<xvdh3>
[    0.952355] md: export_rdev(xvdh3)
[    0.952459] md: unbind<xvdh2>
[    0.952468] md: export_rdev(xvdh2)
[    0.952576] md: unbind<xvdh1>
[    0.952585] md: export_rdev(xvdh1)
``` 

And at this point after a reboot this would neither activate the raid device or mount properly. I could manually assemble and then mount the fs. But the new device naming made me think maybe the solution was simple - I'm mounting the wrong devices .... new kernel ... mounting issues ... new dvice naming convention ... so let's have a look in /dev


```
[ec2-user ~]ls /dev
block            hvc7     md                  sdh3    tty15  tty31  tty48  tty7     vcsa3
char             input    md0                 sdh4    tty16  tty32  tty49  tty8     vcsa4
console          kmsg     mem                 sdh5    tty17  tty33  tty5   tty9     vcsa5
core             log      net                 sdh6    tty18  tty34  tty50  ttyS0    vcsa6
cpu              loop0    network_latency     sdh7    tty19  tty35  tty51  ttyS1    vga_arbiter
cpu_dma_latency  loop1    network_throughput  sdh8    tty2   tty36  tty52  ttyS2    xvda1
disk             loop2    null                shm     tty20  tty37  tty53  ttyS3    xvdh1
fd               loop3    oldmem              stderr  tty21  tty38  tty54  urandom  xvdh2
full             loop4    port                stdin   tty22  tty39  tty55  vcs      xvdh3
fuse             loop5    ppp                 stdout  tty23  tty4   tty56  vcs1     xvdh4
hugepages        loop6    psaux               tty     tty24  tty40  tty57  vcs2     xvdh5
hvc0             loop7    ptmx                tty0    tty25  tty41  tty58  vcs3     xvdh6
hvc1             lp0      pts                 tty1    tty26  tty42  tty59  vcs4     xvdh7
hvc2             lp1      random              tty10   tty27  tty43  tty6   vcs5     xvdh8
hvc3             lp2      root                tty11   tty28  tty44  tty60  vcs6     zero
hvc4             lp3      sda1                tty12   tty29  tty45  tty61  vcsa
hvc5             MAKEDEV  sdh1                tty13   tty3   tty46  tty62  vcsa1
hvc6             mapper   sdh2                tty14   tty30  tty47  tty63  vcsa2
```

Interesting ... both versions of my devices are listed. My old mdadm.conf looked like this:

```
DEVICE /dev/sdh[1-8]
ARRAY /dev/md0 metadata=1.2 name=ip-XX-XXX-XX-XX:0 UUID=e2aef894:56d374f2:92de6861:9b61d5ed
```

On a random hunch I just changed it to look like this:

```

DEVICE /dev/xvdh[1-8]
ARRAY /dev/md0 metadata=1.2 name=ip-XX-XXX-XX-XX:0 UUID=e2aef894:56d374f2:92de6861:9b61d5ed
```

sudo reboot .... and TADA! The raid device magicly activates and fstab mounts it! A quick revisit to dmesg shows md doing almost exactly what it did before but then coming back a couple of seconds later and righting the ship:

```
ec2-user@ ~]$ dmesg | grep -E 'md:|raid'
[    0.415873] md: bind<xvdh1>
[    0.420351] md: bind<xvdh2>
[    0.425141] md: bind<xvdh3>
[    0.431455] md: bind<xvdh4>
[    0.461325] md: bind<xvdh5>
[    0.469443] md: bind<xvdh6>
[    0.477956] md: bind<xvdh7>
[    0.492238] md: bind<xvdh8>
[    0.518618] md: raid10 personality registered for level 10
[    0.519722] md/raid10:md127: active with 8 out of 8 devices
[    0.919828] md: md127 stopped.
[    0.919906] md: unbind<xvdh8>
[    0.919982] md: export_rdev(xvdh8)
[    0.920450] md: unbind<xvdh7>
[    0.920506] md: export_rdev(xvdh7)
[    0.920634] md: unbind<xvdh6>
[    0.920714] md: export_rdev(xvdh6)
[    0.920818] md: unbind<xvdh5>
[    0.920895] md: export_rdev(xvdh5)
[    0.920959] md: unbind<xvdh4>
[    0.920967] md: export_rdev(xvdh4)
[    0.921035] md: unbind<xvdh3>
[    0.921043] md: export_rdev(xvdh3)
[    0.921100] md: unbind<xvdh2>
[    0.921108] md: export_rdev(xvdh2)
[    0.921164] md: unbind<xvdh1>
[    0.921172] md: export_rdev(xvdh1)
[    2.777362] md: bind<xvdh1>
[    2.787218] md: bind<xvdh2>
[    2.797055] md: bind<xvdh3>
[    2.804943] md: bind<xvdh4>
[    2.818034] md: bind<xvdh8>
[    2.834794] md: bind<xvdh5>
[    2.847341] md: bind<xvdh7>
[    2.862080] md: bind<xvdh6>
[    2.876745] md/raid10:md0: active with 8 out of 8 devices
```

and lo and behold, my fs on /dev/md0 is now mounted, magicly even:
```
[ec2-user@ ~]$ df 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/xvda1             8256952   1556672   6616408  20% /
tmpfs                   305624         0    305624   0% /dev/shm
/dev/md0              83836928     33312  83803616   1% /mysqldata
```

Obviously YMMV but I would love to hear if this helps some of you. It makes perfect sense that if the default device mappings were changed in the kernel then mdadm needs to know the names the kernel is going by .... 

So just to verify I set the DEVICE line in mdadm.conf to /dev/sdaXX again and rebooted then ran mdadm --assemble .... and here is what I found:

```
ec2-user ~]$ sudo mdadm --assemble --scan  
mdadm: /dev/md0 has been started with 8 drives.
[ec2-user ~]$ dmesg | grep -E 'md:|raid'
[    0.467764] md: bind<xvdh1>
[    0.471834] md: bind<xvdh2>
[    0.477562] md: bind<xvdh3>
[    0.488167] md: bind<xvdh4>
[    0.522339] md: bind<xvdh5>
[    0.530052] md: bind<xvdh6>
[    0.567123] md: bind<xvdh7>
[    0.577266] md: bind<xvdh8>
[    0.587657] md: raid10 personality registered for level 10
[    0.588267] md/raid10:md127: active with 8 out of 8 devices
[    1.086254] md: md127 stopped.
[    1.086264] md: unbind<xvdh8>
[    1.086273] md: export_rdev(xvdh8)
[    1.086664] md: unbind<xvdh7>
[    1.086675] md: export_rdev(xvdh7)
[    1.086749] md: unbind<xvdh6>
[    1.086757] md: export_rdev(xvdh6)
[    1.086818] md: unbind<xvdh5>
[    1.086826] md: export_rdev(xvdh5)
[    1.086890] md: unbind<xvdh4>
[    1.086899] md: export_rdev(xvdh4)
[    1.086961] md: unbind<xvdh3>
[    1.086969] md: export_rdev(xvdh3)
[    1.087036] md: unbind<xvdh2>
[    1.087045] md: export_rdev(xvdh2)
[    1.087114] md: unbind<xvdh1>
[    1.087123] md: export_rdev(xvdh1)
[   25.515171] md: md0 stopped.
[   25.526062] md: bind<xvdh2>
[   25.527167] md: bind<xvdh3>
[   25.528160] md: bind<xvdh4>
[   25.529120] md: bind<xvdh5>
[   25.529978] md: bind<xvdh6>
[   25.530938] md: bind<xvdh7>
[   25.531816] md: bind<xvdh8>
[   25.532764] md: bind<xvdh1>
[   25.582426] md/raid10:md0: active with 8 out of 8 devices

```

That's me at 25 second in  running 'sudo mdadm --assemble --scan' causing it to stop and activate md0. After that I can mount the fs ... 

I don't know exactly why it works, but it does.

One last bit - I have been doing this on an Amzon Linux AMI 64 bit --  which is CentOS based/derived. However, I am guessing this applies here as well. If I have time I will try it on an Ubuntu instance but not tonight.

Cheers
Chris

follow up: my mdadm.conf is straight from the detail scan bit:

```
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm.conf 
```

---

### Post by doug901 on 2012-01-21
Great thread.  Was having same problem as #18; RAID did not mount in boot under Ubuntu 11.10.  Manual mount after boot was fine.

Turns out the RAID was loaded under a different name in the boot sequence (and after fstab did its work).  That means, per this thread that UUID doesn't work.  Needed to use the dev/ location instead.  But dev location was different than shown after boot.

Using the command:

# dmesg | grep -E 'md: | raid'

I discovered that the RAID was not loading as md0 or the other /dev locations that I thought.  Instead it was at "md127".

With that information, changed the fstab entry to:
/dev/md127    /media/RaidPart    ext4    defaults    0    0

Now it automounts.  Thanks!

---

