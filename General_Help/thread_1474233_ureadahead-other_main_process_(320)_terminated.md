---
title: "ureadahead-other main process (320) terminated"
date: 2010-05-05
forum: General Help
---

### Post by screaminj3sus on 2010-05-05
So when I boot before the boot slpash this shows:
ureadahead-other main process (320) terminated with status 5. It started happening completely randomly, is this anything I should be worried about and can I fix it?

When I try and run ureadahead I get this:

brandon@brandon-laptop:~$ sudo ureadahead -v
/var/lib/ureadahead/pack: No such file or directory
ureadahead: Error while tracing: No such file or directory
brandon@brandon-laptop:~$

Am running lucid 64 bit.

---

### Post by john newbuntu on 2010-05-05
Open /etc/fstab and check if all mount points/UUIDs are ok.  Please go through:
[http://ubuntuforums.org/showthread.php?t=1423305](http://ubuntuforums.org/showthread.php?t=1423305)

---

### Post by screaminj3sus on 2010-05-06
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a999137a-edb7-406f-8111-a61aa929ee0f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=442b517c-4243-4f99-a637-360e86057b52 none            swap    sw              0       0

All thats in my fstab is my main and swap partitons which are both obviously working correctly :/

I've googled around and all ive found are people who had /var on other partitions or a windows drive not mounting. I only have my ubuntu part and swap in fstab and no seperate home or /var or anything.

EDIT: just checked the UUID's and they match up as well.

---

### Post by john newbuntu on 2010-05-06
Reboot once and see if the /var/lib/ureadahead/pack file shows up. Check blkid's in fstab with the those from the command: "sudo blkid -c /dev/null".  Also check if swap is being used using " swapon -s".

---

### Post by screaminj3sus on 2010-05-06
Here is the first command, ids seem to match. > brandon@brandon-laptop:~$ sudo blkid -c /dev/null
[sudo] password for brandon: 
/dev/sda1: LABEL="System Reserved" UUID="DA983FF6983FCFAD" TYPE="ntfs" 
/dev/sda2: UUID="F652467E52464399" TYPE="ntfs" 
/dev/sda5: UUID="a999137a-edb7-406f-8111-a61aa929ee0f" TYPE="ext4" 
/dev/sda6: UUID="442b517c-4243-4f99-a637-360e86057b52" TYPE="swap" 

here is the swapon result:
> brandon@brandon-laptop:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	2170876	0	-1
brandon@brandon-laptop:~$ 





EDIT: and rebooting did not fix it, there is no pack file.

Guess its really not a huge deal though, it still boots fine and its only a couple seconds longer.

---

### Post by john newbuntu on 2010-05-06
The whole idea of ureadahead is to cache data and speed up boot.  Anyway, try this one more time and reboot twice:
sudo ureadahead --force-trace --debug

I see a launchpad bug on this, which is where I got the above command from:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/542334](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/542334)
[https://answers.launchpad.net/ubuntu/+source/ureadahead/+question/101643](https://answers.launchpad.net/ubuntu/+source/ureadahead/+question/101643)

---

### Post by slickvguy on 2010-06-05
I've got the same problem. And I don't have a separate var or home partition either. Just your simple, basic Lucid setup: ext4 / and swap. UUIDs are all good. Nothing unusual. System boots ok (aside from this error). But...no pack file generated. Just debugfs directory. 

Error status 5 on boot. "error while tracking: no such file or directory".


1) What is it looking for, and 2) why can't it find it?

---

