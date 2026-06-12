---
title: "Apache websites no longer have write access"
date: 2010-01-06
forum: General Help
---

### Post by renaudclarke on 2010-01-06
Hello,

I'm a newbie and have setup a LAMP server on Ubuntu Desktop. It's been working perfectly with a windows file server via a samba share but since I upgraded to 9.10 all my php files which need write access can no longer write to the Windows file system. 

For example my wordpress php files can't update the .HTACCESS files on the windows machine.

I'm totally stuck and have searched high and low but unable to find anything remotely like my problem. Is there anything like IIS-USR in apache2? doh.

If anyone can help, and I can find them, maybe I should call the A-Team?

Renaud

---

### Post by cdenley on 2010-01-06
The user www-data needs write permission. There are 3 possiblities:

[LIST=1]
[*]the way the share is mounted does not permit write access for www-data
[*]the file server does not permit write access for the user you authenticate as
[*]the server's filesystem does not permit write access for the user you authenticate as
[/LIST]

Since this happened when changing ubuntu, I would guess number 1. How are you mounting the share?
```

cat /etc/mtab

```

---

### Post by renaudclarke on 2010-01-06
I followed these instructions: [http://industriousone.com/mounting-windows-shares-linux](http://industriousone.com/mounting-windows-shares-linux)

Which allowed me to set up a samba share using the fstab and Hosts file.  Sorry, I'm not great on Ubuntu if it's not in a help guide, I'm lost.

In my mtab file I must have been here before as I have the following:
//server0/File\040Server /media/server0 cifs rw,mand 0 0
(server 0 is my Windows file server)

In my fstab I have the following:
//server0/File\040Server  /media/server0  cifs  username=******,password=******  0  0

thanks so much for helping!
Renaud

---

### Post by cdenley on 2010-01-06
What are the permissions for the mounted filesystem?
```

ls -ld /media/server0

```

You can make www-data the owner.
```

//server0/File\040Server /media/server0 cifs rw,uid=33,username=******,password=****** 0 0

```

---

### Post by renaudclarke on 2010-01-06
When I type in 'ls -ld /media/server0'

I get back:
drwxr-xr-x 1 root root 0 2009-12-31 09:47 /media/server0

Shall I change my fstab to 
//server0/File\040Server /media/server0 cifs rw,uid=33,username=******,password=****** 0 0

thanks again for all your help!

---

### Post by cdenley on 2010-01-06
> **renaudclarke said:**
> When I type in 'ls -ld /media/server0'

I get back:
drwxr-xr-x 1 root root 0 2009-12-31 09:47 /media/server0

Shall I change my fstab to 
//server0/File\040Server /media/server0 cifs rw,uid=33,username=******,password=****** 0 0

thanks again for all your help!

Yes. Unix permissions are assigned at mount time. By default, only the owner has write access, and the default owner is root. That fstab line should set the owner to www-data.

---

### Post by renaudclarke on 2010-01-07
Hello again,

I've done some extra work last night to see if I can find the cause of the problem. I changed my fstab and did a mount -a, which didn't fix my problem. I then decided to move the php files locally. I put them into the /var/www folder on the local hard drive and I still (to my horror) received the same error.

Something in my update has changed which means my apache2 can no longer have write access to my hard drive?

I feel really guilty asking for more help, but if you can, I'd really appreciate it. None of my development sites work correctly at the moment.

thanks again and again,
Renaud

---

### Post by cdenley on 2010-01-07
Apache runs as www-data. That user needs write permission. In a typical configuration, such as the default, apache shouldn't be able to write anything (except logs).

---

### Post by bubblehead74 on 2010-01-07
As mentioned above Apache runs as www-data and can only write into files owned by www-data. Therefore you must change the files that you want to be writable by Apache like this:

```
sudo chown www-data:www-data /var/www/filename
```

---

### Post by renaudclarke on 2010-01-07
Thanks Bubblehead, but would this command work on a windows file system (as it doesn't seem to work), as previously setup? Out of interested do you know why I would need to do this now? As previously it just worked without using the chown command on writeable files?

I'm trying to learn! :-(

thanks,
Ren

---

### Post by bubblehead74 on 2010-01-07
No, chown will only help with your local files in /var/www. I don't know how to help you with the Windows share. Maybe, if you cannot change the owner of the Windows share, you can change its permissions to 777. That should help.

---

### Post by cdenley on 2010-01-07
> **bubblehead74 said:**
> No, chown will only help with your local files in /var/www. I don't know how to help you with the Windows share. Maybe, if you cannot change the owner of the Windows share, you can change its permissions to 777. That should help.

I already explained how to set the owner of a mounted windows share. Make the change I suggested, unmount it, then remount it.

---

### Post by renaudclarke on 2010-01-08
Yes I have done this, and it didn't work. So I moved the files locally and I've still go the same problem?

---

### Post by cdenley on 2010-01-08
> **renaudclarke said:**
> Yes I have done this, and it didn't work. So I moved the files locally and I've still go the same problem?

As I explained previously, by default, www-data does not have write permissions anywhere. Post the permissions for your mount point again to confirm you have set the owner to www-data.
```

ls -ld /media/server0

```

---

### Post by renaudclarke on 2010-01-15
Hello!

sorry been away on meetings! here's my mount:

drwxr-xr-x 1 root root 0 2010-01-07 15:39 /media/server0

and this is what's in my FSTAB
//server0/File\040Server /media/server0 cifs rw,uid=33,username=******,password=******  0  0

---

### Post by cdenley on 2010-01-15
> **renaudclarke said:**
> Hello!

sorry been away on meetings! here's my mount:

drwxr-xr-x 1 root root 0 2010-01-07 15:39 /media/server0

and this is what's in my FSTAB
//server0/File\040Server /media/server0 cifs rw,uid=33,username=******,password=******  0  0

That mount point is owner by root. Are you sure it was mounted AFTER you made that change in fstab?

---

### Post by renaudclarke on 2010-01-15
Yes I've even rebooted the server to make sure. I guess this is the problem?

---

### Post by cdenley on 2010-01-15
> **renaudclarke said:**
> Yes I've even rebooted the server to make sure. I guess this is the problem?

That is odd, because it seems to work perfectly for me. Interestingly, it seems to map the permissions from the server's filesystem, but giving the uid mount option does override the owner.

---

