---
title: "Swap Memory Stays Inactive"
date: 2011-04-12
forum: General Help
---

### Post by rez182 on 2011-04-12
i have 2gm RAM and 2.3 gb Swap. for some reason my swap memory does not activate on its own, i have to activate it manually from gparted each time i start ubuntu.

i did a fresh reinstall from scratch yesterday and created 2gb swap from installation disk. swap was activated automatically then. but hibernation did not work, so i increased swap to 2.3gb but didnt try hibernate yet, pretty sure it wont work. but the problem now is swap stays inactive in each boot.

why is this happening? how can i fix this? should i ask this question in launchpad.net?

thanks.

---

### Post by TeoBigusGeekus on 2011-04-12
Activate your swap and post us the output of
```
sudo blkid
```
and the contents of your fstab file
```
gksu gedit /etc/fstab
```
If you haven't used UUIDs in fstab, perhaps increasing swap via gparted changed its UUID and it's now not recognized by your system.

---

### Post by rez182 on 2011-04-12
Results for sudo blkid:

/dev/sda1: UUID="8bcd1749-f82d-4d4a-967d-ee8a3583e8e2" TYPE="ext4" 
/dev/sda5: UUID="c2b167db-7250-4d6a-900f-3e1d3cf599fb" TYPE="swap"

Results for gksu gedit /etc/fstab:

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
UUID=cdca37ca-6eb0-414e-883a-a5c94d5f9465 none            swap    sw              0       0

---

### Post by mc4man on 2011-04-12
If you look you'll see the UUID's for swap are different
When you changed your swap it's UUID changed, so the one in fstab is now incorrect. Edit the entry in fstab to reflect the current one, as in

```
UUID=c2b167db-7250-4d6a-900f-3e1d3cf599fb
```
just edit the UUID=, the rest of the line is good

---

### Post by plucky on 2011-04-12
If you want to hibernate,and your uuid has changed,you also have to change **etc/initramfs-tools/conf.d/resume** to reflect the change in the UUID.

Please post output of ```
cat /etc/initramfs-tools/conf.d/resume
```

Good Luck

---

### Post by QLee on 2011-04-12
and don't forget to run an update-initramfs after putting the correct UUID in the config.

---

### Post by rez182 on 2011-04-13
> plucky 	 		**Re: Swap Memory Stays Inactive**
 		If you want to hibernate,and your uuid has changed,you also have to change **etc/initramfs-tools/conf.d/resume** to reflect the change in the UUID.

Please post output of  	Code:
 	cat etc/initramfs-tools/conf.d/resume 

Output is:
cat: etc/initramfs-tools/conf.d/resume: No such file or directory. :S

> mc4man 	 		**Re: Swap Memory Stays Inactive**
 		If you look you'll see the UUID's for swap are different
When you changed your swap it's UUID changed, so the one in fstab is now  incorrect. Edit the entry in fstab to reflect the current one, as in

 	Code:
 	UUID=c2b167db-7250-4d6a-900f-3e1d3cf599fb 
just edit the UUID=, the rest of the line is good 	  	


Changed and saved it.

> QLee 	 		**Re: Swap Memory Stays Inactive**
 		and don't forget to run an update-initramfs after putting the correct UUID in the config. 	
How do i  run an update-initramfs?

---

### Post by plucky on 2011-04-14
> Output is:
cat: etc/initramfs-tools/conf.d/resume: No such file or directory. :S

Sorry I forgot to put a / in front of etc.I have corrected my other post as it is now ```
cat /etc/initramfs-tools/conf.d/resume
```

> How do i run an update-initramfs? 

From a terminal ```
sudo update-initramfs
```

Good Luck

---

### Post by burton61 on 2011-04-14
i ran into the same problem when i wanted to update my swap memory. followed the walktrhu and it worked !!!
thanks

---

### Post by rez182 on 2011-04-18
@plucky

sorry for the late reply, for some reason i could not access this thread from my mail, nor could i see this thread in my subscription list :S.

anyways the result for
cat /etc/initramfs-tools/conf.d/resume
is:
RESUME=UUID=cdca37ca-6eb0-414e-883a-a5c94d5f9465
i changed the UUID from fstab but the above UUID shows the previous UUID still.

and when i updated the initramfs using the code **sudo update-initramfs** it ask for more like
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
please help

EDIT: i selected "-u" eg: sudo update-initramfs -u
it then did something but nothing really happened.

---

### Post by rez182 on 2011-04-18
its getting a little confusing, if possible please type in all the steps in one post in orderly fashion. it would be a great help. thanks..

---

