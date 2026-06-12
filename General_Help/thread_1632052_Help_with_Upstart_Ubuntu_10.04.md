---
title: "Help with Upstart Ubuntu 10.04"
date: 2010-11-27
forum: General Help
---

### Post by drewdatrip on 2010-11-27
Hello Im currently running XBMC Live Dharma RC1 which is based on Ubuntu 10.04
In and effort of off loading sickbeard from my existing NAS to my XBMC in an attempt to use hardly ever used CPU on the HTPC and the over used CPU of the nas

Anyway im having issues creating a start / stop script and having it load on boot/reboot
i have figured out that upstart relies on files that are located in /etc/init
I have entitled a file "sickbeard.conf"
these are its contents:
[http://pastie.org/1327694](http://pastie.org/1327694)

However the script is not starting on boot.
After further investigation and typing: "start sickbeard"
```
start sickbeard
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.25" (uid=1000 pid=1583 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
```

Yet typing "sudo start sickbeard" everything starts fine

So i think something is ging wrong in that the user that runs the script "xbmc" has limited permissions and requires "sudo" to load it however i guess i have not evoked sudo in the proper way...just a guess
Any help would be wonderful!

Drew

---

### Post by asmoore82 on 2010-11-27
You can add this to the upstart job file to have it always started on boot:
```
start on runlevel [2345]
stop on runlevel [016]
```

When stopped or started manually, all services should require root privileges.

---

### Post by drewdatrip on 2010-11-27
Awesome!that totally worked!

What exactly did that do? 

And other then that was my upstart script written proper? any other changes or recommendations?

Drew

---

### Post by JoeGoalie on 2011-12-20
> **drewdatrip said:**
> Awesome!that totally worked!
 
What exactly did that do? 
 
And other then that was my upstart script written proper? any other changes or recommendations?
 
Drew
I know this is an old thread, but I'm hoping that what is in this thread will help me out (I'm at work and apparently the pastie.org site is blocked). The old method of using an /etc/init.d script is not working for me. Anyway... You've probably figured this out by now, but what you did is give it a parameter to startup and stop the service. You gave that parameter a run level. Linux/Unix have different init run levels, the standard ones are, 0 = off, 1 = single user mode (for maintainance), 2 = multiuser mode (normal), 6 = restart. I believe Ubuntu handles 2, 3, 4, 5 all the same. I'm not 100% on that though. Other distros or *nix versions have different run levels with different options, like 2 might be multiuser without networking. Here is a [Wikipedia]("http://en.wikipedia.org/wiki/Runlevels") article about it. This might be too late, but hopefully this helps me and I can help you a little bit. :)

---

### Post by JoeGoalie on 2011-12-20
Dang, this didn't work for me.  I copied, added the start/stop runlevels, and changed the username and home.  I can invoke it with sudo start sickbeard, but it doesn't start at system startup for me.

---

