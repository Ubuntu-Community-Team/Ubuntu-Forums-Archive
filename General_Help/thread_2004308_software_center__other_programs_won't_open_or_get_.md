---
title: "software center  other programs won't open or get errors then close"
date: 2012-06-15
forum: General Help
---

### Post by cybertronic toon on 2012-06-15
I am unable to open software center and apt-get update and some applications get
this error:

E: Type 'buntu' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-oneiric.list
E: The list of sources could not be read.

can somone help me fix this?
(this happened after i added Firefox nightly to repository list)

and an error occoured when trying to find updates after i rebooted to try to fix the problem (before reboot there were 151 updates(which i didn't install))

---

### Post by kanikilu on 2012-06-15
It's telling you exactly where the problem is: > E: Type 'buntu' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-oneiric.list

Post the contents of that file, and we should be able to tell you how to fix it.

```
cat /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-oneiric.list
```

---

### Post by kanikilu on 2012-06-15
For what it's worth, assuming you have 11.10, looking at the page for that PPA, the sources file should read:

```
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) oneiric main 
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) oneiric main
```

If it doesn't, edit it to match that:

```
gksu gedit etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-oneiric.list
```

Enter your password when prompted, and then replace the contents of that file with what is above (copy & paste). Save and close the file. Then run: ```
sudo apt-get update; sudo apt-get upgrade
```

// Edit: Gah...the forum is cutting off the URL's above. Copy and paste the full lines from this page:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) (choose 11.10 as your Ubuntu version)

---

