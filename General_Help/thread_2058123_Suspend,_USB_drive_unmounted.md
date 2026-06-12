---
title: "Suspend, USB drive unmounted"
date: 2012-09-15
forum: General Help
---

### Post by dln9 on 2012-09-15
I have an external hard drive connected to my laptop via a USB connection.

When I boot up the laptop, the external drive gets mounted just fine.

When the laptop is running - with this external drive mounted - I sometimes need to suspend the laptop. So, I will select "Log Out", and then select "Suspend". The laptop suspends just fine.

Then, from suspend, I want the laptop to resume its former state. I briefly press the power button, and the laptop ends being in suspended mode, and everything resumes to where I'd left off.

EXCEPT - The external hard drive is no longer mounted. I end up having to manually remount the drive. I don't like this.

How do I make the laptop remount the external hard drive when the laptop is resuming operations from suspend mode?  Or - perhaps more importantly - How do I go about diagnosing what the problem is?  

Thanks.

---

### Post by Epodx64 on 2012-09-15
Post this from a terminal 

cat /etc/fstab

while the drive is mounted.

---

### Post by dln9 on 2012-09-15
cat /etc/fstab:  


[PHP]cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda2 during installation
UUID=f071d055-1a41-4b6a-a09a-b2dba9aec7e0  /               ext4  errors=remount-ro         0  1  
# /boot was on /dev/sda1 during installation
UUID=8e32b52b-a8c5-4111-a5e8-049f861b86b6  /boot           ext4  defaults                  0  2  
# /home was on /dev/sda7 during installation
UUID=5865697b-f7d9-4ec0-a3e3-2200c14fb7d6  /home           ext4  defaults                  0  2  
# /usr was on /dev/sda5 during installation
UUID=c117cc75-d7c1-4a0e-bee5-faaeff5558d9  /usr            ext4  defaults                  0  2  
# /var was on /dev/sda6 during installation
UUID=fcaed2f8-3a75-47f9-aa35-489bcea465cd  /var            ext4  defaults                  0  2  
# swap was on /dev/sda8 during installation
UUID=f358f0f2-5f5a-4f05-85c0-08351ea9f0b5  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
UUID=38807cc4-8870-4a00-a19d-b9310454714c  /media           ext4 defaults                  0  0[/PHP]



The external drive in question is the last one UUID = 38807......  


In the meantime, just a little while ago, I implemented this workaround that does the job, but it just doesn't seem that I should need to do this:  

in /etc/pm/sleep.d, I created this script:  

[PHP]#!/bin/sh

case "$1" in
	hibernate|suspend) ;;
	thaw|resume)
		sleep 5
	        mount -U 38807cc4-8870-4a00-a19d-b9310454714c /media ;;
esac[/PHP]

---

### Post by Epodx64 on 2012-09-15
amended

---

### Post by Epodx64 on 2012-09-15
[B]Hold on I think I found a better solution
try this first[/B]
add after defaults,[B]nofail
[/B]like this
```

[COLOR=#000000][COLOR=#0000BB]UUID[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]38807cc4[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]8870[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]4a00[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]a19d[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]b9310454714c  [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]media           ext4 defaults,**nofail  **                0  0  [/COLOR][/COLOR]

```disregard my other comment this should work.

---

