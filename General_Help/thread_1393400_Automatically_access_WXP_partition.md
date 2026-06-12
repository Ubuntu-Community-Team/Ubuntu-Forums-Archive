---
title: "Automatically access WXP partition"
date: 2010-01-29
forum: General Help
---

### Post by rva1945 on 2010-01-29
The first time I access to the WXP partition from Ubuntu an authentication is required. Is it possible to make Ubuntu access the partition automatically when I start my session?

Of course I have administrator profile.

Automatically log in Windows partition at startup or something like that.

Thanks

---

### Post by n0dix on 2010-01-29
You can try change your fstab, for example:
```
/dev/sdaX /media/WXP ntfs-3g defaults,locale=en_US.utf8 0 0
```
or with UUID
see first:
```
sudo blkid
```
the copy the UUID code to your fstab:
```
UUID=here_the_code /media/WXP ntfs-3g defaults,locale=en_US.utf8 0 0
```

See this for more info: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by c0mput3r_n3rD on 2010-01-29
Just go to Places next to Applications and System and it will be listed there.  When you click you will have to mount it and you will need SU privileges.

---

### Post by rva1945 on 2010-01-29
> **c0mput3r_n3rD said:**
> Just go to Places next to Applications and System and it will be listed there.  When you click you will have to mount it and you will need SU privileges.

An authentication windows appears, but I don't have the Remember authorization checkbox.

I don't want to manually mount it the first time I try to access it after starting my session in Ubuntu.

---

### Post by n0dix on 2010-01-29
> **rva1945 said:**
> An authentication windows appears, but I don't have the Remember authorization checkbox.

I don't want to manually mount it the first time I try to access it after starting my session in Ubuntu.

See my post. It's you specified the WXP partition in fstab file, it's automatically mount every time you login.

---

### Post by c0mput3r_n3rD on 2010-01-29
> **n0dix said:**
> See my post. It's you specified the WXP partition in fstab file, it's automatically mount every time you login.


Yes use the fstab approach.  I half read the post and didn't realize it doesn't give an option to auto mount any more for externel devices.... didn't 8.10 have that?

---

### Post by rva1945 on 2010-01-29
> **n0dix said:**
> See my post. It's you specified the WXP partition in fstab file, it's automatically mount every time you login.

My WXP partition is named Disco local (local disk in Spanish)

But when I run this in Terminal:

/dev/sdaX /media/Disco local ntfs-3g defaults,locale=en_US.utf8 0 0

I get
No such file or directory

How do I have to enter the name of the partition, given that it's two words?

---

### Post by spcwingo on 2010-01-29
You can also accomplish this with a nice little GUI app called ntfs-config.  To install just issue this command in a terminal:

```
sudo apt-get install ntfs-config
```

It should now be accessible under applications>system tools.

---

### Post by rva1945 on 2010-01-30
> **spcwingo said:**
> You can also accomplish this with a nice little GUI app called ntfs-config.  To install just issue this command in a terminal:

```
sudo apt-get install ntfs-config
```It should now be accessible under applications>system tools.

I did it but I don't find it. I don't have the System Tools options under Applications. To search for it, which is the name of the new option?

---

### Post by SecretCode on 2010-01-30
> **rva1945 said:**
> My WXP partition is named Disco local (local disk in Spanish)

But when I run this in Terminal:

/dev/sdaX /media/Disco local ntfs-3g defaults,locale=en_US.utf8 0 0

I get
No such file or directory

How do I have to enter the name of the partition, given that it's two words?

The name (label) of the partition is not used for mounting. You would be better off creating a "mount point" that does not have a space in it. Also, the syntax you've shown is only for use in the /etc/fstab file, not at the command line.

And also, you have not yet found the UUID as suggested above or the actual partition number ("sdaX" is unlikely ever to exist).

Run the following command and post the output here, between [ code ] [/ code ] tags:
```
sudo blkid
```

---

### Post by rva1945 on 2010-01-30
> **SecretCode said:**
> The name (label) of the partition is not used for mounting. You would be better off creating a "mount point" that does not have a space in it. Also, the syntax you've shown is only for use in the /etc/fstab file, not at the command line.

And also, you have not yet found the UUID as suggested above or the actual partition number ("sdaX" is unlikely ever to exist).

Run the following command and post the output here, between [ code ] [/ code ] tags:
```
sudo blkid
```

This is the output:

/dev/sda1: UUID="0E10B3CB10B3B853" LABEL="Disco local" TYPE="ntfs" 
/dev/sda5: UUID="fc7d846b-0f15-490f-9329-f4e159b700e5" TYPE="ext4" 
/dev/sda6: UUID="b0abbeff-6317-43a2-b271-e41381882474" TYPE="swap"

---

### Post by SecretCode on 2010-01-30
Firstly, ntfs-config may still be easier. Look under System > Administration > NTFS Configuration Tool.

To do it manually, edit the file */etc/fstab* and add the following line at the end:
```
UUID=0E10B3CB10B3B853	/media/WXP	ntfs-3g	defaults	0	0
```

I assume you already have a directory /media/WXP - if not,
```
sudo mkdir /media/WXP
```

Then 
```
sudo mount -a
```
to get it loaded, or reboot. Now you should have it automatically mounted at each boot.

---

### Post by rva1945 on 2010-01-30
> **SecretCode said:**
> Firstly, ntfs-config may still be easier. Look under System > Administration > NTFS Configuration Tool.

To do it manually, edit the file */etc/fstab* and add the following line at the end:
```
UUID=0E10B3CB10B3B853    /media/WXP    ntfs-3g    defaults    0    0
```I assume you already have a directory /media/WXP - if not,
```
sudo mkdir /media/WXP
```Then 
```
sudo mount -a
```to get it loaded, or reboot. Now you should have it automatically mounted at each boot.

I finally used NTFS conf. tool and managed to get what I was looking for.

THANKS
Robert

---

### Post by spcwingo on 2010-01-30
> **rva1945 said:**
> I did it but I don't find it. I don't have the System Tools options under Applications. To search for it, which is the name of the new option?

You should be able to find it under Applications>System Tools>NTFS Configuration Tool.

---

