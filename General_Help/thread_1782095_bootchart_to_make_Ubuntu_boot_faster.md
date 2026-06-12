---
title: "bootchart to make Ubuntu boot faster"
date: 2011-06-14
forum: General Help
---

### Post by whohoo on 2011-06-14
Hi guys,

Can anyone please let me know how to make the system boot faster by removing the idle time between 5s to 10s? bootchart attached.

It is Ubuntu10.04LTS by the way.

one more hint, the screen black out for ~4s after "Begin: Running  /scripts/init-bottom... Done." I don't know what is going on during that  4s, but my best guess is there is a way we can get rid of it.

bootchart can be found here: 
[IMG]http://i.imgur.com/P2zCU.png[/IMG]


Thanks,
GW

---

### Post by CoolJohnB on 2011-06-14
If you go to System Settings>Login Screen and take the tick out of the box marked "wait 10 seconds...." that might help.

Also I find Ubuntu Tweak very helpful for cleaning things up and adjusting startup/shutdown procedures, that to makes a difference to the speed.

Hope that helps.

---

### Post by john77eipe on 2011-06-14
Yes, Ubuntu 10.04 is LTS.

---

### Post by psusi on 2011-06-14
> **john77eipe said:**
> Yes, Ubuntu 10.04 is LTS.

That was not the question.  Best to post with eyes open, rather than shut :D

---

### Post by whohoo on 2011-06-14
> **CoolJohnB said:**
> If you go to System Settings>Login Screen and take the tick out of the box marked "wait 10 seconds...." that might help.

Also I find Ubuntu Tweak very helpful for cleaning things up and adjusting startup/shutdown procedures, that to makes a difference to the speed.

Hope that helps.

Thanks for the reply. I am using the server version and I boot to bash command mode directly, which means I cannot use Ubuntu Tweak (a desktop app).  And I already set grub timeout to 0.

---

### Post by hal8000 on 2011-06-14
You're not showing the whole bootchart, copy and paste or upload to
this site:

[http://imgur.com/](http://imgur.com/)

The first few lines of bootchart contain your grub parameters, which are missing and also some of the other services are missing.

Depending on your hard drive you can tune it with hdparm, you can modify
fstab to skip timestamp attributes depending on the filesystem, you can
also skip services you dont require and sometimes booting with options like
quiet and fastboot in grub may help.

Reply with your bootchart posted on imgmur and also, your hard drive type,
IDE or SATA, filesystem type.

---

### Post by whohoo on 2011-06-14
full bootchart updated in the first post.

Disk - SSD;
ext4 file system.

you can see the CPU and I/O are free between 5-10s and I can see the command line is up at about 13s. The system seems not doing much during the time slot betwen 5-10s. There should be a way to remove the idle time.

> **hal8000 said:**
> You're not showing the whole bootchart, copy and paste or upload to
this site:

[http://imgur.com/](http://imgur.com/)

The first few lines of bootchart contain your grub parameters, which are missing and also some of the other services are missing.

Depending on your hard drive you can tune it with hdparm, you can modify
fstab to skip timestamp attributes depending on the filesystem, you can
also skip services you dont require and sometimes booting with options like
quiet and fastboot in grub may help.

Reply with your bootchart posted on imgmur and also, your hard drive type,
IDE or SATA, filesystem type.

---

### Post by psusi on 2011-06-14
You need to post it on an off site image host.  The forums butcher the image beyond recognition.

---

### Post by whohoo on 2011-06-14
uploaded here:
[<img src="http://i.imgur.com/T9wXm.png" alt="" title="Hosted by imgur.com" />]("http://imgur.com/T9wXm")
[IMG]http://ubuntuforums.org/%3Cimg%20src=%22http://i.imgur.com/T9wXm.png%22%20alt=%22%22%20title=%22Hosted%20by%20imgur.com%22%20/%3E[/IMG]
> **psusi said:**
> You need to post it on an off site image host.  The forums butcher the image beyond recognition.

---

### Post by psusi on 2011-06-14
That's the distorted image.

---

### Post by whohoo on 2011-06-15
> **psusi said:**
> That's the distorted image.
re-uploaded in the first post.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
why is your wait for root like a quarter of mine ([http://i.imgur.com/FaAPl.png](http://i.imgur.com/FaAPl.png))?
i am going to try removing v86d on my system
no help just messed up my boot resolution
what is the 512M in your boot line?

---

### Post by psusi on 2011-06-15
I'm going to go out on a limb here and say that the time between 5 and 10 seconds is the time it takes you to type your password.  The system is already booted up and ready to go at 5 seconds.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
it is not i have the same 6 second void at a few seconds into booting i login at about 18

---

### Post by whohoo on 2011-06-15
The system boots directly to root - single user mode. No passwd typing needed.

> **psusi said:**
> I'm going to go out on a limb here and say that the time between 5 and 10 seconds is the time it takes you to type your password.  The system is already booted up and ready to go at 5 seconds.

---

### Post by psusi on 2011-06-15
> **whohoo said:**
> The system boots directly to root - single user mode. No passwd typing needed.

How is that?  I don't see the "single" option on the kernel command line, and these days, it brings up the recovery menu instead of directly dropping you to a root shell.

---

### Post by whohoo on 2011-06-15
I modified the gurb fle to boot to root, and removed the recovery package.
> **psusi said:**
> How is that?  I don't see the "single" option on the kernel command line, and these days, it brings up the recovery menu instead of directly dropping you to a root shell.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
> **whohoo said:**
> I modified the gurb fle to boot to root, and removed the recovery package.
so basically you are root like on puppy linux the user is root
is typing "sudo su" too much work?

---

### Post by psusi on 2011-06-15
> **whohoo said:**
> I modified the gurb fle to boot to root, and removed the recovery package.

How so?

---

### Post by whohoo on 2011-06-15
> **pqwoerituytrueiwoq said:**
> so basically you are root like on puppy linux the user is root
is typing "sudo su" too much work?
I know it is safer to use "sudo su", but this os is for special use and I have to save every second on boot up. That's why I want to remove the idle time between 5 to 10s.

---

### Post by whohoo on 2011-06-16
one more hint, the screen black out for ~4s after "Begin: Running  /scripts/init-bottom... Done." I don't know what is going on during that  4s, but my best guess is there is a way we can get rid of it.

---

### Post by psusi on 2011-06-16
At that point it is waiting for the hard disk to be detected.  What is the next think that happens?

Going by the boot chart, that line should appear at about second 1.

Can you post your dmesg?  Let's see what the kernel is saying between seconds 5 and 10.

---

### Post by whohoo on 2011-06-16
attached. As some scripts finish running, my understanding is the hard disk had been detected already at that point?

> **psusi said:**
> At that point it is waiting for the hard disk to be detected.  What is the next think that happens?

Going by the boot chart, that line should appear at about second 1.

Can you post your dmesg?  Let's see what the kernel is saying between seconds 5 and 10.

---

### Post by psusi on 2011-06-16
It looks like the system is fully booted up and ready to go but then waits a few seconds to run your custom auto login thing, but without knowing more about that, I can't guess what it is waiting for.

---

### Post by whohoo on 2011-06-16
so which file should I look into in this case? I just set the single user mode (recovery mode) as default. Which file/script the system checks after "Begin: Running  /scripts/init-bottom... Done."? there is a display black out for ~3~4s after init-bottom Done, and after the blackout there is a line shows :fsck from util-linux-ng 2.17.2; init: bootchart main process terminated ..; init: bootchart post-stop process terminated ..; /dev/sda1: clean, ..." then it seems .bashrc was called.

It seems a script/file was called between init-bottom and fsck.

---

