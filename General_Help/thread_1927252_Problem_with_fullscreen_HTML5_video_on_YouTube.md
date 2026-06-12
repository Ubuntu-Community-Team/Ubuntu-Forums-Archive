---
title: "Problem with fullscreen HTML5 video on YouTube"
date: 2012-02-17
forum: General Help
---

### Post by Virus666 on 2012-02-17
Hi all,

As some of you know that **Firefox** begins to support fullscreen **HTML5** video from its 10th version. Until that version Firefox 4 to 9 could not provide fullscreen for **YouTube**'s HTML5 videos.

Here is my problem; **fullscreen** HTML5 videos of YouTube return their normal size when the **media button**s of the laptop or external keyboard (volume up, volume down, mute) are pressed. I had that issue at the times of Jaunty with Flash Player, but that was long time ago and it had been already fixed. I tried the same with **Firefox 10** on **Windows Vista** and there is no such problem; same as **Chromium 16**.0.912.77 on Ubuntu 10.10 **Maverick Meerkat**...

You can enable YouTube's HTML5 player via that URL:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

You may try following HTML5 fullscreen check page:
[http://html5-demos.appspot.com/static/fullscreen.html](http://html5-demos.appspot.com/static/fullscreen.html)

Some more HTML5 videos:
[http://www.mozilla.org/en-US/firefox/video/](http://www.mozilla.org/en-US/firefox/video/)

**My Ubuntu Version**:
Ubuntu 10.10 Maverick Meerkat

**My Firefox user agent string**:
Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:10.0.2) Gecko/20100101 Firefox/10.0.2

Any ideas?...

---

### Post by Virus666 on 2012-02-18
Bump... Any ideas?

---

### Post by Virus666 on 2012-02-19
Bump again... :-(

---

### Post by lovinglinux on 2012-02-19
I can reproduce this on Oneiric.

Since it is a problem not exclusive to Firefox, you should report this to Ubuntu developers on launchpad.

---

### Post by Virus666 on 2012-03-01
> **lovinglinux said:**
> I can reproduce this on Oneiric.

Since it is a problem not exclusive to Firefox, you should report this to Ubuntu developers on launchpad.

Well,

I re-tested the same issue with "Official PPA for Firefox Beta" and "Official PPA for Firefox Aurora builds"; the results are the same...

Firefox **Beta** with Ubuntu 10.10 **Maverick** Meerkat: Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:11.0) Gecko/20100101 Firefox/11.0
Firefox **Aurora** with Ubuntu 10.10 **Maverick** Meerkat: Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:12.0a2) Gecko/20120201 Firefox/12.0a2

You have advised me to report the bug to Ubuntu developers on Launchpad, however, I have no experience of bug reporting.

Can please someone report that bg to Launchpad?

Thanks...

---

### Post by lovinglinux on 2012-03-01
> **Virus666 said:**
> Well,

I re-tested the same issue with "Official PPA for Firefox Beta" and "Official PPA for Firefox Aurora builds"; the results are the same...

Firefox **Beta** with Ubuntu 10.10 **Maverick** Meerkat: Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:11.0) Gecko/20100101 Firefox/11.0
Firefox **Aurora** with Ubuntu 10.10 **Maverick** Meerkat: Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:12.0a2) Gecko/20120201 Firefox/12.0a2

You have advised me to report the bug to Ubuntu developers on Launchpad, however, I have no experience of bug reporting.

Can please someone report that bg to Launchpad?

Thanks...

See this: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by elmicha on 2012-04-01
There's already a bug filed in the Mozilla bugzilla: [https://bugzilla.mozilla.org/show_bug.cgi?id=578265](https://bugzilla.mozilla.org/show_bug.cgi?id=578265)

---

