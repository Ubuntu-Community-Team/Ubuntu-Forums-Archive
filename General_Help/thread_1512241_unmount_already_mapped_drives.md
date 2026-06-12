---
title: "unmount already mapped drives"
date: 2010-06-17
forum: General Help
---

### Post by chrismitt2002 on 2010-06-17
how do u unmount already mounted mapped drives

---

### Post by Boondoklife on 2010-06-17
> **chrismitt2002 said:**
> how do u unmount already mounted mapped drives

Can you give a little more info about your setup? How did you mount them? If you just used nautilus to browse to the share and mount it, then just right click on the mounted mounter under computer and click unmount.

---

### Post by chrismitt2002 on 2010-06-17
here is the command i used 

sudo smbmount //192.168.1.2/D /media/D -o username=owner ,password=mypassword,uid-1000,mask000
same with all other shared drives hope this is enough info

---

### Post by Boondoklife on 2010-06-17
Well I don't use that to mount mine, and not gonna install other samba stuff as it may tweak my box in some odd unforeseeable way that will have me cursing until the wee hours of the morning.

With that said, I think umount or smbumount would do it for you (assuming you have proper permissions). Why not just use nautilus to browse and mount?

---

### Post by chrismitt2002 on 2010-06-18
both say command not found

---

### Post by bodhi.zazen on 2010-06-18
```
sudo umount /media/D
```There is only one n in umount (umount not unmount).

FYI, in Linux you are mounting a samba share. I understand it is called mapping a network drive in Windows, but not many on these forums understand what you are asking.

Also Linux does not use letters to refer to partitions or samba mounts, you may use any name you like in the mount point.

I am just saying you are going to find you receive help faster if you use "proper" terminology.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

So rather then ask for help mapping a drive, ask for help with samba.

Rather then asking about drive D , ask about a samba share or the proper partition (ie I need help mounting my ntfs partition rather then I need help mounting C ).

HTH, and welcome to Ubuntu / Linux.

Oh, smbmount is "depreciated" , Linux now uses "cifs" , so again mount -t cifs rather then smbmount , same thing (you are using the samba protocol).

[http://en.wikipedia.org/wiki/Smbmount](http://en.wikipedia.org/wiki/Smbmount)

As you can see at the bottom of that page "In [Red Hat Enterprise Linux]("http://en.wikipedia.org/wiki/Red_Hat_Enterprise_Linux") 5 smbmount  command has been replaced by [mount.cifs]("http://linux.die.net/man/8/mount.cifs")" , well all Linux distros are moving in that direction ....

For details on that, see the Samba home page.

For additional information on mount (cifs) options see

[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)

---

### Post by Boondoklife on 2010-06-18
> **bodhi.zazen said:**
> There is only one n in umount (umount not unmount).


 LOL, you had me looking and thinking I put that dreaded second 'n' in there.

---

