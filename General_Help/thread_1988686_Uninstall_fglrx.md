---
title: "Uninstall fglrx?"
date: 2012-05-28
forum: General Help
---

### Post by Bucky Ball on 2012-05-28
Hi all,

Long story short; I tried to install ATI drivers in 10.04, wound up with purple screen at boot, nothing would fix it (don't suggest nomodset) but I can boot into recovery. 

So I did, hit 'Fix Broken Packages' and it spent about 20 minutes doing so but then threw a heap of errors regarding fglrx. Would delete version 8.723.1 then attempt to install it again, throwing the error:

```
Kernel inclues at /lib/modules/2.6.38-12-generic/build/inclue do not match [bit missing from screen here] ... they are versioned as "" instead of '2.6.38-12-generic'
Might need to adjust your symlinks:
/usr/include
/usr/src/linux
```

Another error I get is that fglrx and fglrx-amdcccle are not configured yet (and the latter relies on the former).

I can't drop to failsafe either. Just leaves me hanging on the 'Running in low graphics mode' window with no control of mouse or keyboard, although on one attempt it listed these three errors which might not be relevant now:

> Open /dev/fb0: no such file or directory
Radeon [dri] RADEONDRIGetversion failed because version mismatch
Radeon: Acceleration initialisation failed.

I decided to kill fglrx altogether which might at least let me boot to failsafe and have a chance at fixing things, so I ran:

```
sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
```

Restart then:

```
sudo rm -r /etc/ati
sudo rm /etc/X11/xorg.conf
sudo rm -rf /usr/share/ati
```

And get this error message when I attempt to 'Fix Broken Packages':

```
Bad return status: module build kernel 2.6.38-12-generic.
fglrx

```

Prior to the purge I was getting:

```
Bad return status: module build kernel 2.6.38-12-generic.
fglrx
fglrx-amdcccle
```

... so something positive's happened.

(some of these errors are not exactly as they were shown because I've had to copy with pen then type back here. ;) ) 

I've been at this off and on for ages and have almost cracked it (with some help from the forum Ubuntuers) so any ideas greatly appreciated ... ;)

* PS: I have 10.10 and 11.04 installed on other partitions and working fine so I can access all files and directories on the 10.04 install without needing to boot into 10.04 recovery if that is any help. At least when I do that I know I am affecting the 10.04 install and not others!

---

### Post by Bucky Ball on 2012-05-28
Well, I managed to kill fglrx with:

```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*

```
There could have been a couple of other things thrown in there along the way but didn't document it closely. This is the one that worked, I know that. You could also try:

```
sudo apt-get remove --purge xorg-driver-fglrx fglrx-kernel-source
```

Now I can boot to the login no probems, actually better than it was before as it goes to 1366x786 from halfway through boot process. But ...

I now have no response from the mouse or keyboard so I am still in the situation of having to hold down the power button to get out. Booting the recovery kernel and selecting 'Failsafe' makes no difference. They are unresponsive. Any ideas here? Everything else looks to be working perfectly so I am only a sniff away.

I might post another thread as the problem has changed (yet again) and post a link back here for anyone that's interested.

---

### Post by Bucky Ball on 2012-05-28
Here is the link to the thread outlining the mouse/keyboard problem:

[http://ubuntuforums.org/showthread.php?p=11975231#post11975231](http://ubuntuforums.org/showthread.php?p=11975231#post11975231)

---

