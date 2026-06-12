---
title: "I think I screwed up my fstab... can anybody take a look?"
date: 2011-01-11
forum: General Help
---

### Post by gschoppe on 2011-01-11
I rebooted my server, for the first time in a couple months, and on boot got the dreaded unable to mount message.  I played with my fstab a while ago, but was pretty sure it was working after my last edit, and I think I've rebooted since then, without issue, but I'm simply not sure...

my fstab file is as follows:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=95af0499-2cd6-4bdd-a16f-af7fd86ebb31 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=8f6ef0ef-9483-4a31-80a8-f3a047d212bc /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=3a7538ae-c082-4614-8fce-69ac2f7463c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# 1TB drive is mounted to shared video folder
/dev/sda1 /home/gschoppe/Shared\040Media/Video           ext4    defaults        0       2

```

Both drives appear to be accessible from live CD, and commenting out the line mounting the home folder and the line mounting 'Shared Video' gets me a desktop, but of course, with no home folder, there isn't much more I can do in the GUI.

if anyone could take a look, it would be a big help... the errors I'm getting reference UUID 8f6ef0ef-9483-4a31-80a8-f3a047d212bc and sda1

I could really use some help on this one, as fstab confuses the heck outta me.

---

### Post by drs305 on 2011-01-11
You should probably run "sudo fdisk -l" and "sudo blkid -c /dev/null" to compare your fstab settings to what the computer is reporting.

What I suspect is that your fstab you have shared Video mounted on /dev/sda1 and so is /. 

We cannot trust the comments, but the comment for / states it was initially installed on sda1.

Check the UUID for sda1 and /. They are most likely the same and you need to change the setting for your Shared video.

---

### Post by papibe on 2011-01-11
Could you post the result of this?
```
$ sudo fdisk -l
```
Regards.

---

### Post by sisco311 on 2011-01-11
EDIT: D'oh! I'm slow! :)

Check out: [uhelp]community/UsingUUID[/uhelp]

In short, run:
```
sudo fdisk -l
```
to find the current device name of the 1TB drive. Then:
```
sudo blkid
```
to get the UUID of the partition. After that edit your fstab and use the UUID of the partition rather than its device name.

---

### Post by gschoppe on 2011-01-11
the comments are indeed misleading, as when I installed my new 1TB HDD it became sda1

I'm on a different machine to post, so unless I absolutely have to, I'd like to not post the entire results of fdisk -l, but the salient points are:

sda1 -   1TB - mounts to /gschoppe/home/Shared Video
sdb1 -  10GB - mounts to /
sdb2 -   2GB - swap
sdb3 - 488GB - mounts to /home

blkid yields

sda1 - UUID: 02c4de06-2c3f-4215-9388-92df4cdf4789
sdb1 - UUID: 95af0499-2cd6-4bdd-a16f-af7fd86ebb31


seems functional, if a bit stilted.. any thoughts?

---

### Post by sisco311 on 2011-01-11
Once again, device names may change between system boots. As you can see, your root partition was /dev/sda1 at installation time and now is /dev/sdb1.

So, edit your fstab and replace the last line with:
```
**UUID=02c4de06-2c3f-4215-9388-92df4cdf4789** /home/gschoppe/Shared\040Media/Video           ext4    defaults        0       2
```

---

### Post by gschoppe on 2011-01-11
New fstab reads:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / (10GB) was on /dev/sdb1 as of 1/11/11
UUID=95af0499-2cd6-4bdd-a16f-af7fd86ebb31 /               ext4    errors=remount-ro 0       1
# /home (488GB) was on /dev/sdb3 as of 1/11/11
UUID=8f6ef0ef-9483-4a31-80a8-f3a047d212bc /home           ext4    defaults        0       2
# swap (2GB) was on /dev/sdb2 as of 1/11/11
UUID=3a7538ae-c082-4614-8fce-69ac2f7463c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /home/gschoppe/Shared\040Media/Video (1TB) was on /dev/sdb1 as of 1/11/11
#/dev/sda1 /home/gschoppe/Shared\040Media/Video           ext4    defaults        0       2
UUID=02c4de06-2c3f-4215-9388-92df4cdf4789 /home/gschoppe/Shared\040Media/Video           ext4    defaults        0       2

```

restarting now... I'm not very hopeful, as the problem persisted even when, in recovery console, on the same boot, the drives were enumerated as used in the original fstab.. but fingers are crossed.

---

### Post by gschoppe on 2011-01-11
same problem:

one or more of the drives defined in fstab cannot be mounted...
waiting for..

except now it has the UUID listed in both places rather than UUID in one spot and sda1 in the other...

---

### Post by gschoppe on 2011-01-11
oh, and before anyone asks, I have triple checked the UUID, it is correct.

I also ran:
sudo fsck -f /dev/sda1
and
sudo fsck -f /dev/sdb3

just to check.  both come up clean, I'm gonna try a Hitachi drive test in the morning, but if there is an issue, it must be intermittent, as the drive mounts fine on the live cd, and the sheer number of times I've rebooted seems to imply that it would have worked at least once...

---

