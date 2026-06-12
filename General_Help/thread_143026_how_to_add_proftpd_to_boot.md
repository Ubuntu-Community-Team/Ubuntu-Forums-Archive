---
title: "how to add proftpd to boot"
date: 2006-03-11
forum: General Help
---

### Post by mitjab on 2006-03-11
i install proftpd and i want that proftpd will start when ubuntu will start, so in boot.
Where to fix that?

---

### Post by hw-tph on 2006-03-11
If you installed the Ubuntu .deb package - **sudo dpkg-reconfigure proftpd** and select inetd. You will also have to configure it - have a look at /etc/proftpd.conf. It should be well documented.


Håkan

---

### Post by harisund on 2006-03-11
Once ubuntu boots, how do you start up proftpd? You can add that to the boot up section, but if you could type out the exact command you use to start it, it would be helpful.

---

### Post by hw-tph on 2006-03-11
**sudo update-rc.d proftpd defaults** will add it to the default runlevel so proftpd starts when the network is up. **sudo /etc/init.d/proftpd start** will start it manually.

And, like I said, check the config. I don't run proftpd anymore (I much prefer vsftpd - simple small and fast) but there may be options you may need to check. Also read the Debian Policy Manual (**sudo apt-get install debian-policy**), chapter 9.3, which deals with system runlevels and init scripts.


Håkan

---

