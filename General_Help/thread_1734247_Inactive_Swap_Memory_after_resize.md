---
title: "Inactive Swap Memory after resize"
date: 2011-04-20
forum: General Help
---

### Post by rez182 on 2011-04-20
I used Gparted to resize the swap area, and doing so changed the UUID so now the swap memory is not activated automatically and hibernation is also inactive. i got some info about this in a previous thread, which became inactive, and could not fix the problem.

the output of **sudo blkid** is:
> sudo blkid
/dev/sda1: UUID="8bcd1749-f82d-4d4a-967d-ee8a3583e8e2" TYPE="ext4" 
/dev/sda5: UUID="e02d4dcf-a064-4e6b-a014-a0d9db55f00f" TYPE="swap" 
(the /dev/sda5's UUID seems to have changed since last time i checked, :S)

output of **gksu gedit /etc/fstab** is:
> gksu gedit /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e02d4dcf-a064-4e6b-a014-a0d9db55f00f none            swap    sw              0       0(i edited the UUID of **fstab** to match the **blkid** just now)

someone in the previous thread asked for the output of **cat /etc/initramfs-tools/conf.d/resume** (but the thread already became inactive so didnt get wat to do with this result
> cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=cdca37ca-6eb0-414e-883a-a5c94d5f9465someone also said to update-initramfs but when i type in **sudo update-initramfs** it asks for more input like this:
> You must specify at least one of -c, -u, or -d.
Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]    Specify kernel version or 'all'
 -c        Create a new initramfs
 -u        Update an existing initramfs
 -d        Remove an existing initramfs
 -t        Take over a custom initramfs with this one
 -b        Set alternate boot directory
 -v        Be verbose
 -h        This message                      

(i made a guess and used **sudo update-initramfs -u** and something happened and dont know what changed)

this is about it, all the info are current.
can someone please help me with this. thanks alot.

---

### Post by rez182 on 2011-04-20
i restarted the after changing the **fstab** and now the swap area is activated automatically, but i cannot resume from hibernation. the pc goes to hibernation but when i start it again, it acts as if i started the pc fresh. i guess i need to update initramfs now to be able to resume from hibernation. how can i do it? using **sudo update-initramfs -?**

---

### Post by plucky on 2011-04-20
> someone in the previous thread asked for the output of cat /etc/initramfs-tools/conf.d/resume (but the thread already became inactive so didnt get wat to do with this result
Quote:
cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=cdca37ca-6eb0-414e-883a-a5c94d5f9465 

You need to edit the file and change the UUID to that specified in the "sudo blkid" command for the swap partition,as that is where it will look to reload the memory from hibernate.

Then run ```
sudo update-initramfs -u -k all
``` to update the initramfs.


Good Luck

---

### Post by rez182 on 2011-04-20
i ran [B]sudo update-initramfs -u -k all
[/B]then restarted the pc, but when i run **cat /etc/initramfs-tools/conf.d/resume** it still shows the previous UUID, basically i guess that means the update didnt work. did i miss something or do somethin wrong?

---

### Post by plucky on 2011-04-20
You need to edit the file and change it manually.

```
gksudo gedit /etc/initramfs-tools/conf.d/resume
``` just as you did with the fstab file,then run the update-initramfs command.

---

### Post by rez182 on 2011-04-20
thanks alot man. you have been a great help. i don know why but hibernation does not seem to work still. all the UUIDs match in fstab, blkid, initramfs. i did everything properly this time. i dont know wat to do anymore.

the current outputs of blkid, fstab, initramfs are:
> **sudo blkid**

/dev/sda1: UUID="8bcd1749-f82d-4d4a-967d-ee8a3583e8e2" TYPE="ext4" 
/dev/sda5: UUID="e02d4dcf-a064-4e6b-a014-a0d9db55f00f" TYPE="swap" 


**gksu gedit /etc/fstab**

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e02d4dcf-a064-4e6b-a014-a0d9db55f00f none            swap    sw              0       0


**cat /etc/initramfs-tools/conf.d/resume**

RESUME=e02d4dcf-a064-4e6b-a014-a0d9db55f00f

i updated the initramfs with **sudo update-initramfs -u -k all** after editing manually then restarted the pc and tried hibernation. no apps which were open were resumed. its getting frustrating.

sorry for all the trouble...

---

### Post by plucky on 2011-04-20
What is the output for ```
free -m
``` in a terminal?

---

### Post by rez182 on 2011-04-20
result for **free -m**
>              total       used       free     shared    buffers     cached
Mem:          2012       1280        731          0        308        554
-/+ buffers/cache:        417       1594
Swap:         2353          0       2353


---

### Post by plucky on 2011-04-20
That is fine,just checking swap was greater than installed memory.

Can't think of anything else that needs to be set up to get hibernation working.

---

### Post by rez182 on 2011-04-20
thanks alot for all ur help, guess ill post in launch pad n see if they know anything about it.

---

