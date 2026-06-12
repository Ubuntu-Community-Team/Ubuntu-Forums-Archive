---
title: "Current state of x64?"
date: 2010-07-02
forum: General Help
---

### Post by Chake99 on 2010-07-02
Haven't upgraded in a while and was considering switching to x64. Last time I checked dealing with 64 bit involved work-arounds to get codecs, flash, or pretty much anything proprietary working.

Is this still the case or has the situation improved? How much difficulty should be expected?

---

### Post by mcooke1 on 2010-07-02
64 bit is worth installing on a 64 bit computer.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by Yellow Pasque on 2010-07-02
Flash sucks even more than usual. Adobe killed their native 64-bit Flash player, so the only official/easy solution is using nspluginwrapper to make the 32-bit version run in 64-bit browsers. Alternatives are running a 32-bit browser in a chroot or using the old, insecure 64-bit Flash. Personally, I choose to use the native 64-bit Flash and only enable it on sites I trust (I use the flashblock plugin). 
I tried gnash, but IMO, it's still not feasible for general browsing and their site hasn't been updated for a bit, which is worrisome.

Other than that, there's still a few 32-bit only codecs (WMA/WMV) and programs that use assembly (like zsnes). It's possible to work around, but annoying. As someone who's used 64-bit since the Edgy days, I'd say that 64-bit support is the best it's ever been, but mainly because of Flash, it's still annoying enough to discourage casual users. My 2 cents..

---

### Post by QIII on 2010-07-02
It has been a while since you tried the 64 bit version, hasn't it?

Flash for Linux still bites.  We can thumb our noses at Adobe all we want, but until they decide to do something about it, we will just have to make do.  Support for the 64 bit Linux version has been pulled and you can't even download it from Adobe right now.

Don't know if you were around long enough ago to remember when things when from 8 bit to 16 bit or from 16 bit to 32 bit, but a lot of people let themselves get left behind as the world moved on...

---

### Post by gwoodruff on 2010-07-02
I currently run it on two desktops and 1 laptop. I have no problems with any perif's or aps.

---

### Post by kir0 on 2010-07-02
I also run x64 and have had no problems with it. All codecs and flash run perfectly.

---

### Post by Seanlol on 2010-07-02
I'm running 64 bit Ubuntu on this machine. I haven't had any problems. Flash is running fine for me.

---

### Post by Chake99 on 2010-07-02
it is decided then. x64 it is.

---

### Post by ubuntu27 on 2010-07-02
When you are ready to install Flash 64-bit for Ubuntu 64-bit, look for "Flash 64-bit scrip" in the forum. That will make it easy to install flash.

---

### Post by NightwishFan on 2010-07-02
[QUOTE='OP']Current state of x64?[/QUOTE]

Sexy.

There are no show stopping differences. Enjoy.

---

### Post by QIII on 2010-07-02
***Do not*** use the 64 bit version of Flash right now.  It has the same security issues that the last 32 bit version had (r53 fixes the flaw in the 32 bit version).  Use the 32 bit version, wrapper and all.

There is, at this point, no support for the native 64 bit version of Flash.  I hope it won't be long before that is rectified.  I'd like to get back to using it.

"Works fine" is deceptive.  Flash for Linux is a terrible resource hog.  It certainly "works fine", if you don't look at htop or your System Monitor and see how your CPU(s) is(are) stumbling over themselves trying to run the thing.

---

### Post by NightwishFan on 2010-07-02
Flash is a stressful process on 32-bit as well. I am hoping gnash/lightspark do well in the near future, as they have hardware acceleration.

---

