---
title: "Allowing Users to Mount/Rip CD's"
date: 2006-03-02
forum: General Help
---

### Post by disabled_20220313 on 2006-03-02
Morning all,

I have set up an Ubuntu computer for my friends family. There are no major problems, even with the speedtouch modem.

One thing though. The computer is set up with multiple user accounts, and my friend is a user not admin (His dad is the only one with admin access). He is trying to rip a CD but when the CD is mounted he is not given permission to even read it.

What folders/files would I need to go and change the permissions on to get this working, not just for him but for all the other users?

I am quite a confident linux user, not afraid of using the command line. Meaning don't be afraid to give me a complicated solution if its a better one.

Thanks,

Ciaran

---

### Post by cronholio on 2006-03-02
In a terminal, do this:

sudo chmod 755 /media/cdrom0

That's the default permissions by the way and it should work like this.

---

### Post by akiro.yamamoto on 2006-03-02
Your fstab entry for the CD/DVD drive should look like this:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
This is what my fstab entry looks like and everyone on my system has access
to the DVD RW drive.
Hope this helps

BTW:
My permissions for the directory where the DVD drive is mounted are as follows:
root:root 755

---

### Post by roshan.s on 2006-03-02
A better (more secure) way to do this is to add the user to the "cdrom" group. This can be done on the commandline by ```
adduser <username> cdrom
``` or with the GUI like this:

1. Go to System > Administration > User and Groups
2. Select the user
3. Click on properties
4. Go to the "User Privileges" tab
5. Check the "Use CD-ROM devices" box

Edit: Just wanted to add that you don't need to mess around with /etc/fstab, since gnome-volume-manager takes care of that

---

### Post by disabled_20220313 on 2006-03-02
Will try adding him to the CD rom users group.

Thanks. Will report when I have tried it.

---

