---
title: "Mysql Erro"
date: 2011-07-11
forum: General Help
---

### Post by Illusio on 2011-07-11
I'm using ubuntu as a webhost and am getting this error all of the sudden, /etc/rc2.d/w19mysql: The partition with /var/lib/mysql is too full! 

Last week I deleted a file that was around 1gb and then rebooted the server... everything seemed to be working.  This morning the sites that are hosted on this server, which is a VM, were down again.  Let me know if you all know a fix.

---

### Post by Habitual on 2011-07-11
login to the host and issue a 
```
df -h
```
(it "may" need sudo) so "sudo df -h" if it does)
and report the output here.

---

### Post by Illusio on 2011-07-11
Filesystem     Size    Used      Avail    use%   Mounted
/dev/sda1      19g      19g        0      100        /
udev           501m     140k      500m     1         /dev
none           501m     0         501m     0         /dev/shm
none           501m     276k      500m     1         /dev/run
none           501m     0         501m     0         /dev/lock
none           501m     0         501m     0         /lib/init/rw

---

### Post by Illusio on 2011-07-11
I am also getting this error.

/etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full!

I am guessing they are related.

---

### Post by Illusio on 2011-07-11
Here is a pic, represents better.

---

### Post by Habitual on 2011-07-11
you need to create more room on / (sda) or ask your service provider for more resources.

Alternatively, you can check /var/log for any files that may be approaching 2G
```
sudo find `pwd` /  -size +1G -type f -exec ls -hal {} \;

```

The Apache log quite frequently gets large.
the mysql databases can be huge also...
```
sudo du -sh  /var/lib/mysql/*
```

---

### Post by Habitual on 2011-07-11
> **Illusio said:**
> ...I am guessing they are related.

You guessed correctly. You will have/see numerous errors until the situation is corrected by adding more space to sda1

---

### Post by Illusio on 2011-07-12
Since this is a VM, do we need to use any program to combine the new allocated disk space?  Also, will these files continue to grow after more space is added?

---

### Post by Habitual on 2011-07-12
what kind of VM exactly?

---

### Post by Illusio on 2011-07-12
its set up through our VMWare vSphere Client

---

### Post by Habitual on 2011-07-12
Although, I live and work in "The Cloud" I have no immediate knowledge of that particular product, sorry.

---

### Post by Illusio on 2011-07-13
No problem, thanks a lot for all of your help thus far.

---

