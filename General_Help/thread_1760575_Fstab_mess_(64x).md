---
title: "Fstab mess (64x)"
date: 2011-05-17
forum: General Help
---

### Post by whynot on 2011-05-17
Hi Everyone

I have a huge problem. I changed my fstab file because of i need to extact rar files that includes other language characters encodings so i have read in internet somewhere that i need to add ```
,utf8
``` this parameter to fstab file. But after i add this parameter i get this error and it won't load gnome desktop.
```

An error occurred while mounting /
Press S to skip mounting or M for manual recovery

```
I tried with S and M options but im no longer able to be a root user.Im only in [COLOR="DarkRed"]read only mode[/COLOR]. I have no root authorization. And this commands don't let me to be root user.
```

sudo gedit /etc/fstab
sudo mc
sudo nano -w /etc/fstab
sudo -i (It won't help me out)

```


And i have Ubuntu 64X wubi system almost bran new under (D:\ubuntu\disks\)windows ntfs partiton installed.

/etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro,[COLOR="Red"]utf8[/COLOR] 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```

Thanks.

---

### Post by Arand on 2011-05-17
Boot a liveCD and edit fstab from there, removing the utf8 option.

- arand

---

### Post by whynot on 2011-05-17
> **Arand said:**
> Boot a liveCD and edit fstab from there, removing the utf8 option.

- arand

(/host/ubuntu/disks/root.disk)
Thats Cool but how could we get a file linux system.I dont have any linux partitions?

Thanks.

---

### Post by Arand on 2011-05-17
You should be able to follow the steps in:
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

- arand

---

### Post by whynot on 2011-05-17
> **Arand said:**
> You should be able to follow the steps in:
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

- arand

thats amazing!
Now my system works.I have second questions. How could we extract rar files includes other language character encodings? Im able to extract rar files in windows but in ubuntu im getting error.

Thanks.

---

### Post by Arand on 2011-05-17
You may want to look into installing the packages "rar" and/or "unrar" which are not open source software but may enable compatibility with newer version of the rar format (should be able to open it with the default archive manager once installed).

- arand

---

### Post by whynot on 2011-05-17
> **Arand said:**
> You may want to look into installing the packages "rar" and/or "unrar" which are not open source software but may enable compatibility with newer version of the rar format (should be able to open it with the default archive manager once installed).

- arand
Ok i installed other rar packages and now it works.
I have last question :)
Is there any way to resize /host/ubuntu/disks/root.disk this file.When i install wubi in windows it has not much diskspace selected and i accepted.
so i need more diskspace for my ubuntu system.I have to increase this file size in this manner i become more space in ubuntu system or what? 

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             19G   18G  908M  96% /

```

Thanks a lot.

---

### Post by whynot on 2011-05-17
Ok i thing my answers in this link
[https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b]("https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b")
Thanks

---

