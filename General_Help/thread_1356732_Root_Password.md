---
title: "Root Password"
date: 2009-12-16
forum: General Help
---

### Post by jim1932 on 2009-12-16
I have installed a new printer and went to system>Administration>printing and filled in all the blanks with proper info. When I try to enter my password it is not aurthorizing my root password. I use my root to log on to the system, authorize updates, and have never had problems. Is there a way to get around the password or reset it to work? I have gone to CUPS localhost and:( tried that but I can not get the printer to work.

---

### Post by philinux on 2009-12-16
Open a terminal and post back what this says.

```
cat /etc/group | grep lp
```

You should not need a password to set up a printer. Is this 9.10 karmic?

---

### Post by jim1932 on 2009-12-16
No I have not downloaded the new version. I am using 8.04

---

### Post by philinux on 2009-12-16
> **jim1932 said:**
> No I have not downloaded the new version. I am using 8.04

What does the above command spit out.

---

### Post by jim1932 on 2009-12-16
It leads me through all the setup and when I try to print a test page nothing happens. Then I go through the tests and it gives the window to insert my root and then it is not recognized. I have thought about downloading the new 9,01 but I have heard that there is one version that has bugs and I have enough of those. What do you recommend I do to download the latest version?

---

### Post by philinux on 2009-12-16
Go to system>admin>printing and remove the printer. 


Start again. Is it a usb printer? What make/model?

Open a terminal. Copy and paste this in.

```
cat /etc/group | grep lp
```

---

### Post by aysiu on 2009-12-16
Just to clarify, unless you deliberately set up a root password, Ubuntu should never ask you for a root password.

The first user created during installation is an *admin* user and so can temporarily assume root privileges for particular tasks by using her own *user* (not root) password.

These two links should help you:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

To understand more about sudo and root in general, read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

