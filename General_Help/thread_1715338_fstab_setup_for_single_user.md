---
title: "fstab setup for single user"
date: 2011-03-26
forum: General Help
---

### Post by mrphud on 2011-03-26
[SOLVED]

Hi everyone. I haven't been on in a while. I am trying to mount an external hard drive at start-up, but I only want to do it for my user name. What to do?

---

### Post by kiyop on 2011-03-26
I cannot understand what you want to do exactly.

If you want to prohibit another user from accessing(x) (or writing(w) or reading(r)) some directory and/or file in ext2/ext3/ext4 partition, you can use "chmod" and "chown" command to change access right and owner and group.
Please type in terminal,
```
man chmod
man chown
```If you want to do with ntfs or FAT32(vfat) partition, please type in terminal,
```
man mount
```and read "ntfs" "fat" and "vfat" sections.
"auto", " uid", "gid", "umask" or so may help.

Of course, if another user can use "sudo", it is useless. Please prohibit another user from using "sudo".
```
man visudo
```

---

### Post by WorMzy on 2011-03-26
You can't mount something for just one user, but you can restrict access to the mounted filesystem, either by setting the ownership of the filesystem's root folder, or (in the case of FAT and NTFS partitions) by forcing the partition to mount with specific ownership/permissions.

Kiyop has suggested some good reading material for you, and I highly recommend that you read through it.

If, however, you find it all going over your head, please provide us with a little more information, and we'll be able to assist you further.

What we need to know is: what filesystem is the partition using. As mentioned above, NTFS and FAT (as well as other filesystems which don't support UNIX file permissions) need to be mounted in a specific way to make them "pretend" to have a certain set of permissions.

---

### Post by mrphud on 2011-03-28
OK. Well if I can't mount for just one user than I do want to restrict access to it. I have tried to determine permissions for the drive, but under properties->permissions it says "the permissions of this folder could not be determined." This must be an artifact of ntfs's failure to recognize UNIX file permissions.

the fstab file has this line pertaining to the mounted drive. 

/dev/sdb1       /media/My_Computer  	ntfs    rw,user,auto,noexec	  0 

I want access to this drive for my (admin) account only. As you can see, it's ntfs.
I don't believe chmod or chown will work in this case. I think I need to know more about your configuration that "pretends" to act like a unix filesystem.

Thanks in advance. 

I have read the man pages for chmod and chown, so there are no knifes in my eye. The ubuntu community documentation and forum posts are better for those commands anyway.

Aren't binary and hex the ones that are used?

---

### Post by vanadium on 2011-03-28
Mount options that would restrict access only to the root account would be:
```

auto,noexec,umask=0177

```

---

### Post by Morbius1 on 2011-03-28
It's quite possible I don't understand the original requirement but I think this is what you are after:

```
 /dev/sdb1  /media/My_Computer  ntfs  defaults,umask=077,uid=1000 0 0
```If you have /media/MyComputer mounted already unmount it then run the following command to test for errors and mount the partition with the new ownership / permissions settings:
```
sudo mount -a
```umask=077 will make the partition accessible only to the owner and uid=1000 will make the owner you. Just to make sure uid=1000 is in fact you run the following command to find out:
```
id
```[COLOR=Blue]EDIT: This is more an FYI:[/COLOR]
Since this is an external drive and it's formatted in NTFS just make sure it's turned on before you boot. Also I would recommend you changing the /dev/sdb1 part to either a LABEL or a UUID since depending on what else you have attached to your machine it may be /dev/sdb1 now but it may not be the next time you boot.

If you run the following command it will show you the LABEL and UUID:
```
 sudo blkid -c /dev/null
```It will come back with something like this:
> /dev/sdb1: LABEL="BACKUP" UUID="66E4DC83E4DC56C1" TYPE="ntfs" And you would change the fstab line to this:
```
UUID=66E4DC83E4DC56C1  /media/My_Computer  ntfs  defaults,umask=077,uid=1000 0 0
```

---

### Post by WorMzy on 2011-03-28
> **mrphud said:**
> I want access to this drive for my (admin) account only. As you can see, it's ntfs.
I don't believe chmod or chown will work in this case. I think I need to know more about your configuration that "pretends" to act like a unix filesystem.

Like others have said, you can use uid, gid and umask to specify the permissions the partition will mount with. There's some documentation [here]("http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt") if you'd like to read through the various options.

---

### Post by mrphud on 2011-04-10
Thanks everyone for all of the help. This is precisely what I wanted.

Cheers

---

