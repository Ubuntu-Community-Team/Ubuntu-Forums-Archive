---
title: "Wordpress permissions error"
date: 2010-09-11
forum: General Help
---

### Post by cj13579 on 2010-09-11
Hi all,

So I had a wordpress blog up and running on my server and wanted to create a second.

They are both in my /var/www folder under "blog" and "site".

I have temporarily chmoded (recursively) /var/www 777 using:

```
sudo chmod -R 777 /var/www
```

but no matter what I try and do I keep getting permission errors when trying to install plugins etc.

The error I receive is:

Could not create directory. /var/www/site/wp-content/upgrade/wp-userlogin.tmp

I am also now getting errors on my first site which has never had any problems before!!

Any thoughts would be greatly received!

Chris

EDIT:

When upgrading Akismet on my original site (which has always been fine) I get:

Warning: ftp_mkdir() [function.ftp-mkdir]: Permission denied. in /var/www/blog/wp-admin/includes/class-wp-filesystem-ftpext.php on line 240

Could not create directory /var/www/blog/wp-content/upgrade/akismet.2.4.0

---

### Post by lisati on 2010-09-11
I'm having a look for informaiton. While you're waiting for a response, you might find [this page]("http://codex.wordpress.org/Changing_File_Permissions") useful.

---

### Post by cj13579 on 2010-09-11
Yea, I have been having a read of that myself. The thing I don't understand is that I have everything in /var/www set to 777 (I'm aware of the dangers, it' just a tmp thing)! That being the case I don't understand why it wont let me write to the dir.

I have just given the box a reboot as well. Made no difference. Darn!

Thanks for the help!

---

### Post by lisati on 2010-09-11
I also found [http://www.tamba2.org.uk/wordpress/chmod/](http://www.tamba2.org.uk/wordpress/chmod/) and [http://wordpress.org/support/topic/wordpress-file-permissions](http://wordpress.org/support/topic/wordpress-file-permissions)

---

### Post by cj13579 on 2010-09-11
Hi, thanks for those. 

I thought maybe it was the built in FTP that word press uses that might be the issue so I tried using FileZilla. But I still can't write to /var/www at all!

I tried setting permissions to 755 with:
 ```
sudo chmod -R 755 /var/www
``` 
but that didnt seem to work.

I then tried setting it back to 777 this time with a -c switch so:

```
sudo chmod -R -c 777 /var/www
```

It listed everything in those directories as changed but still can't write to that folder at all. Further, if you right click on a folder/file with FileZilla and view the attributes it still says that it is 755!! WTF!?!?!?!

Baffled!

---

### Post by ubulal on 2010-09-11
When the FTP client shows the permissions to be 755 and local "ls -l" shows 777, then most probably the FTP server has it's own setting for file permissions.  Check your FTP servers config.

---

### Post by cj13579 on 2010-09-11
> **ubulal said:**
> When the FTP client shows the permissions to be 755 and local "ls -l" shows 777, then most probably the FTP server has it's own setting for file permissions.  Check your FTP servers config.

You are my hero. That was the problem!

Will mark thread as solved!

---

### Post by khatkarrohit on 2010-10-12
I have a little question.
Why all use 755 permission for /var/www/. Permission 744 are more restrictive and better & 744 give the read access so why 755.

To execute something just give executable file a separate execute permission.

---

