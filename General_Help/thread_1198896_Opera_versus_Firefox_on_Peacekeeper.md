---
title: "Opera versus Firefox on Peacekeeper"
date: 2009-06-28
forum: General Help
---

### Post by DeMus on 2009-06-28
Maybe this is not the right place to post this, but since this forum is a very active one I give it a shot and hope for helpful answers:

I have just done some tests using this site: [_Peacekeeper_]("http://service.futuremark.com/peacekeeper/index.action").
The score for Firefox 3.0.11 was 1432, for Opera 10.0 Beta 2006. Quite a difference you would think. But look at the two screendumps I attached. This doesn't happen just on that site, it happens everywhere: the Opera screen is terrible, a cheap jpg like picture using lots of compression.
Anybody knows how to change this? Opera has some nice things but looking at screens like this prevents me from using it.

---

### Post by 3rdalbum on 2009-06-28
Your problem is Opera Turbo. It's a feature of Opera 10 that uses the Opera servers as a proxy, and the Opera server will compress all images down to very small sizes. It helps when you have low bandwidth.

On the bottom panel, the third image from the left (it looks like a speedometer). Click it to toggle Opera Turbo on and off.

EDIT: The screendumps have come through now. You definitely have Opera Turbo turned on.

---

### Post by DeMus on 2009-06-28
> **3rdalbum said:**
> Your problem is Opera Turbo. It's a feature of Opera 10 that uses the Opera servers as a proxy, and the Opera server will compress all images down to very small sizes. It helps when you have low bandwidth.

On the bottom panel, the third image from the left (it looks like a speedometer). Click it to toggle Opera Turbo on and off.

EDIT: The screendumps have come through now. You definitely have Opera Turbo turned on.

That's it. I didn't know about Opera servers compressing everything to make it faster. Now that I have switched it of, the picture is normal.
Thanks for your answer, it really helped.

---

### Post by 3rdalbum on 2009-06-28
I'm glad I could help :-)

---

### Post by lovinglinux on 2009-06-28
Opera 10 is faster than Firefox 3.0.11 but not too much faster than Firefox 3.5. I think since both are pre-releases, they are better suited for comparison, then comparing with FF 3.0.11

Here are my benchmark points:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118681&stc=1&d=1245764692[/IMG]

---

### Post by DeMus on 2009-06-28
> **lovinglinux said:**
> Opera 10 is faster than Firefox 3.0.11 but not too much faster than Firefox 3.5. I think since both are pre-releases, they are better suited for comparison, then comparing with FF 3.0.11

Here are my benchmark points:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118681&stc=1&d=1245764692[/IMG]

From where did you get Chromium? Is it ready for Linux, or just for the other OS? When ready, is it a ready install already or did you need to compile it yourself?

---

### Post by lovinglinux on 2009-06-28
> **DeMus said:**
> From where did you get Chromium? Is it ready for Linux, or just for the other OS? When ready, is it a ready install already or did you need to compile it yourself?

Is not ready yet. There are several features missing, like plugins, but you can download it. See quote below:

> **netJackDaw said:**
> There are daily builds of chromium available to test for Ubuntu. It is very unstable though, it may work one day, not work at all another day and crash on your favorite site the third. Do not run as a production browser.

It is installable through launchpad.net:
Check out: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
also check: [https://launchpad.net/chromium-project](https://launchpad.net/chromium-project) and [http://code.google.com/chromium/](http://code.google.com/chromium/)

---

