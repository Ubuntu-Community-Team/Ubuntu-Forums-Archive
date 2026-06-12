---
title: "Can't login new 10.10 installation"
date: 2010-12-12
forum: General Help
---

### Post by marcerickson on 2010-12-12
I,ve just installed a fresh copy of Ubunutu 10.10, downloaded a few days ago. The installation seemed to go fine - a user was created during the install. However I can't log in:  the login screen just seems to reset and asks me for my password again. If I try login via a terminal with [Control] + [Alt] + F1 nothing happens.  If I try to shut down and restart nothing happens.  If I try in recovery mode I also can't login - I get login incorrect.

Box is an IBM NetVista 6579-TAU PIII with 512 MB RAM and Intel 82815 graphics.

---

### Post by ryadav on 2010-12-12
boot off the LiveCD into rescude mode, reset password for user

passwd <user>

where <user> is the login id of the user's account

---

### Post by sikander3786 on 2010-12-12
I don't think if that is a problem with password. However you can reset your password as described here.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

For diagnosing the problem, we need to see the output of a few commands. Press and hold down shift key from Bios screen until you see the Grub menu. Select Recovery (2nd on the list) and then Drop to Root Shell. You'll be using the same recovery mode for resetting your password.

If resetting password doesn't help, please post the output of these commands.

```
 ls /home
```

```
df -h
```

```
lspci | grep VGA
```

```
sudo dpkg --configure -a
```

---

### Post by marcerickson on 2010-12-12
Although I couldn't boot into the rescue CD, ryadav's suggestion worked after I booted into recovery mode text only.  Thank you!

---

### Post by marcerickson on 2010-12-12
It worked once only.


If resetting password doesn't help, please post the output of these commands.

```
 ls /home
```marc
```
df -h
```Filesystem                 Size    Used    Avail    Use%    Mounted On
/dev/sda5                  5.2G   3.0G    2.0G     60%     /
none                         243M   204K   243M       1%    /dev
none                         248M     0       248M       0%    /dev/shm
none                         248M    52K    248M       1%    /var/run
none                         248M     0       248M       0%    /var/lock
```
lspci | grep VGA
```00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
```
sudo dpkg --configure -a
```Returned an empty prompt.

---

### Post by sikander3786 on 2010-12-12
Your username is marc? Disk space usage is normal, you have free space on all the drives. Graphics chip is intel so you haven't installed any drivers for that. And you don't have broken package.

You said it worked once. You changed the password and you were able to login? Does it return an error that password is not correct?

---

### Post by marcerickson on 2010-12-12
No error messages.  Same thing happens as my original post.

---

### Post by marcerickson on 2010-12-12
I got tired of waiting and blew it away - I'll try 8.10 on the next install on this box.

Thanks to all.

---

### Post by sikander3786 on 2010-12-12
> **marcerickson said:**
> I got tired of waiting and blew it away - I'll try 8.10 on the next install on this box.

Thanks to all.
Remember, 8.10 is not supported any longer.

Better consider installing the latest LTS release i.e, 10.04.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by marcerickson on 2010-12-12
Thanks for pointing that out.  This box has mimimal RAM and I want to stop screwing around with it as I have been all weekend and get a VPN server up and running on it.

---

