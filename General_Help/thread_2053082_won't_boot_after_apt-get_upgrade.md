---
title: "won't boot after apt-get upgrade"
date: 2012-09-04
forum: General Help
---

### Post by Meijuh on 2012-09-04
After I ran an apt-get upgrade my Ubuntu 12.04 won't boot anymore.

I have put a dmsg on pastebin: [http://pastebin.com/3G32EYrc](http://pastebin.com/3G32EYrc).

Can somebody look at this? Does anyone have an idea how to fix this?

The problem is -- I think -- that lightdm does not start. It hangs on 'checking battery state...'.

---

### Post by wyliecoyoteuk on 2012-09-04
This bit looks a likely candidate:

```
 NVRM: API mismatch: the client has the version 295.49, but
[    7.244817] NVRM: this kernel module has the version 304.43.  Please
[    7.244818] NVRM: make sure that this kernel module and all NVIDIA driver
[    7.244819] NVRM: components have the same version.

```

try Ctrl-C and startx, then look at the X11 logs (in /var/log).
You may need to reinstall the nvidia driver.

Renaming the /etc/X11/xorg.conf to xorg.conf.old and rebooting may let you start in standard driver mode.

---

### Post by Meijuh on 2012-09-04
Hi,

I tried
```
sudo apt-get purge nvidia-current
```

then

```
sudo apt-get install nvidia-current
```

then I did a reboot, but that did not solve the problem.

When I type *startx* then it will again report the api mismatch. Any ideas?

---

### Post by Meijuh on 2012-09-04
I managed to fix it.

I had ppa:ubuntu-x-swat/x-updates as my nvidia driver source.

I removed it using

> sudo add-apt-repository -r ppa:ubuntu-x-swat/x-updates

Then I reinstalled *nvidia-current*.

So, now my driver version again is 295.49 instead of 304.something.

---

### Post by wyliecoyoteuk on 2012-09-04
excellent please mark the thread solved so that itcan help others

---

