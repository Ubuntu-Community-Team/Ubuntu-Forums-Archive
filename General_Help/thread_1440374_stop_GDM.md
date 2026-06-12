---
title: "stop GDM"
date: 2010-03-27
forum: General Help
---

### Post by shahin on 2010-03-27
Greetings-
I am trying to follow:
[url]
http://forums.nvidia.com/index.php?showtopic=99513
[/url]
I get the following error message when I try to stop GDM.  And I tried to issue the command recommended.  But I get another error message.  Is there anything that I am missing about running the command?
```

Script started on Sat 27 Mar 2010 12:34:31 PM EDT
root@thunder:~# /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
gdm stop/waiting
root@thunder:~# exit

Script done on Sat 27 Mar 2010 12:35:04 PM EDT

```

---

### Post by nothingspecial on 2010-03-27
Do what it says

```
sudo service gdm stop
```

---

### Post by dwarfolo on 2010-03-27
As suggested by the error message try using the service command:

service gdm stop

---

### Post by ninecows on 2010-04-10
Got the same problem and obviously I tried "service gdm stop", but stop appears to be an unknown instance

---

### Post by patchwork on 2010-04-10
Unknown instance indicates GDM is not running.

---

### Post by ninecows on 2010-04-10
I suspected that... However the nvidia install complain and days that x-server is still running... So I cant install

---

### Post by Monotoko on 2010-04-10
That message means that GDM was stopped successfully, but it gives you the proper way of doing it for future reference.

You could try this:

```
pgrep Xorg
```

that command will give you a number, then:

```
sudo kill ###
```

Replacing ### with the number you got earlier

---

### Post by motsteve on 2010-04-10
I've hopped through these hoops myself.  I can't seem to get to the tutorial page mentioned in the first segment of this thread, but when I was having trouble, I tried using a virtual terminal in Ubuntu and that didn't work, so I booted into rescue mode and tried and that didn't work, so I ended up booting off of systemrescueCD and mounting the Ubuntu partition, chrooting into it, and then doing all the stops and executing the nvidia.sh.  It was a real pain.  I think now though that there is a .deb package with the new nvidia drivers in it and you just use the package installer to install it.  No fancy Linux weenie stuff required. :)

---

