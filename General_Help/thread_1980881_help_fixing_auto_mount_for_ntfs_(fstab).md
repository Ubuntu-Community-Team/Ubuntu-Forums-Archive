---
title: "help fixing auto mount for ntfs (fstab)"
date: 2012-05-15
forum: General Help
---

### Post by oldmankit on 2012-05-15
I have an ntfs partition that I want to be automatically mounted every time I login, at ~/share.

Here is the relevant line of my /etc/fstab:
UUID=12B01D06285506A5    /home/me/share    ntfs    defaults,uid=1000,noatime    0 0

This doesn't quite work.  When I login, if I type `ls /home/me/share`, the directory appears completely empty.

I have to do:
`sudo umount /home/me/share`
which responds by saying "not mounted".

`sudo mount -a`
Which successfully mounts the partition.  Now I can see the directory contents.  Interestingly, if I skip the umount step, mounting like this has no effect-I still can't see the directory contents.

Thank you for any suggestions to fix this.

---

### Post by rai4shu2 on 2012-05-15
Interesting. How about this?

```
sudo mkdir /windows
```

then put this into /etc/fstab:

```
UUID=12B01D06285506A5 /windows ntfs defaults,umask=007,gid=46 0 0
```

---

### Post by JKyleOKC on 2012-05-16
The mounting via fstab happens before the network is up, which is why you're having a problem. There's an option that can be added to the line in fstab to delay it, but I don't remember exactly what it is. Hopefully this will be enough of a lead to get someone else to provide you more details...

---

### Post by oldmankit on 2012-05-17
> **JKyleOKC said:**
> The mounting via fstab happens before the network is up, which is why you're having a problem. There's an option that can be added to the line in fstab to delay it, but I don't remember exactly what it is. Hopefully this will be enough of a lead to get someone else to provide you more details...

Thanks for that.   This partition is on the same hard drive as Ubuntu.  It's not a network share.  Is this still a possible solution?

---

### Post by oldmankit on 2012-05-17
> **rai4shu2 said:**
> Interesting. How about this?

```
sudo mkdir /windows
```then put this into /etc/fstab:

```
UUID=12B01D06285506A5 /windows ntfs defaults,umask=007,gid=46 0 0
```

Thanks for the input.  

I don't understand why I would want to change the mount point... could you throw some light on that please?

---

### Post by scottbomb on 2012-05-17
In that fstab line, I believe that should be ntfs-3g not just ntfs. This will provide for read/write operations on the NTFS partition. I believe one must have fuse installed for to this work.

---

### Post by JKyleOKC on 2012-05-17
> **oldmankit said:**
> Thanks for that.   This partition is on the same hard drive as Ubuntu.  It's not a network share.  Is this still a possible solution?It might be, since it would delay things for that partition. Another possible solution would be to add the two command lines, minus the sudo prefixes, to your /etc/rc.local file just in front of the existing "exit 0" line. The "sudo" must be removed since rc.local runs as root itself, as the last step of the boot process. You might need to insert a "sleep 5" command between the two to provide a small time delay and allow the error message to go nowhere, too...

---

### Post by forrestcupp on 2012-05-17
Why do you need to mount it to a non-standard folder? It would be much easier just to let it mount to the proper folder, and it wouldn't be any harder to access it from Nautilus.

If you decide you don't mind doing that, then you can remove what you've already done to fstab and install **ntfs-config**, which is a graphical tool to set it up to automatically mount and set write permissions for your NTFS drive.

---

### Post by jerome1232 on 2012-05-17
Do you have an encrypted home? (I'm just wondering if it was failing to mount in your ~/ during the boot up process due to the encryption not being unlocked yet)

---

### Post by rai4shu2 on 2012-05-17
> **oldmankit said:**
> I don't understand why I would want to change the mount point... could you throw some light on that please?

Mounting in the home folder is problematic because it applies that mount *before* you or anyone else login. And it sticks even after you logout. So, there is the small problem of it being a security issue for other users.

---

### Post by oldmankit on 2012-05-18
> **jerome1232 said:**
> Do you have an encrypted home? (I'm just wondering if it was failing to mount in your ~/ during the boot up process due to the encryption not being unlocked yet)

That was probably it!

Thanks for everyone's help on sorting this out.

The only step I had to do to sort this out was to mount it at /windows instead of inside my encrypted home folder.

Thanks again, all.

---

