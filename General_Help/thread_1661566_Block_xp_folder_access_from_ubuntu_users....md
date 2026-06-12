---
title: "Block xp folder access from ubuntu users..."
date: 2011-01-06
forum: General Help
---

### Post by Postmaster_G on 2011-01-06
So I have searched the net and this forum, and I am not sure how to search for this. I hope this is the proper location for this question... [and link me to the answer if it exists!!!]
 
I have figured out how to keep the XP my documents folder private and blocked from other XP users, but I can still access this folder from all of my Ubuntu user accounts.
 
Is there a way I can block this folders access from within Ubuntu?
 
Please let me know if you need more information... and thank you for your help!!!
 
G
 
](*,)](*,)

---

### Post by ronnielsen1 on 2011-01-06
Someone might come up with a way to do this but I doubt it. Linux doesn't hide things from you and if you want to see hidden files, it will show you hidden files. The best way I can come up with is to move the files you want to hide somewhere where people aren't likely to browse like C:/Windows/System32/etc

or use encryption

---

### Post by Postmaster_G on 2011-01-06
Well that is interesting, because I can block my Ubuntu document folders (etc...) from other Ubuntu users.  Perhaps I can add my ubuntu account as an owner of the xp folder (although you can probably only have one owner)?  There has to be some way... I hope.  Hiding things is not an option... Thank you!

---

### Post by 0949er on 2011-01-06
what about auto-mounting the xp drive in ubuntu and then making only a specific group have access to it?

---

### Post by Postmaster_G on 2011-01-12
Well My NTFS drive in question does auto-mount as far as I can tell (pysdm)...
 
So how do I make a user group or other control this folder.
 
As far as I can tell, the options are grayed out to set the permissions.

---

### Post by Krytarik on 2011-01-13
Set the permissions with the respective mount options in "/etc/fstab", for NTFS the following options are allowed:
> **uid=**_value_, **gid=**_value_ and **umask=**_value_ 

   Set the file permission on the filesystem.  The umask  value  is
      given in octal.  By default, the files are owned by root and not
      readable by somebody else.[FONT=Verdana]
[/FONT]> 
**uid=**_value_ and **gid=**_value_

      Set the owner and group of all files.  (Default: the uid and gid
      of the current process.)

**umask=**_value_

      Set the umask (the bitmask  of  the  permissions  that  are  **not**
      present).  The default is the umask of the current process.  The
      value is given in octal.
[http://manpages.ubuntu.com/manpages/maverick/en/man8/mount.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/mount.8.html)
[http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)

---

### Post by Krytarik on 2011-01-13
multiple posts due to UF error

---

### Post by Krytarik on 2011-01-13
multiple posts due to UF error

---

### Post by Primefalcon on 2011-01-13
only real way is encryption, check into truecrypt

---

