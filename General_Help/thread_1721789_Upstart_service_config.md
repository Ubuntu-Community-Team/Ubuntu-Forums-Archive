---
title: "Upstart service config"
date: 2011-04-05
forum: General Help
---

### Post by xshadowmintx on 2011-04-05
I'm trying to find out how to configure upstart.

Specifically, I'm trying to turn off gdm when ubuntu boots a desktop system.

I have already seen and read various posts on this topic, including this post:
[http://superuser.com/questions/105581/how-do-i-prevent-gdm-from-running-at-boot-on-ubuntu/266039](http://superuser.com/questions/105581/how-do-i-prevent-gdm-from-running-at-boot-on-ubuntu/266039)

Which I will summarize as follows:

1) Use init.d style config tools (eg. rcconf) to turn off gdm.
This does not work.

2) Remove /etc/init/gdm
This works.

However, there must be some kind of configuration tool for this, which I simply cannot find. 

How can you configure upstart?

If there is indeed, no configuration tool, then why on earth has ubuntu swapped to using this un-configurable start up system?

This discussion is also being taken to the upstart dev mailing list directly, but I'm hoping someone here and simply point out what I'm doing wrong...

---

### Post by spacesamurai on 2011-04-05
When you mention upstart service, are you referring to programs that are start on login? Something like 

System-->Preferences-->Startup-Applications?

---

### Post by lilorox on 2011-04-20
hi,

I'm digging up this thread because I'm looking for the same thing: finding out what command set allows us to manage the upstart scripts.

Some daemon are running (according to service --status-all) but have no configuration files in /etc/init

How do I (cleanly) turn them off?

I'm really astonished that there is nothing about this in upstart's cookbook or wiki ( [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/) ).

Any help on this would be appreciated :)

Thanks!

---

### Post by fyslab on 2011-07-22
Did you find any proper tool for this? like sysv-rc-conf used to be?

Otherwise yes, upstart thing is quite a mess in Ubuntu, it used to way easier with traditional Sysv startup scripts and command line tools like sysv-rc-conf and chkconfig.

What I am looking for is a simple way to kill some daemon and prevent it from startting at boot. Something like

# /etc/init.d/myservice stop
# sysv-rc-conf  myservice off

---

### Post by jonathanlemoine on 2011-11-06
If you install BUM (Boot Up Manager)you can shut many services off that you don't want to start.

---

