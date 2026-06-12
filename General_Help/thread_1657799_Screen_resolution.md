---
title: "Screen resolution"
date: 2011-01-01
forum: General Help
---

### Post by storze on 2011-01-01
Hi all!

I'm an absolutely beginner in Linux and my knowledge in computers is only as a typical user. Since today I've changed my operating system from Vista to Linux Ubuntu 10.10.
Now I stand in front of the problem to change the screen resolution. The current resolution is 800x600. How can I change to a higher resolution?

Thanks for any help!

Storze

---

### Post by iosuna86 on 2011-01-01
Hi!

Go to System - Preferences - Monitors.

There, you can change it.

---

### Post by Quirion on 2011-01-01
That's right, though I would also add that there's a possibility that your favorite resolution isn't properly listed there. That usually happens if you are using a monitor or video card that isn't perfectly supported by Ubuntu. If that's the case, you should come back here for more help.

---

### Post by storze on 2011-01-01
> **Quirion said:**
> That's right, though I would also add that there's a possibility that your favorite resolution isn't properly listed there. That usually happens if you are using a monitor or video card that isn't perfectly supported by Ubuntu. If that's the case, you should come back here for more help.

yes, that's it: my favorite resolution is not listet. my graphic driver is "SIS Mirge 3 671 MX"

---

### Post by akand074 on 2011-01-01
Go to System > Administration > Additional Drivers. Make sure your proprietary graphics driver is installed.

---

### Post by storze on 2011-01-01
I've tried this, but there are no additional drivers - my question is now, how to install this driver ...

---

### Post by iosuna86 on 2011-01-01
There is a tutorial on how to install those drivers:

[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html) (it is for Lucid Lynx. I think it can work for Maverick too)

A similar thread you may want to have a look at:

[http://ubuntuforums.org/showthread.php?t=958967&page=61](http://ubuntuforums.org/showthread.php?t=958967&page=61)

I hope you can manage to install them with the tutorial. Let's see how that goes.

---

### Post by akand074 on 2011-01-01
> **storze said:**
> I've tried this, but there are no additional drivers - my question is now, how to install this driver ...

What's your graphics card? If you don't know you should be able to find out by using the command

```
lspci | grep VGA
```

in the terminal.

---

