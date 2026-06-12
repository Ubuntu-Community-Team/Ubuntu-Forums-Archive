---
title: "Ubuntu Server 9.10 &amp; Xubuntu - how to stop gdm"
date: 2010-03-10
forum: General Help
---

### Post by gottijr on 2010-03-10
How do i stop the desktop application 

  tryed:

  sudo: stop gdm, gdm stop, /etc/init.d/gdm stop

  none is working

  any advice?

  xubuntu is installed on top of server

---

### Post by n0dix on 2010-03-10
Try in a tty console:
```
 sudo service gdm stop 
```

---

### Post by gottijr on 2010-03-10
<code>
stop: Unknown instance: 
</code>

  not working

---

### Post by gottijr on 2010-03-11
this is the error that i'm getting

  on both ubuntu server (virtual and phisic)

  ```

root@UbuntuSV1:/home/gottijr/Desktop# gdm stop

** (gdm-binary:1990): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:1990): WARNING **: Could not acquire name; bailing out
root@UbuntuSV1:/home/gottijr/Desktop# service gdm stop
stop: Unknown instance: 
root@UbuntuSV1:/home/gottijr/Desktop# /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
root@UbuntuSV1:/home/gottijr/Desktop# 


```  thanks

---

### Post by gottijr on 2010-03-11
I will post the resolve for me!

  I disabled the boot in gdm with
 "vi /etc/init/gdm.conf"

> **sisco311 said:**
> 
```

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

#start on (filesystem
#          and started hal
#          and tty-device-added KERNEL=tty7
#          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0**2**16]

```



  than i can start and stop service gdm without a problem

```

  sudo service gdm start
  sudo service gdm stop

```

  the other options didn't allowed me to start stop service because of errors!

---

### Post by n0dix on 2010-03-11
Thanks for post the solution. Maybe an update change the way to stop gdm.

---

### Post by HuXu on 2010-09-26
I was having the same problem with my 10.04 Desktop install and when I tried your fix my inicator-session-applet would crash and I would always have to log in and manually call startx.  So what I did is I checked my installed programs and found that gdm wasn't even installed!! So I installed it and uncommented the gdm lines and walla! Fixed!

---

