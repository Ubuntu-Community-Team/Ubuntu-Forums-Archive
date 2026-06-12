---
title: "Cannot write to second hard drive, fstab"
date: 2012-02-13
forum: General Help
---

### Post by sb360 on 2012-02-13
I am having a problem writing to a second hard drive that I use as a media dump, I have setup fstab to automount it and I can't figure out why it wont work.

```
/dev/sdb1 /media/multimedia ext4 defaults 0 0
```

From what I have read this should make it completely accessible but it doesn't. Have I done something stupid? 
Any help is appreciated.

---

### Post by HiImTye on 2012-02-13
make sure that you have proper permissions to write to /media/multimedia
```
ls -l /media/
```

---

### Post by sb360 on 2012-02-13
That gives me 
```
drwxr -xr-x 13 root root 4096 2012-01-29 18:07 multimedia
```

I have no idea if that is good or not though, I am not very good at this yet.

---

### Post by HiImTye on 2012-02-13
```
chown -R <yourusername> /media/multimedia
```
should solve your problems

---

### Post by Bobhuber on 2012-02-13
/dev/sdb1 /media/multimedia ext4 user,exec 0 0

You should be using UUID instead of /dev/sdb1 - Run blkid from a terminal to get the UUID of the partition.

/dev/disk/by-uuid/YOUR UUID HERE /media/multimedia    ext4   user,exec     0     0

Then change the ownership as stated above if needed.

---

### Post by HiImTye on 2012-02-13
> **Bobhuber said:**
> /dev/sdb1 /media/multimedia ext4 user,exec 0 0
no it should work correctly once he has proper folder permissions, the extra options are not necessary
here is my fstab for /storage which works fine with the correct folder permissions set
```
UUID=<the UUID> /storage        ext4    defaults        0       2
```and the folder permissions
```
tye@T:~$ ls -l / | grep storage
drwxr-xr-x  23 tye  tye   4096 2012-02-10 06:15 storage
```

---

### Post by sb360 on 2012-02-13
> **HiImTye said:**
> ```
chown -R <yourusername> /media/multimedia
```
should solve your problems

Thanks, that has let me write to it but transmission is still giving me a permission denied error when I specify anything on the partition as a download location.

Any Ideas ?

---

### Post by HiImTye on 2012-02-13
try
```
sudo chmod -R a=rwx /media/multimedia
```

---

### Post by sb360 on 2012-02-13
> **HiImTye said:**
> try
```
sudo chmod -R a=rwx /media/multimedia
```

That hasn't seemed to change it much, I can still access and write to it but still getting the issue with transmission. Could it be down to how I have set transmission up?

---

### Post by HiImTye on 2012-02-13
it could be. double check the directory you are trying to save to. remember that *nix folders/files are case sensitive

---

### Post by Bobhuber on 2012-02-13
> **HiImTye said:**
> no it should work correctly once he has proper folder permissions, the extra options are not necessary
here is my fstab for /storage which works fine with the correct folder permissions set
```
UUID=<the UUID> /storage        ext4    defaults        0       2
```and the folder permissions
```
tye@T:~$ ls -l / | grep storage
drwxr-xr-x  23 tye  tye   4096 2012-02-10 06:15 storage
```

OK - Explanation as to why.
user - Permit ANY USER to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden
nouser - Only permit root to mount the filesystem. This is also a DEFAULT setting. 
defaults - Use default settings. Equivalent to rw, suid, dev, exec, auto, NOUSER , async.

Hence he is mounting the partition as root with the command he was using.
user,exec will also allow him to access file system binaries from the external partition if needed (Transmission).

---

### Post by sb360 on 2012-02-13
> **HiImTye said:**
> it could be. double check the directory you are trying to save to. remember that *nix folders/files are case sensitive

Ahhh, the file paths and folders are fine, but if I change to a different directory it works fine, still not sure if I can get a new torrent to start going to the right directory though.

---

### Post by sb360 on 2012-02-13
All works for me now Thankyou everyone, what are the benefits of switching to UUID over sdb1?

---

### Post by HiImTye on 2012-02-13
> **Bobhuber said:**
> OK - Explanation as to why.
user - Permit ANY USER to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden
nouser - Only permit root to mount the filesystem. This is also a DEFAULT setting. 
defaults - Use default settings. Equivalent to rw, suid, dev, exec, auto, NOUSER , async.

Hence he is mounting the partition as root with the command he was using.
user,exec will also allow him to access file system binaries from the external partition if needed (Transmission).
he doesn't need to dynamically mount/unmount the partition so user is not needed. he needs to write to it (and rw, exec, etc are default settings) so all he needs to do is fix the file/folder permissions

---

### Post by HiImTye on 2012-02-13
> **sb360 said:**
> All works for me now Thankyou everyone, what are the benefits of switching to UUID over sdb1?
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

basically, if you are using an interface that has multiple drives drives on it (for instance: IDE or PATA with master/slave) then it might reassign the drive number (/dev/sdb1), although unlikely. it's generally safer to use UUID as it is unique to the drive and not the interface. it is more necessary for removable media as they are dynamically assigned (i.e. USB hard drives)

---

