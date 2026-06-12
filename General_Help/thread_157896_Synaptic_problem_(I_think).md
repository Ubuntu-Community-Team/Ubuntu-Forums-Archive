---
title: "Synaptic problem (I think)"
date: 2006-04-10
forum: General Help
---

### Post by Sonique on 2006-04-10
I can do anything in synaptic or sudo apt-get because I always get the same error message:
```

$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

```

$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  librpm4 rpm
Suggested packages:
  lsb-rpm lintian
The following NEW packages will be installed:
  alien librpm4 rpm
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

I get the same error message in synaptic manager too. Also, updater is not updating my system, and I don't think anything else is. The same error message appears if I have synaptic manager open, and do sudo apt-get install alien.
Thanks

---

### Post by WakkiTabakki on 2006-04-10
You'll get this error if more than one program is trying to update the system through apt (apt-get, synaptic, alien etc...)... 
You could also get this if any of those programs have crashed nasty, in a perfect Murphy-moment (which is so unlikely, that it's almost guaranteed to happen if it can cause a maximum of damage :p )

Have you tried rebooting? 
If that fails, simply remove the lock file (/var/cache/apt/archives/lock), well, provided you _know_ apt isn't running in any shape or form...

Good luck
/N

---

### Post by Sonique on 2006-04-10
I pretty much know that nothing is running apt so do I just do:
```

sudo rm /var/cache/apt/archives/lock

```

Thanks for the speedy response

---

### Post by Sonique on 2006-04-10
Yes it worked! Thanks :D

---

