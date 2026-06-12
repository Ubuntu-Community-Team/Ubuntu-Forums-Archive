---
title: "chown on SD card: Operation not permitted"
date: 2010-12-16
forum: General Help
---

### Post by munin81 on 2010-12-16
Hello,

I am trying to modify the user and group for a directory on my SD card, but I get an "Operation not permitted" error even when I'm signed in as root.

I have the SD card auto mounted using:
```
root@ubuntu:/media# cat /etc/fstab
/dev/mmcblk0p1 /media/sd vfat auto,user,dmask=0000,fmask=0111 0 0
```

---

### Post by Morbius1 on 2010-12-16
You can't chown or chmod a vfat partition let alone a directory within it. You can only change ownership and permissions in fstab and it will apply to all directories and files.

So to change ownership of the entire mount point you would change your fstab entry to include the following options as an example:

[COLOR=Blue]uid=1000[/COLOR] would change the owner to you
[COLOR=Blue]gid=46[/COLOR] would change group to 46 - plugdev - all local login users are members of plugdev by default.

---

### Post by munin81 on 2010-12-16
I thought it might be related to vfat. *sigh*

I'm trying to move my mySQL database to an SD card, but I'm not having any luck. If I change the gid to 46 will MySQL be able to use it?

---

### Post by tredegar on 2010-12-16
If it's an MS-formatted SD card, linux permissions will not work because the MS filesystem does not understand them.

Copy the file(s) to your linux box and then fix up the permissions once you have the file on a linux filesystem.

Once the file is copied over fix up the ownerships.

If you are unsure what your user and group names are, take a look at the output of

**ls -l ~**

It should be obvious, but the third field is username and the fourth is groupname.

Then you can:

sudo chown username:groupname /path/to/the/file

Then the problem should be solved.

---

### Post by Morbius1 on 2010-12-17
> **munin81 said:**
> I thought it might be related to vfat. *sigh*

I'm trying to move my mySQL database to an SD card, but I'm not having any luck. If I change the gid to 46 will MySQL be able to use it?
I can't answer that question specifically for MySQL but there's something odd about all this. With that line in fstab you have dmask=0000 and fmask=0111. That means all directories will have permissions of 777 and all files will have permissions of 666. Everyone and your Aunt Agnes should be able to do anything they want to do to that partition except execute files.

If MySQL is attempting to create a directory or file with specific permissions or ownership and then checking if that's been set correctly then it's not going to happen. 

Sorry, just don't know enough about MySQL to offer a solution except to create another partition in the SD card formatted in a Linux filesystem so that things like chown and chmod can be used.

---

### Post by munin81 on 2010-12-17
Thank you for your help. I really appreciate it! I think I'll reformat the SD card as ext2 and be done with it. =)

---

