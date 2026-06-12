---
title: "basic directory permissions"
date: 2010-09-03
forum: General Help
---

### Post by cpressland on 2010-09-03
hey guys,

thanks for all your help so far, I love this forum.

/ontopic

Okay so I've managed to set SSH/SFTP setup exactly how I need it but I just need to adjust the permissions on two folders and I hope you guys can help me.

So I have two folders
Download
Upload

I want a user to be able to upload to upload, but not delete from it.
I want a user to be able to download from download, but again, not delete from it, and not upload to it.

Thanks Guys

Chris

---

### Post by sikander3786 on 2010-09-03
> **cpressland said:**
> 
I want a user to be able to upload to upload, but not delete from it.

No idea. Not sure even if it is possible or not. Write permissions don't care if you write or delete.

> 
I want a user to be able to download from download, but again, not delete from it, and not upload to it.
Chris

Read only permissions on the "download" folder will allow accomplishing that.

---

### Post by cpressland on 2010-09-03
Well, thats done the download folder, thanks :)

As for the upload folder, I know it's possible, I've seen it done before... just don't know how!!

---

### Post by cpressland on 2010-09-03
maybe set it so that the user can 'write' to the folder but not view it?

---

### Post by sisco311 on 2010-09-03
The user needs write and execute permissions on the directory. If you set the sticky bit, then only the file's owner, the directory's owner or root can delete/rename the files.

Check out: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by cpressland on 2010-09-03
could you provide me with an example of stickybit...? I've never heard of that before.

How would I go about doing that in this case?

---

### Post by sisco311 on 2010-09-03
> **cpressland said:**
> could you provide me with an example of stickybit...? I've never heard of that before.

How would I go about doing that in this case?

```
chmod +t path/to/dir
```

---

### Post by cpressland on 2010-09-03
okay, I've done that but the user can still delete

---

### Post by cpressland on 2010-09-03
okay, so the folder is owned by root, but files uploaded to it are still owned by the user, hence can be deleted.

---

### Post by cpressland on 2010-09-06
Any additional input from anyone?

---

### Post by gadolinio on 2010-09-06
Maybe you can use the stickybit and also SUID or SGID (set user ID set group ID). One of the latter, when applied to a directory instead of a file, makes every file created into the folder belong to the folder's owner/group, instead of the user/group who created it.
Hope you find this useful.

---

### Post by cpressland on 2010-09-06
Could you explain how to implement such a thing?

Thanks

---

