---
title: "Deleting with admin privileges"
date: 2011-09-06
forum: General Help
---

### Post by marvolo1300 on 2011-09-06
Hi there,

I am new to Linux and I've encountered a problem. When i extracted the tar.gz file for xampp, i found out that i could not delete the folder. Here is the error:

"The folder "eaccelerator" cannot be handled because you do not have permissions to read it."

I extracted it using "sudo", which i presume is the ubuntu/linux equivalent of the administrator account on Windows.

How do i delete the folder with the administrator account (i think its called "root")?

ty in advance for your help

---

### Post by WorMzy on 2011-09-06
```
sudo rm -r *[COLOR="Red"]foldername[/COLOR]*
```

Be *very* careful with "sudo rm" commands. If you mess one up, and accidentally delete your entire OS, there is no "undo" command.

Also, why are you using XAMPP? Why not just use the native LAMP installation?

```
sudo apt-get install lamp-server^
```

---

### Post by Enigmapond on 2011-09-06
Hi and welcome to the forum. I assume you extracted it to the root file system. Open the  terminal and do:

```
gksu nautilus
```

then enter you password and you will be able to navigate to where you extracted and delet the folder but be careful...you can delete anything this way. Close when done.

Cheers!

---

### Post by marvolo1300 on 2011-09-06
Wow, the Ubuntu community is very helpful. Thanks for your help. WorMzy's idea worked.

And, I'm using XAMPP because it has the Filezilla server for FTP, and the standard Apache, MySQL.

---

### Post by WorMzy on 2011-09-06
Not sure about that. Probably not.

I don't have any experience with ftp servers (I use ssh based sftp), but perhaps someone else can suggest a ftp server to use with the native LAMP server.

---

### Post by sisco311 on 2011-09-06
If you are running some kind of server on a Linux box, then I would strongly suggest you to familiarize yourself with Linux/Unix file permissions and modes. 

If you are familiar with ACLs used on Windows, then learning the Unix file permissions shouldn't be hard at all.

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)


You might also want to check out: [uhelp]community/RootSudo[/uhelp]

---

