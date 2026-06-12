---
title: "File permissions (new to ubuntu)"
date: 2010-09-23
forum: General Help
---

### Post by ksuchewie on 2010-09-23
Hello,
My company laid off our employee who was in charge of our ubuntu server.  I am trying to edit a PHP file so that his account is no longer mailed when forms are submitted.  Unfortunately no one else is familiar with ubunutu, so we're a little stuck at the moment.

The trouble I am having, is when I try to save the file, I receive the error, "Could not save the file /var/www/file.php"

When I checked the permissions, it says the file is owned by root, not the login I am using, so the next time before I opened the file I went into terminal and did:
sudo -s 

I thought this would make me act as root, but I am still receiving the error.

Please point me in the right direction.

Thank you.

---

### Post by ksuchewie on 2010-09-23
I figured out what I was doing wrong.

sudo -s
then:
nautilus

---

### Post by bryanfblareunion on 2010-09-23
You can also change the permission of the file by: sudo chmod *file_name*

I know 777 is the "ultimate" permission. Probably not a great idea but I use sometimes to edit. Just change it back immediately after. However, sounds like you fixed it yourself.

---

### Post by rgiles43 on 2010-09-23
Hello,

Also if you want to change the ownership of the file you can type something like this:

sudo chown root:root <file name> 

Note: you can use whatever username instead of root

Hope this helps

---

### Post by eriktheblu on 2010-09-23
The file is owned by and authorize for use to root for a reason. Unless you have good cause, I wouldn't be changing the permissions of that file.

In the terminal preface your command with sudo for CLI applications (e.g. sudo nano /var/www/file.php), or gksudo for GUI apps(e.g. gksudo gedit /var/www/file.php).

---

