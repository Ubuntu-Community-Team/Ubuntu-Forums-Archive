---
title: "default boot option"
date: 2011-06-22
forum: General Help
---

### Post by eduzav on 2011-06-22
Hy, I've already installed ubuntu 10.04 LTS, I added gdm environment and now when I boot the default is the graphical environment, I need change that behavior (the default must be shell) but I don't find /etc/inittab file, how do I configure that?
Thanks,
Eduardo

---

### Post by Beacon11 on 2011-06-23
No problem.

```
sudo update-rc.d -f gdm remove
```

That will prevent gdm from running at any runlevels. If you ever want to put it back to normal, run

```
sudo update-rc.d gdm defaults
```

---

### Post by dandnsmith on 2011-06-23
as regards the /etc/inittab, the man page says:
The  /etc/inittab  file was the configuration file used by the original
       System V init( 8 ) daemon.

       The Upstart init( 8 ) daemon does not use this file,  and  instead  reads
       its  configuration  from  files  in  /etc/init.   See  init(5) for more
       details.

---

### Post by Beacon11 on 2011-06-23
Yeah, I think 9.10 was the first release where Ubuntu moved completely to Upstart.

---

### Post by sisco311 on 2011-06-23
> **eduzav said:**
> Hy, I've already installed ubuntu 10.04 LTS, I added gdm environment and now when I boot the default is the graphical environment, I need change that behavior (the default must be shell) but I don't find /etc/inittab file, how do I configure that?
Thanks,
Eduardo

See: [http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)

---

### Post by sisco311 on 2011-06-23
> **Beacon11 said:**
> Yeah, I think 9.10 was the first release where Ubuntu moved completely to Upstart.

Ubuntu uses Upstart since 6.10. In 9.10 they replaced some of the System V style init scripts with native Upstart jobs. That's why GDM can't be disabled with update-rc.d in 9.10, 10.04 and 10.10. As a workaround one could boot with the **text** kernel parameter in order to prevent GDM from being started (see the link in my earlier post).

In 11.04 and higher one could use a .override file to disable an Upstart job. See: [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

---

### Post by Beacon11 on 2011-06-23
Wait, you're saying my solution won't work? Why does this say "The following information is tested on 11.04 Natty?" [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by sisco311 on 2011-06-27
> **Beacon11 said:**
> Wait, you're saying my solution won't work?


Yes. 

> **Beacon11 said:**
> 
Why does this say "The following information is tested on 11.04 Natty?" [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Because some services still use the traditional System V style init scripts. You can use update-rc.d to disable/enable this services, but you can't use it to manage the services, like gdm, which use a native Upstart Job.

---

