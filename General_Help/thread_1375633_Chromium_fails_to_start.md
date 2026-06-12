---
title: "Chromium fails to start"
date: 2010-01-08
forum: General Help
---

### Post by Heisenborg on 2010-01-08
Hi. After this morning's automatic update Chromium fails to start. I get the following message when starting Chromium from the command line:

```
$ chromium-browser 
Inconsistency detected by ld.so: dl-minimal.c: 138: realloc: Assertion `ptr == alloc_last_block' failed!
```I have Ubuntu 9.10. Rebooting does not help, reinstalling Chromium does not help either. Google finds nothing for the mentioned error. And I have found no related entries on this forum either.

I'd be grateful for any ideas.

Thanks.

---

### Post by polki@mac.com on 2010-01-08
Same problem here, I started a thread too after searching the forums. Man I'm a slow typer :-D

[http://ubuntuforums.org/showthread.php?t=1375641](http://ubuntuforums.org/showthread.php?t=1375641)

---

### Post by armandopimpa on 2010-01-08
Ok, the same 4 me.... geez....

```

$ chromium-browser
Inconsistency detected by ld.so: dl-minimal.c: 138: realloc: Assertion `ptr == alloc_last_block' failed!

```This is my ps result:

```

$ ps aux | grep chromium
armando  13623  0.0  0.6  70084 21976 pts/0    S+   12:48   0:00 /usr/lib/chromium-browser/chromium-browser
armando  13624  0.0  0.5  70668 17232 pts/0    S+   12:48   0:00 /usr/lib/chromium-browser/chromium-browser
root     13625  0.0  0.0      0     0 pts/0    Z+   12:48   0:00 [chromium-browse] <defunct>

```


wich means that something started but, just after opening, it crashes.
Maybe something wrong with the profile informations.... how to manually delete all the infos about the profile?

---

### Post by zaadjis on 2010-01-08
First time the daily builds are broken, I downgraded to the beta builds: [https://launchpad.net/~chromium-daily/+archive/beta](https://launchpad.net/~chromium-daily/+archive/beta) and it works :)

gksudo gedit /etc/apt/sources.list.d/chromium-browser.list

```
# change **ppa** to **beta**
# deb [http://ppa.launchpad.net/chromium-daily/](http://ppa.launchpad.net/chromium-daily/)**ppa**/ubuntu jaunty main
deb [http://ppa.launchpad.net/chromium-daily/](http://ppa.launchpad.net/chromium-daily/)**beta**/ubuntu jaunty main
```

---

### Post by tarbox on 2010-01-08
Glad to see that there was an answer to how to fix this.  Unfortunately,  synaptic itself is now much less useful as a tool... for whatever reason, "mark for reinstallation" is no longer an option as its greyed out.

The chromium thing is OK.. beta PPA and all... that synaptic has somehow gotten itself broken is a serious bummer.

---

### Post by fragos on 2010-01-08
> **tarbox said:**
> Glad to see that there was an answer to how to fix this.  Unfortunately,  synaptic itself is now much less useful as a tool... for whatever reason, "mark for reinstallation" is no longer an option as its greyed out.

The chromium thing is OK.. beta PPA and all... that synaptic has somehow gotten itself broken is a serious bummer.

You may be able to use Package-> Force in Synaptic to get that done. This seems to happen sometimes when you wish to go back a release. I ended up this time installing Chrome unstable which did work. It's unclear what's the real difference between the two but Chromium appears be more leading edge than Chrome beta -- just my guess.

---

### Post by martywd on 2010-01-08
Update: chromium-browser_4.0.294.0~svn20100108r35810-ubuntu1~ucd1~karmic_i386.deb is available now.  This fixed the 'failed to start' issue for me.

---

### Post by armandopimpa on 2010-01-09
Ok they fixed. On the last release everything works.
Just uninstall and re-install the chromium-browser.

---

### Post by Heisenborg on 2010-01-10
Yes, it's fixed now, reinstallation helps. Thanks to whoever it concerns.

---

