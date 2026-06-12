---
title: "chown entire dir structure as root"
date: 2012-10-01
forum: General Help
---

### Post by Albury_Boy on 2012-10-01
I just executed sudo chown -R [user] * in root dir, instead of in home...

Are there any solutions other a bullet to my head??

---

### Post by nothingspecial on 2012-10-01
The solution is to back up your data and reinstall your system.

---

### Post by Albury_Boy on 2012-10-01
Thanks for the reply... but I can't just re-install the system for many reasons. 

Would chown'ing each dir (excluding home) as user 'root' work?

---

### Post by funicorn on 2012-10-01
I'm afraid not.

---

### Post by prshah on 2012-10-01
> **Albury_Boy said:**
> I just executed sudo chown -R [user] * in root 
Are there any solutions 

Before you take an extreme step (reinstalling), try this (untested, at your own risk only, please)

I THINK (absolutely not sure) that re-installing the problematic packages should fix permissions. 

If you have the time, and would like to experiment before re-installing, try installing the ubuntu-desktop meta package
```

sudo apt-get install --reinstall ubuntu-desktop
```

Hopefully, you won't have to download anything at all, unless you have run a recent apt-cache clean (purge old apt .deb files from cache).

AT YOUR OWN RISK only, sorry about that.


Example of a small test, which shows the "--reinstall" seems to work.
```

Wed Sep 26 @16:22:35:~$ ll `which dvdisaster `
-rwxr-xr-x 1 root root 577176 Oct 16  2010 /usr/bin/dvdisaster
Wed Sep 26 @16:22:41:~$ sudo chmod 500 /usr/bin/dvdisaster 
Wed Sep 26 @16:23:11:~$ ll /usr/bin/dvdisaster 
-r-x------ 1 root root 577176 Oct 16  2010 /usr/bin/dvdisaster
Wed Sep 26 @16:23:21:~$ sudo apt-get install --reinstall dvdisaster
..
After this operation, 0 B of additional disk space will be used.
..
Preparing to replace dvdisaster 0.72.1-2 (using .../dvdisaster_0.72.1-2_amd64.deb) ...
...
Setting up dvdisaster (0.72.1-2) ...
Wed Sep 26 @16:23:44:~$ ll /usr/bin/dvdisaster 
-rwxr-xr-x 1 root root 5

```

So, it may be worth a try. However, at your own risk only, please.

You may need to boot into recovery mode to do this.

Good luck.

---

### Post by Albury_Boy on 2012-10-01
Cheers prshah, that looks like a viable solution to a couple of long running problems I've had. I'll report back after trying it... but first, I've been reading this : [http://forums.fedoraforum.org/showthread.php?t=272144](http://forums.fedoraforum.org/showthread.php?t=272144) and I'm going to try manually setting ownership back to 0 for most of the root dir.

It was all for the lack of a ~     Sigh....  

sudo chown -R [user] /* 
instead of....
sudo chown -R [user] ~/*

---

### Post by Albury_Boy on 2013-05-20
> [COLOR=#000000]The solution is to back up your data and reinstall your system.[/COLOR]

He was right :-(
[COLOR=#000000][/COLOR]

---

