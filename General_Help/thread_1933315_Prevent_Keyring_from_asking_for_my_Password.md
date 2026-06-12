---
title: "Prevent Keyring from asking for my Password"
date: 2012-02-29
forum: General Help
---

### Post by waltwin on 2012-02-29
[SIZE=2]I am using ubuntu 10.10 on my Laptop. I am able to log in without entering my password but keyring asks for my password. I am using a wireless setup. When I allow my Laptop to sit unattended for any amount of time I guess it goes into hibernation, which is fine but once again I need to enter my password to restore operation.

Know one has access to this machine but myself and I would like to be able to eliminate  the need to enter my password if possible. Any assistance in correcting these issues would be greatly appreciated.  

waltwin[/SIZE]

---

### Post by wyliecoyoteuk on 2012-02-29
Use seahorse to edit the keyring.
Use screen settings to disable screen locking.
Both should be installed by default, open the dash and type seahorse or screen to launch them.

edit sorry, 10.10 may be a little different, I am using 11.10

---

### Post by Tiganjero on 2012-02-29
The easiest way to do this would be to set the keyring password to an empty password. Open *Applications > Accessories > Password and Encryption Keys* (or *System > Preferences* in 11.04), right-click the login keyring and select *Change password*. Enter your old password and leave the new one blank. A security warning will pop up informing you of the danger of leaving the password blank, as anyone who has access to your computer can gain access to your data. But, in your case, this is not a concern. Hope this helped!

Cheers,
George

---

### Post by Krytarik on 2012-03-01
This is the *secure* way ;-) :

[https://help.ubuntu.com/10.10/internet/C/troubleshooting-keyring.html](https://help.ubuntu.com/10.10/internet/C/troubleshooting-keyring.html)

Regards.

---

### Post by waltwin on 2012-03-01
That took care of the problem. Many thanks. 

waltwin

---

