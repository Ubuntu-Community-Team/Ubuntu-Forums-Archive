---
title: "All of my Chrome downloads fail with &quot;Download Interrupted&quot;"
date: 2011-11-04
forum: General Help
---

### Post by poebae on 2011-11-04
Ubuntu 11.10
Chrome 16.0.912.21 dev

---

### Post by notgary on 2011-11-11
Hi there, can you please provide some more information on the problem you're having? Specifically can you please answer the following:

[LIST=1]
[*]Does it happen on a fresh boot of the computer?
[*]Does it happen on a fresh install of the browser?
[*]Does deleting the configuration directory in ~/.config/chromium (I think that's where it is) have any effect?
[/LIST]

---

### Post by dnissimi on 2012-01-05
The same is happening to me.  I have tried deleting ~/.config/google-chrome/ and have rebooted the system as well.

Did you ever solve the issue?  If so, I'd appreciate some info.

I'm running Ubuntu 10.04 LTS.  Chrome 16.0.912.63.

Thanks.

---

### Post by 4levels on 2012-01-12
Hi all,

This seems to be related to the apparmor profile settings for chromium.  I'm currently struggling to get apparmor to allow chromium to download files to an external harddrive...
As soon as I find the answer, I'll post back here.

I had the same issue with Firefox and downloading files to an external drive.  However for Firefox I just needed to adjust the file [FONT="Courier New"]/etc/apparmor.d/abstractions/user-download[/FONT] by adding

```
  owner /media/**  rwl,
```

and this works for FF.  No idea why Chromium is not picking this up as well..

---

