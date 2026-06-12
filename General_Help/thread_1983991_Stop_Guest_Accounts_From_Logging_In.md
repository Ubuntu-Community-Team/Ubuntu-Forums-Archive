---
title: "Stop Guest Accounts From Logging In"
date: 2012-05-21
forum: General Help
---

### Post by EDLIU on 2012-05-21
Hi,

How do I prevent people from using my Ubuntu?

I have added password to my account. But do not know how to stop "Guests" from logging in.

Thanks.

Ed

---

### Post by zombifier25 on 2012-05-21
Edit the file /etc/lightdm/lightdm.conf as root:
```
gksudo gedit /etc/lightdm/lightdm.conf
```
Then add this line to the bottom of the file:
```

allow-guest=false

```

---

### Post by EDLIU on 2012-05-21
> **zombifier25 said:**
> Edit the file /etc/lightdm/lightdm.conf as root:
```
gksudo gedit /etc/lightdm/lightdm.conf
```Then add this line to the bottom of the file:
```

allow-guest=false

```

Hi,

It asked for the "Root PWD". And I do not know my "Root PWD"...

Thanks.

Ed

---

### Post by Lars Noodén on 2012-05-21
[gksudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo) should ask for your user password, not root.  Can you try using your password and see if it is accepted?

---

### Post by zombifier25 on 2012-05-21
> **EDLIU said:**
> Hi,

It asked for the "Root PWD". And I do not know my "Root PWD"...

Thanks.

Ed

In another thread of yours you said that your user account is no longer an admin. Fix it, come back here and do it.

---

### Post by EDLIU on 2012-05-22
> **zombifier25 said:**
> In another thread of yours you said that your user account is no longer an admin. Fix it, come back here and do it.

How do I fix the problem?

Thanks.

ED

---

### Post by lisati on 2012-05-22
> **zombifier25 said:**
> In another thread of yours you said that your user account is no longer an admin. Fix it, come back here and do it.

For the curious, the other thread can be found here: [http://ubuntuforums.org/showthread.php?t=1983989](http://ubuntuforums.org/showthread.php?t=1983989)

---

