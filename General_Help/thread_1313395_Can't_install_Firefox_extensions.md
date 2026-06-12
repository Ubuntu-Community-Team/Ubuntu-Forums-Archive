---
title: "Can't install Firefox extensions"
date: 2009-11-03
forum: General Help
---

### Post by Pro-reason on 2009-11-03
A couple of days ago, I did two things: I upgraded to Karmic, and I reorganised my home folder into a new encrypted drive.

One of these things has made it impossible to update or install extensions in Firefox.  I can’t think why.  Everything else is fine.  Any ideas?

---

### Post by ruinen on 2009-11-06
I had same problem with a release candidate, then with the Beta, and now just installed a fresh version of 9.10 and still have the problem.

[http://www.uluga.ubuntuforums.org/showthread.php?t=1287367](http://www.uluga.ubuntuforums.org/showthread.php?t=1287367)

---

### Post by Pro-reason on 2009-11-06
I created a fresh account:

```
sudo adduser test
ssh -Y test@localhost
firefox
```

I still couldn’t add extensions.

I’ve filed a bug:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/477103](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/477103)

---

### Post by winotree on 2009-11-06
[http://ubuntuforums.org/showthread.php?t=1287367](http://ubuntuforums.org/showthread.php?t=1287367) may help you as much as the OP.

---

### Post by Pro-reason on 2009-11-06
As I understand it, the OP created a new profile.  But I’ve already said that I created a whole new system account, and then ran Firefox.  This necessarily creates a new Firefox profile.

Just to be sure, I’ve just created a new Firefox profile on my own account.  The result is as expected.

I’ve found that Firefox will not even let me download an XPI file.

---

### Post by Pro-reason on 2009-11-08
I’ve also tried disabling even those extensions that are installed system-wide via .deb packages.  Still doesn’t work.

My girlfriend’s 32-bit machine can update/install extensions just fine.

---

### Post by fernandoch on 2009-11-08
I am having the same problem...

Firefox version 3.5.4

Tried to create a new profile, but still cannot install extensions :(

---

### Post by Pro-reason on 2009-11-08
Are you using the 64-bit edition of Ubuntu too?

---

### Post by fernandoch on 2009-11-08
Nop, I am using the 32 bits version.

I guess it is a problem with the https. I found a solution for that. I download the addons from the ftp directly to my system from here

[ftp://ftp.mozilla.org/pub/mozilla.org/addons/](ftp://ftp.mozilla.org/pub/mozilla.org/addons/)

then I install the addon by right clicking on the .xpi and installing it with firefox.

---

### Post by Pro-reason on 2009-11-08
Yes, it presumably is a problem with downloading via https.

Using SSH, I made my girlfriend’s machine download an XPI file for me, transferred it to my own machine, and installed it.  No problem.

So, Firefox can install extensions if spoon-fed.  It just can’t download them, and neither can any program on the system.

I tried filing this bug, but they wouldn’t take it seriously.  They just treated it as a tech support issue (telling me to do obvious stuff like reinstall Firefox) instead of understanding it as a bug report.

It would seem that the upgrade to Karmic Koala broke https support somehow.  I’m not sure what the workaround might be.

---

