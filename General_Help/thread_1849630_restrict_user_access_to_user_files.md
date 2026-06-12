---
title: "restrict user access to user files"
date: 2011-09-24
forum: General Help
---

### Post by Unguidedone on 2011-09-24
Hey :D

what i would like done but have no idea how is :


in order to access a folder that is protected they must enter sudo password to view it or contents will be encrypted (aes 256) and not be useable.  can this be done?

im not talking about this:
[http://chetangole.com/blog/wp-content/uploads/2008/11/permissions-given.jpg](http://chetangole.com/blog/wp-content/uploads/2008/11/permissions-given.jpg)

just want it to ask for sudo password to use a protected folder

---

### Post by papibe on 2011-09-24
There are several alternatives, depending if you want to encrypt a folder ([encfs]("https://help.ubuntu.com/community/FolderEncryption") and [ecryptfs-utils]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")), a complete [filesystem]("https://help.ubuntu.com/community/EncryptedFilesystemHowto") (even your [Home]("https://help.ubuntu.com/community/EncryptedHome"))

On the other hand, if you need that to work also on Windows, [TrueCrypt]("https://help.ubuntu.com/community/TrueCrypt") would a nice solution.

I hope it helps,
Regards.

---

### Post by bodhi.zazen on 2011-09-24
> **Unguidedone said:**
> Hey :D

what i would like done but have no idea how is :


in order to access a folder that is protected they must enter sudo password to view it or contents will be encrypted (aes 256) and not be useable.  can this be done?

im not talking about this:
[http://chetangole.com/blog/wp-content/uploads/2008/11/permissions-given.jpg](http://chetangole.com/blog/wp-content/uploads/2008/11/permissions-given.jpg)

just want it to ask for sudo password to use a protected folder

You should use permissions and each user need a unique account.

If you do not allow "other" to read the file, they can not.

So your files are already password protected so long as :

1. Each user has a unique account.

2. You understand and set the proper permissions.

If you need a finer grain of control, use ACL (Access control Lists).

If you need more then that use encryption. Cryptkeeper is in the repositories and is a graphical front end for encryption.

---

### Post by patryk77 on 2011-09-24
sudo password is the password of the user that runs sudo, if they are in the admin group.

Making users part of the admin group just so they can access a file is a **bad** idea.

Without encrypting a folder, the easiest way to restrict access to a folder to one specific group is by making other users unable to read it. Typically, that would mean running "chmod 770" or "chmod 750" on the folder, depending on if you want the group members to be able to write to the folder.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

As for encryption, what they said ^^.

---