### Post by drs305 on 2011-01-12
I know you are running a server but perhaps you could add 'defaultls,**noauto**' on the Video drive and then manually mount it after the system boots. You can then experiment with commands to view the error messages and come up with a mounting option that works. 

You could experiment with different fstab settings for the partition by running:```

sudo umount -a
sudo mount -a
```
You would get 'busy' messages for your system partitions but it would ensure the additional partition mounts via fstab command if you get no error messages on mounting. At that point, you could incorporate the working options into fstab. 

If it turns out that you need to delay mounting to allow time for the drive to become available to the system you could write a simple start up script which includes a 'sleep' option.

---

### Post by sisco311 on 2011-01-12
Also check out /var/log/dmesg* and see if contains some relevant error messages.

---

### Post by gschoppe on 2011-01-12
ok, so here's the latest:

it appears that I misread the fstab error message I was getting... it first says it can't mount the /home partition, then also fails at mounting the /home/gschoppe/Shared Media/Video directory... obviously, as it failed to mount /home, so there's no mount point available.

so, the issue is that it won't mount /home

- I ran a full DFT (Drive Fitness Test) on both drives, with no issues found.

- /var/log/dmesg appears to have no relevant errors

- sudo fsck -f seemed to find nothing on either drive

- no SMART errors

any ideas?

---

### Post by gschoppe on 2011-01-12
one more thing, sudo blkid isn't listing my /dev/sdb3 (/home) drive when i run it from the recovery shell, only when run from a live cd... just realized that...

however, the drive is fully acessable from the live cd... and appears to have data intact

---

### Post by piquat on 2011-01-13
> **drs305 said:**
> I know you are running a server but perhaps you could add 'defaultls,**noauto**' on the Video drive and then manually mount it after the system boots. You can then experiment with commands to view the error messages and come up with a mounting option that works. 

You could experiment with different fstab settings for the partition by running:```

sudo umount -a
sudo mount -a
```You would get 'busy' messages for your system partitions but it would ensure the additional partition mounts via fstab command if you get no error messages on mounting. At that point, you could incorporate the working options into fstab. 

If it turns out that you need to delay mounting to allow time for the drive to become available to the system you could write a simple start up script which includes a 'sleep' option.

I would back up and start doing this.  It's basically what I did when I was trying to figure this out.  Change fstab, sudo mount -a, look at the errors, if any, and make a change in fstab to try and compensate, then another sudo mount -a to see what difference it made.  It's tedious but it works and also helped me learn a bit more about what was really going on.

---

### Post by drs305 on 2011-01-13
> **gschoppe said:**
> one more thing, sudo blkid isn't listing my /dev/sdb3 (/home) drive when i run it from the recovery shell, only when run from a live cd... just realized that...

however, the drive is fully acessable from the live cd... and appears to have data intact

Can you get to the grub prompt during boot? Press 'c' from the grub menu (hold down the SHIFT key if it the menu doesn't appear).

Then try these commands:
```
ls (hd1,3)
ls (hd1,3)/
```

You might try (hd0,3) if you get no result from (hd1,3)...

Does the first report your HOME UUID and the proper information?
Does the second report any contents?

---

### Post by gschoppe on 2011-01-16
ls (hd0,3) - shows the correct UUID of 8f6ef0ef-9483-4a31-80a8-f3a047d212bc
ls (hd0,3)/ - shows the expected subfolders gschoppe and lost+found

sudo mount -a yields
"special device UUID=8f6ef0ef-9483-4a31-80a8-f3a047d212bc does not exist"

confused at the simultaneous existing and not existing...

---

### Post by drs305 on 2011-01-17
From a LiveCd, have you tried editing the fstab and changing the entry to "/dev/sda3" instead of it's UUID? Or labeled sda3 "home" and using "LABEL=home" in fstab. 

You could also try changing the UUID with the "tune2fs -U random /dev/sda3"  command; you would need to change fstab and your grub menu if you do so (not that they are working that well at the moment anyway...).

I must say this is very odd.

---

### Post by gschoppe on 2011-01-18
OK, Thanks to Everybody (especially drs305), the machine is now booting.

I replaced the UUID with /dev/sdb3, and everything is working again... I once again re-checked the UUID, and there is no typo... I even copied/pasted it from blkid to fstab, and it still won't boot with the UUID.

I'd like to be using the UUID, so I don't have the same issue next time I change hardware, but at least its working...

does anyone have any ideas as to why this might have happened?

---

### Post by s1baker on 2011-06-18
I'm a noob, but should the slash between Shared and 040Media
be a foward slash?
```

/dev/sda1 /home/gschoppe/Shared\040Media/Video 
```

---

### Post by Morbius1 on 2011-06-18
No, the real name of the directory is "Shared Media". Fstab gets confused with spaces so you add "\040" to let it know that a space goes there.

---

### Post by drs305 on 2011-06-18
> **s1baker said:**
> I'm a noob, but should the slash between Shared and 040Media
be a foward slash?
```

/dev/sda1 /home/gschoppe/Shared\040Media/Video 
```

The way you have entered it above is correct: .../Shared\040Media/... which will be interpreted as "*Shared Media*"
"\040" is interpreted as a 'space' in fstab.

---

