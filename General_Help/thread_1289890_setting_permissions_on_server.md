---
title: "setting permissions on server"
date: 2009-10-12
forum: General Help
---

### Post by weazoe on 2009-10-12
Hope you can help a Noob. I've setup an old computer with Ubuntu 9.04 desktop and am using it as a file and print server. In the home folder I've setup a separate folder for each family member for personal backup and storage.
My question is; How do I set permissions on each folder so only the person to who it is assigned can access it over the network?
Any help will be greatly appreciated

---

### Post by wojox on 2009-10-13
You can learn all about permissions here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

It all depends on if their in the same group or individual...

---

### Post by nothingspecial on 2009-10-13
```
chown -R dad:dad ~/dad/
chown -R mum:mum ~/mum/
```

etc

```
chmod -R 700 ~/dad/
chmod -R 700 ~/mum/
```

etc

See [[COLOR="Magenta"]here[/COLOR]]("http://linuxcommand.gds.tuwien.ac.at/lts0070.php#directory_permissions")

---

### Post by Lars Noodén on 2009-10-13
> **wojox said:**
> You can learn all about permissions here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

It all depends on if their in the same group or individual...

@ wojox : that is a very informative reference document!

umask in fstab has been removed.  Maybe umask in /etc/login.defs, /etc/profile, or ~/.profile would still be relevant for the page.


@ weazoe : how are they accessing the files, sftp, samba or other?

---

### Post by Ivo_Wever on 2009-10-13
> **weazoe said:**
> My question is; How do I set permissions on each folder so only the person to who it is assigned can access it over the network?
That depends on the way in which they will access it. When sharing with others using Windows, Samba is usually the easiest solution. However, Samba has it's own system of user permissions, independent of the file system permissions.

---

