---
title: "DPKG  for a dead system?"
date: 2011-08-11
forum: General Help
---

### Post by Robbyx on 2011-08-11
How do I adjust the **dpkg --get-selections >installed** so that it tells me about a linux installation that is not active.

Currently I can not load the original installed Ubuntu on the HD and am using the live CD. **How do I extract the list of installed applications for the system on the hard disk **

---

### Post by TeoBigusGeekus on 2011-08-11
I'd try looking at /bin, /sbin, /usr/bin for starters.

---

### Post by Robbyx on 2011-08-11
I would like to use the dpkg approach because I  can then reverse the procedure into a clean installation. However I do not know how to make dpkg look at the installation on the HD which is not in use, assuming I run dpkg from with the live cd, is there a synatax which makes it look at the old installation instead of the one set up by the liveCD.

---

### Post by gmargo on 2011-08-11
You'll need to mount the partition containing the other root file system, and use the **--admindir** option on **dpkg(1)** to point to it.

From the **dpkg(1)** man page:
> 
       --admindir=dir
              Change default administrative directory, which  contains  many  files  that  give  information  about  status  of
              installed or uninstalled packages, etc.  (Defaults to /var/lib/dpkg)


---

### Post by Robbyx on 2011-08-11
Do you think this would work from the livecd terminal?

sudo dpkg ----admindir=sda1/var/lib/dpkg --get-selections >sda1/robin/oldpackage.selections

sda1 is the partition with the original installation that needs a clean install.

---

### Post by cbowman57 on 2011-08-11
If you manage to access & mount the HDD installation you might find this useful.

[http://www.coredump.gr/linux/debian-package-list-backup-and-restore/](http://www.coredump.gr/linux/debian-package-list-backup-and-restore/)

---

### Post by Robbyx on 2011-08-11
> **cbowman57 said:**
> If you manage to access & mount the HDD installation you might find this useful.

[http://www.coredump.gr/linux/debian-package-list-backup-and-restore/](http://www.coredump.gr/linux/debian-package-list-backup-and-restore/)

Thank you for this reference. I am not sure how to use it in my situation where I am trying to extract a list of programs installed on the original linux operating system using the liveCD.

As asked above would the following do what I want and does it have the right syntax for the file locations?

sudo dpkg ----admindir=sda1/var/lib/dpkg --get-selections >sda1/robin/oldpackage.selections


I really am not clear if my command line using admindir will only look at the operating system on sda1 and ignore the liveCD created os.

---

### Post by cbowman57 on 2011-08-11
I wish I could say for sure but I'm no command line wizard. :)

I think you can try that without doing any damage though.

To use the link I posted you will likely have to chroot into the installed system, but again, trying to describe how to do that is beyond my ability.  

To get an idea on how to use chroot a good place to look might be how-to restore grub from LiveCD.

Sorry I'm not more help.

---

### Post by gmargo on 2011-08-12
> **Robbyx said:**
> Do you think this would work from the livecd terminal?

sudo dpkg ----admindir=sda1/var/lib/dpkg --get-selections >sda1/robin/oldpackage.selections

sda1 is the partition with the original installation that needs a clean install.

From the LiveCD terminal, you just need to mount the hard disk partition first.  Here's how to do it, and write the results back to the hard disk:
```

sudo mkdir /media/sda1
sudo mount -t auto /dev/sda1 /media/sda1/
dpkg --admindir=/media/sda1/var/lib/dpkg --get-selections | sudo tee /media/sda1/home/robin/oldpackage.selections
sudo umount /media/sda1

```The third step retrieves the dpkg info from the mounted hard disk, and then uses "sudo tee" in order to write to the hard disk (since simple redirection will have permission problems.)  Change the "/home/robin" part to put the file wherever you like.

---

### Post by Robbyx on 2011-08-12
> **gmargo said:**
> From the LiveCD terminal, you just need to mount the hard disk partition first.  Here's how to do it, and write the results back to the hard disk:
```

sudo mkdir /media/sda1
sudo mount -t auto /dev/sda1 /media/sda1/
dpkg --admindir=/media/sda1/var/lib/dpkg --get-selections | sudo tee /media/sda1/home/robin/oldpackage.selections
sudo umount /media/sda1

```The third step retrieves the dpkg info from the mounted hard disk, and then uses "sudo tee" in order to write to the hard disk (since simple redirection will have permission problems.)  Change the "/home/robin" part to put the file wherever you like.

The above does not seem to work.

```
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount -t auto /dev/sda1 /media/sda1/
mount: special device /dev/sda1 does not exist

```

Do you think chroot is needed somewhere?

---

