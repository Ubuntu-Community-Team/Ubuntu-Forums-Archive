---
title: "root file system check failed"
date: 2011-11-16
forum: General Help
---

### Post by cleosurf88 on 2011-11-16
Hi there. 
 
Been having a few issues. Basically I'm locked of my laptop.

It says: Root filesystem check failed
             A maintenance shell will now be started
             CONTROL-D will terminate this shell and reboot the system
             root@charley-laptop:~# 

Can anyone help

---

### Post by matt_symes on 2011-11-16
Hi

It looks like you need to run fsck on your root partition. You can do this from a live CD (make sure the partition is not mounted) or you can do it from the maintenance shell if you remount the root partition read only.

In either case just make sure the root partition is not mounted read/write.

```
fsck /dev/sdX
```where X is the partition for /. You can do a trail run with the -N switch.

That should fix it (hopefully).

Kind regards

---

### Post by cleosurf88 on 2011-11-16
Tried that, now saying: Error reading block 3670326 (attempt to read block from filesystem resulted in short read) while getting next uniden from scan. Ignore error <y>?

---

### Post by matt_symes on 2011-11-16
Hi

It 'n' to *not* ignore the error. 

Run fsck again but try using a backup superblock instead of the main one. That one may be corrupted.

Run the trail run with the -N switch to see what it says.

Kind regards

---

### Post by cleosurf88 on 2011-11-16
Thanks Matt

That fixed the errors but I am still locked out. It loads to login in screen but nowhere to sign in

---

### Post by matt_symes on 2011-11-16
Hi

What version of Ubuntu are you using ?

> It loads to login in screen but nowhere to sign in

Is it possible to upload a screen shot; maybe from a camera phone. I don't quite understand this and a picture speaks a thousand words.

Kind regards

---

### Post by cleosurf88 on 2011-11-16
Using 10.10 


 [https://dl-web.dropbox.com/get/Public/IMAG0059.jpg?w=79ab15bd](https://dl-web.dropbox.com/get/Public/IMAG0059.jpg?w=79ab15bd)

---

### Post by matt_symes on 2011-11-16
Hi

> **cleosurf88 said:**
> Using 10.10 

So you using GDM. It sounds like it may be corrupted. What happens if you drop to a virtual terminal (ctrl + alt + f1) and restart GDM ?

```
sudo service gdm restart
```

or 

```
sudo /etc/init.d/gdm restart
```


 > [https://dl-web.dropbox.com/get/Public/IMAG0059.jpg?w=79ab15bd](https://dl-web.dropbox.com/get/Public/IMAG0059.jpg?w=79ab15bd)

I can't see the picture. I am getting a permission denied error when i go to your dropbox web page.

You can try to upload the picture to these forums in your next reply. Have a look at the attachments button.

Kind regards

---

### Post by cleosurf88 on 2011-11-16
5 times. Maximum number of tries exceeded 

Won't let me upload photo.

---

### Post by cleosurf88 on 2011-11-16
Missed the bit off that says login incorrect

---

### Post by cleosurf88 on 2011-11-16
Try [https://www.dropbox.com/s/2ta098qvrq0bi4i/IMAG0059.jpg](https://www.dropbox.com/s/2ta098qvrq0bi4i/IMAG0059.jpg)

---

### Post by matt_symes on 2011-11-16
Hi

> 5 times. Maximum number of tries exceeded 


I did not quite understand this statement.

The first thing i would do id to create another user to allow you to login. When you are logged in it will be easier to track down the problem.

Let's create a new user and see if you can use that to log in.

Drop to a virtual terminal by pressing crtl + alt + F1 keys at the same time.

Login by typing your user name and password.

Then type

```
sudo adduser recovery_user
```

```
sudo usermod -aG adm,cdrom,plugdev,admin recovery_user
```

Then reboot your PC and see if you can log in as user [I]recovery_user

[/I]Kind regards

---

