---
title: "Install /home on secondary ext3 drive"
date: 2010-09-04
forum: General Help
---

### Post by MartinusEx on 2010-09-04
Hi
I'm running lucid.

I want to unmount the current /home from sda7 and mount it to sdb1


I had a look at system -> drives management but just was able to mount the secondary drive sdb1 as "DataDrive"

I had a look at /etc/fstab.
This doesn't show the recently mounted sda7 "DataDrive"

So now I'm somewhat lost on how to achieve the goal

>> What ist the correct way to do it?

Scenario 1.
Copy all contents of /home to the new drive and then switch the /home mount point

Scenario 2. Switch the mount point of /home from sda7 to sdb1 and cp the contents afterwards


>> How do I unmount /home from sda7 and mount it back to the sdb1 (ext3) when lucid doesn't use fstab (does it?) and I don't know where the drives manager stores it's information.

(Just had the idea that I need to use a live cd for not to lock the system drives (sdaN) )

For sure there is a man page or a how to somewhere i didn't just find 
>> A link to such information might be sufficient

Thx for any input

Martinus

---

### Post by gzarkadas on 2010-09-04
You can perform the process without using a live CD, by going to single user (root) mode. This is necessary to avoid loosing updates to files in /home while transferring it to the new partition, something that is possible (depending on the apps you run and your cron jobs) if you try to copy /home and modify your /etc/fstab from within your GUI login.

[B]Preparation:
[/B] 
1. Print this entire post in paper. You *will* need it, as there will be no ability to use your browser while performing the steps described. Make sure that the entire commands are printed. 

2. Verify that all the needed tools are installed on your system: blkid, rsync, awk, sed, grep. They will, most probably, but it is a Good Thing to check beforehand.

3. If your new disk is not properly formatted, do it now, before proceeding below.

**Implementation:**

Reboot in single user mode. Use either method of A or B below:

A. Use the reboot command and upon reboot choose the recent `(recovery)' kernel - typically, the 2nd line of your grub menu. In the menu that appears at the end of the boot process choose `Root shell ...' (with or without networking).

B. Open a terminal and type `sudo telinit 1'.

You are now, after reboot, at a root shell. Be careful. Type the following commands (read them again and verify them before hitting the <ENTER> key):

1. Make a directory and mount new home partition there.
```

mkdir -p /mnt/newhome
mount /dev/sdb1 /mnt/newhome

```2. Copy entire contents of old home to new home, preserving *everything* (aHAX) while staying on the same filesystem (x). The (v) is to see progress; it will take time to complete. The slashes at the end of source, destination *are* important.
```

rsync -vaxHAX /home/ /mnt/newhome/

```3. Unmount both partitions and remove the directory of step #1.
```

umount /mnt/newhome
umount /home
rm -R /mnt/newhome

```4. Modify your /etc/fstab to mount the new partition as /home; comment out the old one. You may delete it afterwards, when you are sure everything is ok.
```

NEWID=$(blkid | grep '/dev/sdb1' | awk '{print $2}' | sed 's/"//g')
cat /etc/fstab | awk '{ if ($0~/^.*[[:space:]]\/home[[:space:]]/) { print "#" $0; sub(/UUID=[0-9a-f\-]*/, "'"$NEWID"'", $0); print $0 } else print $0 }' > /etc/fstab.new
mv /etc/fstab /etc/fstab.old
mv /etc/fstab.new /etc/fstab
chmod 640 /etc/fstab /etc/fstab.old

```The code uses `blkid' to read the UUID of your partitions, `grep' to select the right line and `awk' and `sed' to select the right field and clear the double quotes around the uuid. The result is stored to environment variable NEWID. 

Then your /etc/fstab is processed by an awk script that finds the line containing /home, puts a # to comment it out, duplicate it and change the old uuid value (that of /dev/sda7) to the new one (that of /dev/sdb1). That way your mount options are kept the same. The result is written to a new file, because writing it back to /etc/fstab directly would truncate it (this would be bad!). 

Then a backup of original /etc/fstab is made to /etc/fstab.old - to use it if something goes wrong to restore your system - and the new file replaces /etc/fstab. Lastly, permissions of both files are set as should be (in case your umask changes them).

Note that the double quote/single quote/double quote parts around $NEWID, ie:
```
"'"$NEWID"'"
```are _essential_, because the value of the shell variable is thus entered inline the awk code as if it was a string contained in double quotes.

5. Sync to ensure changes are back to disk and then remount /home to verify the correct setup of your system.
```

sync
mount /home

```6. Issue a ```
mount
``` command without arguments and inspect the output. Navigate (`cd' and `ls -l') through /home and see if everything looks right.

7. Leave the single user mode. Use either method of A or B below:
A. ```
shutdown -r now
```B. ```
telinit 2
```**Restoration (if things go wild):**

If something goes wrong after changing /etc/fstab and rebooting, simply replace the new fstab by the old (backup) and reboot:

```

sudo mv /etc/fstab /etc/fstab.new
sudo mv /etc/fstab.old /etc/fstab
chmod 640 /etc/fstab*

```

---

### Post by dcstar on 2010-09-05
> **MartinusEx said:**
> 
........
Thx for any input

Martinus

And apart from the instructions to set up a separate /home partition, I would personally use an EXT4 partition rather than EXT3.

---

### Post by MartinusEx on 2010-09-05
> **gzarkadas said:**
> gzarkadas : Your Deskripton 
Oh boy, thats quite indepth.
I'll need some time to get that understood and done.
I surely report back to you when I'm through

Thanks so far 

Martinus

---

### Post by MartinusEx on 2010-09-05
> **dcstar said:**
> And apart from the instructions to set up a separate /home partition, I would personally use an EXT4 partition rather than EXT3.

Jep, that's what I did actually. 
(It's already ext4 but I quoted the wrong  partition type)

Anyway, you're  comment is greatly appreciated and I thank you very much

Rgds

Martinus

---

### Post by MartinusEx on 2010-12-23
At least I did it.
I am a lazy boy so I used the ubuntu live CD to edit fstab and to mount/umount the drives.

The most important point was to log in on the recovery kernel
and use rsync to copy ALL data to the new location.
Also I used this to enhance the /usr drive space

One tip for the searching visitor:
If you log in via grub, your are asked to log in as root.
You might not remember because you never was asked to, that you never gave a root password therefor, you do not know one and cannot login as root.

As I found out, this is quite the ubuntu approach.
No one enters the system as root, the password is a some kind of hashcode.
You always enter as yourself and do things via sudo or su
You can always reset the root password via passwd if you want to, but sudo and su do all the work as well.


You need to presss Ctrl D at the point where the system asks you for the root passwd.

By some reason from my account "sudo telinit 1" did not do what I expected, i found myself at the login again after a reboot??!!
hmm, i don't think gzarkadas gave wrong advice, I rather think, i did something wrong, such as i later reset the root password and after that i did all things from the root account.

All in All gzarkadas, your advice showd me off and I'm very gratefull alhtough I did not use the elaborate scripting.
At least it was a real education
Again thx a lot.



Martinus :popcorn:

---

