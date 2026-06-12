---
title: "Run Bind Before Clock Synchronisation ?"
date: 2006-03-03
forum: General Help
---

### Post by MasJ on 2006-03-03
Hi Everyone.
Well, I'm in a fix today and after searching the forums haven't been able to come up with an answer. My problem is that I installed BIND, and it's configured correctly. Only thing is that after I've installed it, when I boot up my system, the "Synchronising clock to NTP.Ubuntulinux.org" always results in a failure.
I figured that this is happening because I've set my DNS server to 127.0.0.1 (since I'm running bind..) but the Synchro step happens before Bind is started. Infact Starting DNS is the last thing that happens in the sequence before the Ubuntu login screen shows up. (I'm using Breezy)

So my question is, can you please tell me how to make bind run before the synchronisation ? I just need to know where to modify this configuration since I haven't been able to find it.
Thank you, in advance.

---

### Post by schilcha on 2006-03-03
Quick and dirty (and probably not a wise idea):
use the ip-address of the ntp-server instead of the name.

Elaborate suggestion: Change the startup-sequence.
FIrst, have a look at the current sequence:
```

ls -l /etc/rc?.d/*ntpdate

```
which gives on my system
> 
lrwxrwxrwx  1 root root 17 2005-11-08 10:15 /etc/rc2.d/S50ntpdate -> ../init.d/ntpdate
lrwxrwxrwx  1 root root 17 2005-11-07 21:50 /etc/rcS.d/S51ntpdate -> ../init.d/ntpdate

The first entry tells you that ntpdate is started when entering runlevel 2 (default at boot) -- every linke (script) in /etc/rc2.d is executed when entering runlevel 2. The order of this execution is determined by the two-digit number after the initial "S". The first scripts to be run will have number 01. The last ones will have 99. 

Now have a look at the priority of bind, using something like
```

ls -l /etc/rc?.d/*bind

```
or
```

ls -l /etc/rc?.d/*named

```
Since I didn't install bind on my machine, I can't check. If the priority of bind is higher or equal to the one of ntpdate, you just need to change the number to a lower one. (By hand or with a program like update-rc.d or some gui-runlevel-editor)

If bind is started before ntpdate already, something else is causing your pain.

Good Luck!

---

### Post by MasJ on 2006-03-03
Thank you so much! I figured it out from your instructions :). I would've gone for the quick and dirty using the IP address thing earlier, had I known where it was running from. :)
But I've managed to change the runlevels. It seems that the ntpdate program was only there in rc.S and there was no bind over there, bind was there in rc0 to rc5 though. So I think the system goes through rc.S and then switches to rc.5 (I'm guessing..), right ?
In any case, I've added a bind9 symlink in rc.S. Maybe I should remove the symlink in rc.5 ? (Since that's the runlevel it switches to, I think..)

Well, next time I reboot I'll find out anyway. Thank you so much for helping!

---

### Post by schilcha on 2006-03-03
[QUOTE=MasJ]It seems that the ntpdate program was only there in rc.S and there was no bind over there, bind was there in rc0 to rc5 though. So I think the system goes through rc.S and then switches to rc.5 (I'm guessing..), right ?[/QUOTE]
You're right -- I just found a nice and brief overview over that topic in the ubuntu-docs. Just have a look at the readme at /usr/share/doc/sysv-rc/README.runlevels.gz.

I think I understand, why things are the way they are on your system -- it is consistent with the philosophy described in that readme: rcS.d-scripts are executed first. They're used to set up the basic system.
> 
[...]
One should not start daemons in this runlevel unless absolutely necessary.
[...]
But this is not the time to start the squid proxy server.
[...]


After reading these lines (after writing my first reply to you), I figured that adding bind to these early-starters is probably not as wise as I thought before. 

[QUOTE=MasJ]I've added a bind9 symlink in rc.S. Maybe I should remove the symlink in rc.5[/QUOTE]

Yes and no. In normal situations, I'd say yes. Otherwise, imagine, your system is up and running. You need to do some adminitrative task in single-user-mode (e.g. resize an LVM-partition). So you switch to runlevel 1. Bind is consequently terminated. But, as soon as you return to multiuser-mode (runlevel 5 or 2 or whatever), bind is not restarted, since it's no longer in the rc2.d directory and rcS.d is only used during bootup.

If you leave it at rc5.d, bind will probably report an error that it cannot be run twice and exit (maybe ubuntu will realize that it's running already and not even try starting it again).

So, after all this idle talk... the baseline is: Go ahead and try it with this new configuration, but beware that you might encounter some problems.

Another suggestion: You can also try to add second (external) nameserver to your /etc/resolv.conf, that will be queried as long as your local bind is not running. That would allow you to leave the boot-process as it is.

Anyways,
  GOOD LUCK!

p.s.: Don't count your chickens before they are hatched -- especially when following my suggestions... ;)

---

### Post by MasJ on 2006-03-03
I would move the clock synchronisation to rc5 but the only problem with that I think would be if the clock gets changed while other programs are running, they might get messed up. (Since a lot of stuff is clock dependent..)
I think the best thing to do at this point would be to add a secondary nameserver to resolv.conf. Or even better yet, just use the IP for the clock server, which should be alright.

---

### Post by schilcha on 2006-03-03
Agree! 

If this machine is going to be up 24/7, you should think about using ntpd. This will keep your clock synchronized all the time. This will also prevent time-leaps during startup.

---

