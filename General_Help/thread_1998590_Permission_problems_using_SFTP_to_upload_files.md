---
title: "Permission problems using SFTP to upload files"
date: 2012-06-07
forum: General Help
---

### Post by Jhorra on 2012-06-07
I'm trying to upload files to a server using my admin login and filezilla.  I get an error saying permission denied because I'm not the owner of the folder.  This is for a website I'm updating for someone, so I'm going to be uploading a lot of files.

I don't want to just make the folder writable as they've had security issues in the past.  

I was told I could use "sudo chmod g+r dir" to make it temporarily writable, then "sudo chmod g-w dir" to lock it back down.  I've tried doing this but still get the permission denied error.

Does anyone have a suggestion?

---

### Post by Sarteck on 2012-06-07
Find out what user and group owns the directory and what the permissions are.  (A simple **ls -l** would do.)

If your account owns it and it has user write access, you probably wouldn't be posting. X3

If a group you are NOT part of owns it and it has group write access, then add yourself to that group.  (For example, on one site I have, I added myself and othr Admins to the www-data group so that they could access/modify files for the site.)



Mind you, I JUST had some user/group permission problems myself and had to come here to get it sorted, so take my advice with a grain of salt. :P

---

### Post by Jhorra on 2012-06-07
Right now www-data owns the folder and all files in it.  I don't work with linux often enough to remember how to do a lot of stuff.  Would you be able to give me the commands to create a group, add myself to it, then give and take away write permissions to this folder?

---

### Post by Sarteck on 2012-06-07
Well, instead of putzing around with doing all that, what you could do is just add yourself to the www-data group.

Let's assume that your username is "jhorra" for this:```
sudo usermod -a -G www-data jhorra
```

Since you will need to use the "sudo" command, you will need to be logged in as a user with privileges to do so, and you will need to enter your password.


What this does is adds "jhorra" to the "www-data" group.  This way (hopefully) you won't need to edit the permissions on files *at all*.



EDIT: Oh, one thing I just learned myself, though... You will have to log out and then log back in for the new group to take effect.

---

### Post by Jhorra on 2012-06-07
Awesome, thanks

---

