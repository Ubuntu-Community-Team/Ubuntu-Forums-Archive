---
title: "I guess this go's here"
date: 2009-11-01
forum: General Help
---

### Post by jncocontrol on 2009-11-01
I just recently installed UbuntU 9.0.4. And upgraded to .10.

And i have a few question, cause i'm not quite use to Linux at the moment.

1) How to i log-in to Root. Cause i'm trying to install a nvidia display driver and it keep telling me once i put in the stuff in the command line terminal about must be logged in to root or something like that.

2) Is there a type of Defragmentation programe for Linux?


Any help would be greatly appreciated.

---

### Post by 6205 on 2009-11-01
1./ Try start commands in terminal with [COLOR="DarkRed"]sudo[/COLOR] if you wanna do administrative tasks. 
But for installing nvidia driver i strongly suggest you to use Hardware Drivers wizard in System > Administration
(btw. logging in root account in ubuntu is disabled and it's better that way..)

2./ Forget it.. There is no need to defragment linux filesystems :)

---

### Post by P4man on 2009-11-01
> **jncocontrol said:**
> I just recently installed UbuntU 9.0.4. And upgraded to .10.

And i have a few question, cause i'm not quite use to Linux at the moment.

1) How to i log-in to Root. C

You dont. please read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For nvidia drivers just go system > adminstration > hardware drivers.

> 2) Is there a type of Defragmentation programe for Linux?

There is no need. The linux filesystem is pretty much immune to fragmentation. Defraggers exist but have never proven to actually achieve anything.

---

### Post by 3rdalbum on 2009-11-01
Whoa there... don't install the Nvidia driver manually. Go to System > Administration > Hardware Drivers and install it from there. It's easier to install it that way (it downloads and installs it for you) and it keeps in sync with new kernel releases automatically.

---

