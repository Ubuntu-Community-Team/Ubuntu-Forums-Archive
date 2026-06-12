---
title: "Allow all users to mount internal media without a password"
date: 2010-10-09
forum: General Help
---

### Post by beastrace91 on 2010-10-09
Howdy All,

Is there a way I can allow all users to mount internal media without entering a password, without using sudo, and without making edits to my /etc/fstab file.

Regards,
~Jeff Hoogland

---

### Post by Handssolow on 2010-10-09
I'm not certain but would the Storage Device Manager package Pysdm achieve this? (an fstab gui program). I've just used it to sort out a problem I had with an external usb stick not mounting.

---

### Post by aysiu on 2010-10-09
Yes, you can edit the /etc/sudoers file to allow all users to use the /sbin/mount command without a password.

---

### Post by deserthowler on 2010-10-10
Have you tried changing permissions?

Earl

---

### Post by robert shearer on 2010-10-10
> mount internal media

If you mean data partitions to be shared such as music, video etc then the workaround that worked for me was to have all data partitions formatted as NTFS.

This allows me to access these partitions from all Ubuntu installs and from Windows installs.

Probably not ideal but it works. You will need ntfs-3g and ntfsprogs installed but that is default with Maverick anyway.

---

### Post by dcstar on 2010-10-10
> **beastrace91 said:**
> Howdy All,

Is there a way I can allow all users to mount internal media without entering a password, without using sudo, and without making edits to my /etc/fstab file.


There are specific mount options to put into /etc/fstab to allow users to mount devices, use them.

---

### Post by sisco311 on 2010-10-10
> **dcstar said:**
> There are specific mount options to put into /etc/fstab to allow users to mount devices, use them.

+1

Also you can configure policykit to allow users to mount partitions via the GUI (i.e. Places menu or nautilus) without a password.

---

### Post by srs5694 on 2010-10-10
To be more specific, the user, users, and owner options enable ordinary users to mount filesystems listed in /etc/fstab. Type "man mount" and search for those words for details. An entry might look something like this:

```

/dev/sdc1  /mnt/shared  ext3  noauto,users  0 0

```

The question, though, is why you would want to *un*mount internal partitions, at least on a regular basis. There are valid reasons for doing this, but offhand I'm not sure why you'd want to do it with user data storage areas. In most cases, it makes more sense to *permanently* mount data storage areas. That way, users don't need to mess with the mount command. To do this, you'd use an /etc/fstab entry like the above, but you'd substitute "defaults" for "noauto,users". (The "noauto" option in the original keeps the partition from being mounted when the system boots.)

---

### Post by beastrace91 on 2010-10-11
> **aysiu said:**
> Yes, you can edit the /etc/sudoers file to allow all users to use the /sbin/mount command without a password.

What would that edit look like? This is what I am looking for.

~Jeff

---

### Post by oldfred on 2010-10-11
These posts show how to share a folder:

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

---

### Post by beastrace91 on 2010-10-12
I discovered what I am looking to do is actually a HAL configuration issue. I am now trying to sort through policykit in a thread [here]("http://ubuntuforums.org/showthread.php?p=9957211#post9957211"). Any suggestions will be lovely :-/

~Jeff

---

### Post by beastrace91 on 2010-10-13
So, since this thread went no where hear (and on another Linux message board as well) I ended up writing a small bash script that auto-mounts all media when a user logs in. Going to leave this thread marked as "un-solved" though in case someone knows how to do this in a more elegant way.

~Jeff

---

