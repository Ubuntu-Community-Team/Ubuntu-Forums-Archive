---
title: "problems unmounting a cdrom"
date: 2009-07-26
forum: General Help
---

### Post by bjdonhauser on 2009-07-26
Q: How do I get a mounted cdrom (which is now useless) to go permanently when "eject volume" only works for the duration of my session?

I'm running Ubuntu 9.0.4 as a VM via Sun's VirtualBox. Their GuestAdditions cdrom was mounted and displayed on my desktop. I installed the GuestAdditions and everything worked wonderfully. I selected "eject volume" from the right-click menu on the "VBOXADDITIONS_3.0.2_49928" icon appearing on my desktop. It then disappears from my desktop. Wonderful. I restart the VM. There it is again. It won't go away! Fine, so I tried something else.

In my /etc/fstab file I found:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I then "ejected volume" and commented this line out (with root priveleges). Restart. There's "VBOXADD.." showing up on my desktop AGAIN.

What's going on? I'm almost certain that the cdrom doesn't need to still be there after I've already installed the guest additions. I suppose there's always the "rm" option...but I figure that's poor practice

---

### Post by ridetheteapot on 2009-07-26
I dunno virtualbox that well... but is that guestadditions actually a cd?
type mount in the terminal, and see what device the guestadditions is mounted on. if its on /dev/cdrom0 then thats wierd -- but its probably not. 
if its just a disc image, then its being mounted by virtualbox itself - check options for a virtual cdrom and delete the entry for guestadditions.

even if thats not the problem uncomment that line is fstab, its just for mounting a cdrom normally.

---

### Post by bjdonhauser on 2009-07-26
> **ridetheteapot said:**
> I dunno virtualbox that well... but is that guestadditions actually a cd? 

It's an iso

> **ridetheteapot said:**
> 
type mount in the terminal, and see what device the guestadditions is mounted on. if its on /dev/cdrom0 then thats wierd -- but its probably not. 

it is


> **ridetheteapot said:**
> 
if its just a disc image, then its being mounted by virtualbox itself - check options for a virtual cdrom and delete the entry for guestadditions. 

hmm, not really sure how to go about this. and just to check, a 

```
 rm -r /media/cdrom0 
``` would be a bad idea right?

---

### Post by ridetheteapot on 2009-07-29
yea don't do that.

hey what device is it using anyway? whats the output of mount.

i think its probably being mounted by virtualbox itself, so double check its device options (not in linux, but the setting for that virtual machine).

---

### Post by bjdonhauser on 2009-08-01
> **ridetheteapot said:**
> yea don't do that.

hey what device is it using anyway? whats the output of mount.

i think its probably being mounted by virtualbox itself, so double check its device options (not in linux, but the setting for that virtual machine).

bingo. you got it :) virtual box was actually mounting it each time. all i needed to do was uncheck that option in virtual box after installing the first time. 

thanks for the help!

---

