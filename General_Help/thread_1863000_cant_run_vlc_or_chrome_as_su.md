---
title: "cant run vlc or chrome as su?"
date: 2011-10-17
forum: General Help
---

### Post by Helen84 on 2011-10-17
i try to run vlc as root

```
root@helen-ubunntu:~# vlc
VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and
cannot be run by non-trusted users first).
root@helen-ubunntu:~# 
``````
root@helen-ubunntu:~# chromium-browser
Chromium can not be run as root.
Please start Chromium as a normal user. To run as root, you must specify an alternate --user-data-dir for storage of profile information.
root@helen-ubunntu:~# 
```how can i make it run?

---

### Post by haqking on 2011-10-17
> **Helen84 said:**
> i try to run vlc as root

```
root@helen-ubunntu:~# vlc
VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and
cannot be run by non-trusted users first).
root@helen-ubunntu:~# 
``````
root@helen-ubunntu:~# chromium-browser
Chromium can not be run as root.
Please start Chromium as a normal user. To run as root, you must specify an alternate --user-data-dir for storage of profile information.
root@helen-ubunntu:~# 
```how can i make it run?

why are you logged in as root ?

Root is and should be locked by default in Ubuntu.

See [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Helen84 on 2011-10-17
i unlocked it so i can log in as root

---

### Post by haqking on 2011-10-17
> **Helen84 said:**
> i unlocked it so i can log in as root

Why ? it is not recommended and everyone will tell you the same.

Please read the link i posted

---

### Post by Helen84 on 2011-10-17
yeah i read it bla bla bla. im sick of typing my password and sudo so often im not running servers for nasa just hope pc

---

### Post by haqking on 2011-10-17
> **Helen84 said:**
> yeah i read it bla bla bla. im sick of typing my password and sudo so often im not running servers for nasa just hope pc

I am sad to say that the bla bla attitude will not get you much help on the forum.

I am trying to help you but that dismissal of best practices will not help i am afraid.

---

### Post by Elfy on 2011-10-17
Running as root is not supported here - you've been given the reasons why.

If you still feel the need to do do and need help you'll have to find somewhere else to help with that.

Closed

---

