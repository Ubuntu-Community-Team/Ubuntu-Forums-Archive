---
title: "NTFS partition renamed"
date: 2010-10-21
forum: General Help
---

### Post by SuperFreak on 2010-10-21
I am dual booting with XP.I have a an NTFS disk that I want Ubuntu to access as the disk name I gave it in Windows (Music) but I am finding that on boot I get an error message "the disk drive for media/music  is not ready or is not present. Press S to skip...." When I press S Ubuntu loads up and my Music disk is usually mounted but if I go into my media folder it is renamed Music_ . It occurs to me there is another folder under "Places" called "Music" ; could this be the reason Ubuntu is running into difficulties with my NTFS disk.
I really do not want to rename my Music disk in Windows as that will cause problems with my Windows programs. Would deleting the unused Music  directory (not my NTFS directory)in Ubuntu solve this or is the problem elsewhere.

---

### Post by coffeecat on 2010-10-21
Post the output of these three terminal commands. They should give us the information we need to see what is going wrong.

```
cat /etc/fstab
ls -l /media
sudo blkid
```

---

### Post by SuperFreak on 2010-10-21
cat /etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda5	/	ext4	errors=remount-ro	0	1
/dev/sda6	/home	ext4	defaults	0	2
/dev/sda8	/media/Data	ntfs-3g	defaults,locale=en_CA.utf8	0	0
/dev/sdc5	/media/Music_	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sda1	/media/sda1	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sdb5	/media/Music	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.utf800
/dev/sda7	none	swap	sw	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0


ls -l /media
total 48
drwx------ 2 root root  4096 2010-10-13 15:58 1AF0C12DF0C11045
drwxrwxrwx 1 root root 16384 2010-10-19 15:44 Data
lrwxrwxrwx 1 root root     7 2010-10-10 13:25 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2010-10-10 13:25 floppy0
drwxr-xr-x 3 root root  4096 2010-10-13 20:10 Music
dr-xr-xr-x 1 root root  4096 2010-10-20 11:06 Music_
dr-xr-xr-x 1 root root 16384 2010-10-21 12:00 sda1

sudo blkid
/dev/sda1: UUID="1AF0C12DF0C11045" TYPE="ntfs" 
/dev/sda5: UUID="de7ae6f4-eeb3-4525-9849-7a2f0ef26bf5" TYPE="ext4" 
/dev/sda6: UUID="fd6d0724-d226-43b3-bc98-2b00368cf1e4" TYPE="ext4" 
/dev/sda7: UUID="4d6b6326-7d4a-472b-8ce5-5e531c90cd52" TYPE="swap" 
/dev/sda8: LABEL="Data" UUID="566C0AE26C0ABD2D" TYPE="ntfs" 
/dev/sdc5: LABEL="Music" UUID="01CB1E0382AC3490" TYPE="ntfs"

---

### Post by coffeecat on 2010-10-21
There is no sdb in your blkid, but an sdc. What happened to sdb?

Anyway, I guess this is an oddity caused by your BIOS, because drives are usually named sequentially.

You have a line in /etc/fstab which refers to a non-existent partition and which is malformed:

> **SuperFreak said:**
> ```
/dev/sdb5    /media/Music    ntfs-3g    defaults,nosuid,nodev,locale=en_CA.utf800
```

Fields 5 and 6, both of which would be '0', are missing.

Additionally your sdc6 is mounted to /media/Music_ ...

> **SuperFreak said:**
> ```
/dev/sdc5    /media/Music_    ntfs    defaults,nls=utf8,umask=0222    0    0
```... but its label is 'Music' ...

> **SuperFreak said:**
> ```
/dev/sdc5: LABEL="Music" UUID="01CB1E0382AC3490" TYPE="ntfs"
```

Unless sdb5 is going to reappear somehow, you need to remove the sdb5 line from fstab. While you're about it, I suggest you edit the sdc5 line so that it is mounted to /media/Music, thusly:

```
 /dev/sdc5    /media/Music    ntfs    defaults,nls=utf8,umask=0222    0    0
```Much more tidy. Do you need any help with that?

By the way, if sdb and/or sdc are going to come and go and/or change their designations for whatever reason, you might want to use UUIDs in /etc/fstab.

---

### Post by SuperFreak on 2010-10-21
Do I use the gedit etc/fstab command and make all the changes in fstab?


Edit when I use that command I get an empty window for fstab (see thumbnail). Also the fstab file appears to be in the home/david/etc directory; is that correct or should it be file/etc/fstab?

---

### Post by sisco311 on 2010-10-21
> **coffeecat said:**
> There is no sdb in your blkid, but an sdc. What happened to sdb?

Anyway, I guess this is an oddity caused by your BIOS, because drives are usually named sequentially.

Nope, device names may change between system boots. 

From the [archlinux wiki]("http://wiki.archlinux.org/index.php/Udev"):
> 
udev loads kernel modules by utilizing coding parallelism to provide a potential performance advantage versus loading these modules serially. The modules are therefore loaded asynchronously. The inherent disadvantage of this method is that udev does not always load modules in the same order on each boot. If the machine has multiple block devices, this may manifest itself in the form of device nodes changing designations randomly. For example, if the machine has two hard drives, /dev/sda may randomly become /dev/sdb.

That's why one should use UUIDs or LABELs: [uhelp]community/UsingUUID[/uhelp]

---

### Post by sisco311 on 2010-10-21
> **SuperFreak said:**
> Do I use the gedit etc/fstab command and make all the changes in fstab?


Edit when I use that command I get an empty window for fstab (see thumbnail). Also the fstab file appears to be in the home/david/etc directory; is that correct or should it be file/etc/fstab?

fstab is in /etc, you missed the leading / from the path:
```
gksu gedit /etc/fstab
```

---

### Post by coffeecat on 2010-10-21
> **sisco311 said:**
> Nope, device names may change between system boots. 

Interesting - I've never seen that on any of my machines. Nevertheless....

> **sisco311 said:**
> That's why one should use UUIDs or LABELs: [uhelp]community/UsingUUID[/uhelp]

Agreed.

---

### Post by SuperFreak on 2010-10-21
Thanks Coffeecat. but...
First reboot go same error message "the disk drive for media/music is not ready or is not present. Press S to skip...." . I press S and the Music disk is not mounted. Second reboot it goes straight through boot and Music is mounted as it should. Third boot get error message again. If I were to add these UUIDs would the disk mount properly and the error message disappear. I will look at the page you linked me to more carefully later this evening and add the UUID tags

---

### Post by coffeecat on 2010-10-21
Actually, it was sisco311 who posted the link but, yes, it should work reliably with UUIDs.

It does sound as though the sdb/sdc designation is changing from boot to boot. So long as you have just one NTFS partition in fstab mounted to the correct mountpoint, you should avoid those errors.

Be very careful when adding your UUIDs to fstab. To avoid the possibility of a typo, use a copy and paste from the output of 'sudo blkid'.

---

### Post by SuperFreak on 2010-10-21
Thanks sisco311

---

