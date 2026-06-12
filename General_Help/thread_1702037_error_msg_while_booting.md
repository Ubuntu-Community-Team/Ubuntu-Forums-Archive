---
title: "error msg while booting"
date: 2011-03-07
forum: General Help
---

### Post by brothersman on 2011-03-07
When I boot i get this error,
 "the disk drive for /windows is not ready yet or not present"

I have been searching these other forums on this site and others sites and cant find any solution

I am running Lucid Lynx

---

### Post by Habitual on 2011-03-07
Do you have a Windows partition? (dual booting)?

Please give us the output of 
```
cat /etc/fstab
```

and 
```
df -h
```
and
```
sudo blkid 
```

Thank you

---

### Post by brothersman on 2011-03-07
> **Habitual said:**
> Do you have a Windows partition? (dual booting)?

Please give us the output of 
```
cat /etc/fstab
```

and 
```
df -h
```
and
```
sudo blkid 
```

Thank you



I did have it dual boot at one time but not anymore

codes


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/sda1       /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda6 during installation
UUID=3D3C-97F3  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=cd06ee47-9f6a-4622-bf23-5d920e98a621 none            swap    sw              0       0
/dev/sda1 / ext4 errors=remount-ro,user_xattr 0 1
---------------------------------------------------------

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             367G   86G  263G  25% /
none                  1.5G  348K  1.5G   1% /dev
none                  1.5G  1.9M  1.5G   1% /dev/shm
none                  1.5G  196K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
-----------------------------------------------------------

/dev/sda1: UUID="3e47fc04-0faf-4344-87d2-2bbca9d4bc62" TYPE="ext4" 
/dev/sda5: UUID="cd06ee47-9f6a-4622-bf23-5d920e98a621" TYPE="swap" 
/dev/sda6: UUID="4C0EFFE80EFFC94A" TYPE="ntfs"

---

### Post by tredegar on 2011-03-07
The entries in **fstab** should be consistent with, and match the output of **blkid**, if you are going to refer to drives by their UUIDs (a good idea).
They aren't. In fstab : ```
# /windows was on [COLOR="DarkGreen"]/dev/sda6[/COLOR] during installation
[COLOR="Red"]UUID=3D3C-97F3[/COLOR] /windows [COLOR="Blue"]vfat[/COLOR] utf8,umask=007,gid=46 0 1
```

But from blkid :```
[COLOR="DarkGreen"]/dev/sda6[/COLOR]: [COLOR="Red"]UUID="4C0EFFE80EFFC94A[/COLOR]" TYPE="[COLOR="Blue"]ntfs[/COLOR]" 
```

Also you need to specify the correct filesystem type in fstab, currently listed as vfat, but looks like it should be ntfs

How did you get into this mess?

---

### Post by brothersman on 2011-03-07
> **tredegar said:**
> The entries in **fstab** should be consistent with, and match the output of **blkid**, if you are going to refer to drives by their UUIDs (a good idea).
They aren't. In fstab : ```
# /windows was on [COLOR="DarkGreen"]/dev/sda6[/COLOR] during installation
[COLOR="Red"]UUID=3D3C-97F3[/COLOR] /windows [COLOR="Blue"]vfat[/COLOR] utf8,umask=007,gid=46 0 1
```

But from blkid :```
[COLOR="DarkGreen"]/dev/sda6[/COLOR]: [COLOR="Red"]UUID="4C0EFFE80EFFC94A[/COLOR]" TYPE="[COLOR="Blue"]ntfs[/COLOR]" 
```

Also you need to specify the correct filesystem type in fstab, currently listed as vfat, but looks like it should be ntfs

How did you get into this mess?


I have not clue, whats do i do next?

---

### Post by Habitual on 2011-03-07
Alt+F2 and run this, or run this from terminal:
```
gksu gedit /etc/fstab
```

Stick a # in front of 
```
UUID=3D3C-97F3 /windows vfat utf8,umask=007,gid=46 0 1 
```
so it is like this:
```
# UUID=3D3C-97F3 /windows vfat utf8,umask=007,gid=46 0 1
```

Save upon exit, or save then exit, or exit with save and reboot.

Message should be gone.

---

### Post by brothersman on 2011-03-08
everything worked great, thank you

---

### Post by Habitual on 2011-03-08
Glad it worked out.

---

