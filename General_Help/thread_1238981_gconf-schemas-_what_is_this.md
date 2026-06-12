---
title: "gconf-schemas- what is this?"
date: 2009-08-13
forum: General Help
---

### Post by monarda22 on 2009-08-13
Hi!

I do this:  sudo dpkg --configure -a

And I get this:
Setting up gthumb (3:2.10.8-0ubuntu1) ...
Warning: /usr/share/gconf/schemas/gthumb.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gthumb

What is it and how do I fix it?

If I do:  fsck -p -v 

I get 
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=e4fc8037-c222-412d-9fe0-8408191a8352'

which may or may not be related but surely isn't good?


Direction???

Thanks

---

### Post by P4man on 2009-08-13
> **monarda22 said:**
> Hi!

I do this:  sudo dpkg --configure -a

And I get this:
Setting up gthumb (3:2.10.8-0ubuntu1) ...
Warning: /usr/share/gconf/schemas/gthumb.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gthumb


Seems like a problem with gthumb :) try 

```
sudo aptitude reinstall gthumb
```

(or remove it if you dont use it anymore).


> 
What is it and how do I fix it?

If I do:  fsck -p -v 

I get 
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=e4fc8037-c222-412d-9fe0-8408191a8352'

which may or may not be related but surely isn't good?


Direction???

I doubt its related, but it looks like the UUID of one of your partitions changed. You probably changed something with the partition editor (made a new partition?) and fstab no longer has the correct UUID. Good idea to fix that.  Get the correct UUIDs by running:

```
sudo blkid
```

Also paste the contents of /etc/fstab

I bet there is a mismatch between them.

---

### Post by monarda22 on 2009-08-13
> **P4man said:**
> Seems like a problem with gthumb :) try 

```
sudo aptitude reinstall gthumb
```

(or remove it if you dont use it anymore).



I thought I tried that, but I will try it again.  I don't know if I use it because I dont' know what it is.  I THINK it is related to the little thumbnail icons I used to have on the dropdown topbar menu for programs in 7.10 that I don't seem to have anymore in 8.04.

I do know that when I tried to add an FTP client, I think it installed (it runs) but it was very upset about gthumb.



> **P4man said:**
> 
I doubt its related, but it looks like the UUID of one of your partitions changed. You probably changed something with the partition editor (made a new partition?) and fstab no longer has the correct UUID. Good idea to fix that.  Get the correct UUIDs by running:

```
sudo blkid
```

Also paste the contents of /etc/fstab

I bet there is a mismatch between them.

I am trying to complete an upgrade from 7.1 to 8.04 so maybe that did it?  I haven't knowingly repartioned anything.

The blkid think I will try. I get the contents of fstab (whatever that is) with gedit?

Thanks for your response.

---

### Post by P4man on 2009-08-13
> **monarda22 said:**
> 
I am trying to complete an upgrade from 7.1 to 8.04 so maybe that did it?  I haven't knowingly repartioned anything.

Not sure, but I suppose it could have something to do with it. I dont remember when grub started using uuid's, maybe its "new" for 8.04.

> 
The blkid think I will try. I get the contents of fstab (whatever that is) with gedit?
Yes. with gedit you can edit it.

```
gksudo /etc/fstab
```

fstab is a file that defines your mountpoints.
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by P4man on 2009-08-13
> **monarda22 said:**
> I thought I tried that, but I will try it again.  I don't know if I use it because I dont' know what it is.  I THINK it is related to the little thumbnail icons I used to have on the dropdown topbar menu for programs in 7.10 that I don't seem to have anymore in 8.04.

I do know that when I tried to add an FTP client, I think it installed (it runs) but it was very upset about gthumb..

Its an image viewer. Not a particularly good one by the looks of it. If you dont use it by launching it manually, you're probably not using it all.

```
sudo apt-get remove gthumb
```

Though I wouldnt be surprised it starts complaining, so post any errors you might get :)

---

### Post by monarda22 on 2009-08-13
```
sudo aptitude reinstall gthumb
```

This resulted in "Segmentation Fault" and required a warm boot.  :(




> 
```
sudo blkid
```

Also paste the contents of /etc/fstab

I bet there is a mismatch between them.


I did "sudo blkid" and got:
/dev/sda1: UUID="e4fc8037-c222-412d-9fe0-8408191a8352" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="47a7c95b-d448-45a5-b07e-b15e828cce9b" 


I did gedit /etc/fstab and got:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e4fc8037-c222-412d-9fe0-8408191a8352 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=47a7c95b-d448-45a5-b07e-b15e828cce9b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



I have no idea what I am looking at.

---

### Post by monarda22 on 2009-08-13
I did a aptitude autoclean and a clean and got rid of old packages.  Then I did the reinstall and that seems to have done the trick.  Gthumb shows up on my menu and I have now installed a text editor and an FTP client without getting yelled at.  So that is good.

Don't know if I need to do anything about the UUID thing or not.

---

### Post by P4man on 2009-08-14
Your fstab is correct. Im probably misreading the error you got initially. Did you try checking the drive while it was mounted? If so, that might explain, and you should never run fsck on a mounted volume (it tells you so). Maybe it even refuses, and thats why it says "unable to resolve...".

---

### Post by monarda22 on 2009-08-14
Thank you for your help.  Somebody else also told me not to run the fsck.  I did becasue it was the only thing I knew how to do.  I'm trying to learn shell commands but I really have no clue.  

I think I am in okay shape at the moment machinewise- it seems to be working!  Thanks!

---

