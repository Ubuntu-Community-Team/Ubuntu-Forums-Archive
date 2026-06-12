---
title: "mount folder to different folders"
date: 2011-04-22
forum: General Help
---

### Post by Add1cken on 2011-04-22
hey, I'm not an expert on Linux or ubuntu.

I just sat up an openSSH Server with Samba access and all, but don't think about that...

here's my question, and as you read you may understand why I posted this instead of googling it, it's un-google-able.

can I mount a regular folder like /media/disk1/random

to 2 different places ? and if so
here's the tricky part:

1: when I end up in that folder, I don't want the direction path to end up like this: /media/disk1/random
IE: so I don't want a link to the other folder, I want the OS to think it's a regular folder (in lames terms)

the reason is because I want my openSSH clients to move inside a small space, without jumping all over the place, and be able to use the (...) feature in the SFTP client. 
(don't think about the permissions their already set.)

2: I don't want it to be a synchronized folder, I want the data to be stored on /media/disk1/random

or else it kind of blows the whole file storage server idea straight out of the window.

---

### Post by earthpigg on 2011-04-22
yup, that is doable. several ways of doing it - mounting may be the most awkward.

have you looked at 'symbolic links'?

---

### Post by Add1cken on 2011-04-23
> **earthpigg said:**
> yup, that is doable. several ways of doing it - mounting may be the most awkward.

have you looked at 'symbolic links'?

heh, yes, and they doesn't fit my need, check criteria nr. 1

anyways, if you know a solution that would fit both my criterias, that would be great.

thnx for the quick reply anyways.

---

### Post by fdrake on 2011-04-23
> **Add1cken said:**
> heh, yes, and they doesn't fit my need, check criteria nr. 1

actually with symbolic links you will have a new directional path depending on where you put your link, if I did understand what you mean..

or you can just run mount 2 twice
mount -t typeOfFile /dev/deviceName /path/to/directory/1

mount -t typeOfFile /dev/deviceName /path/to/directory/2

---

### Post by Add1cken on 2011-04-23
> **fdrake said:**
> actually with symbolic links you will have a new directional path depending on where you put your link, if I did understand what you mean..

or you can just run mount 2 twice
mount -t typeOfFile /dev/deviceName /path/to/directory/1

mount -t typeOfFile /dev/deviceName /path/to/directory/2

hmm, maybe, but i want to mount a folder to several folders :)
so no types of files.


so let me try to explain it better:

here's the original folder:
/media/disk1/pictures

and here's the mounted destination: (mounted from /media/disk1/pictures):
/home/add1cker/pictures

the other mounted destination: (mounted from /media/disk1/pictures):
/home/testuser/pictures.

when I enter the folder and look up the path, I want it to show:
/home/add1cken/pictures

but when i save files, i want the files to be saved on the disk1/pictures, but still accessible from /home/add1cken/pictures.

and when i save pictures in that folder, i want it to be accessible from /home/testuser/pictures aswell.


did this clear it up ?
I can't really explain it in any other way...

---

### Post by ~Plue on 2011-04-23
```
mount -o bind /media/disk1/pictures /home/add1cker/pictures
mount -o bind /media/disk1/pictures /home/testuser/pictures
```when you're done, *umount /home/add1cker/pictures* etc....
if you want to add a fstab entry to auto-mount at startup, it should look like
```
/media/disk1/pictures /home/add1cker/pictures none defaults,bind 0 0
```(that should be after the line for /media/disk1)

---

### Post by Morbius1 on 2011-04-23
@~Plue, I use your method and recommend it to others but I have noticed an odd bug when I add the equivalent lines in fstab. I get errors at boot as it seems the bind expression is occurring before the mounting of the partition it's binding from. There's an actual bug report somewhere in my notes which I cannot find at the moment so I started putting it in rc.local instead - before the "exit 0" line.

Have you experienced this phenomenon?

I have also created my own upstart job to do this that stipulates that the bind will not occur untill all the standard partitions are mounted first.

---

### Post by ~Plue on 2011-04-23
i've been using that method for some time too, but haven't experienced what you described..(on arch and a natty test machine)
it spits some errors and doesn't mount if i move the line before the actual drive though

//out of curiosity; if you find the bug report, please let me know

---

### Post by Add1cken on 2011-04-23
> **~Plue said:**
> ```
mount -o bind /media/disk1/pictures /home/add1cker/pictures
mount -o bind /media/disk1/pictures /home/testuser/pictures
```when you're done, *umount /home/add1cker/pictures* etc....
if you want to add a fstab entry to auto-mount at startup, it should look like
```
/media/disk1/pictures /home/add1cker/pictures none defaults,bind 0 0
```(that should be after the line for /media/disk1)

thanks verry much !!!
that worked perfectly, exactly what I was looking for.
and thanks for the auto-mount advice, I also needed that.

thread solved !

---

### Post by Morbius1 on 2011-04-23
> **~Plue said:**
> //out of curiosity; if you find the bug report, please let me know
I think this is the one I was thinking about:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/519380](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/519380)

In any event it's a problem for me every time I've tried it in fstab which is why I ended up just creating an upstart job to do it.

---

### Post by Add1cken on 2011-04-25
@~Plue heh, i tried adding the mount entries in the /etc/fstab

looks like this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=87bb1867-a60a-4e20-bb28-ad1e3c8a55fa /               ext4    errors=remount-ro,user_xattr 0       1
/dev/sda1       none            swap    sw              0       0

```


i tried adding the lines at the end of the text file:
```

/media/Diverse/mountme /home/addicken/Desktop/mounted/1 none defaults,bind 0 0
/media/Diverse/mountme /home/addicken/Desktop/mounted/2 none defaults,bind 0 0

```
i'm getting an error at startup:
press S or wait, to skip mounting, or M for manual recovery.

even if i add the line which adds the partition where the mount point is located (before my other mount entries ofc.)
```
/dev/sda4       /media/Diverse  Ext4    0               0       0
```it still shows the error and doesn't mount...



can i use another method for mounting automatically at startup ?
or can i fix this, and how ?

---

### Post by Morbius1 on 2011-04-25
> /dev/sda4       /media/Diverse  Ext4    0               0       0I don't think that line will mount properly as is. Try this:
```
/dev/sda4 /media/Diverse ext4 defaults 0 0
```And it must precede the bind lines in fstab.

Also to save wear and tear on your system, use the following command when you make changes to fstab:
```
sudo mount -a
```The true test is an actual reboot but if there are errors "sudo mount -a" will tell you.

---

### Post by 1clue on 2011-04-25
One thing that concerns me, you are putting your real folder in /media.  This is generally reserved for the automatically mounted volumes, so are you using a CDROM or some other removable device for that?

Another thing:  If you have multiple writers, you might have file permissions problems using a strategy like this, or have a bunch of people who have sudo access who shouldn't.

---

