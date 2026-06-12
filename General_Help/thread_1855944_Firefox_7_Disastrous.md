---
title: "Firefox 7 Disastrous?"
date: 2011-10-07
forum: General Help
---

### Post by neu5eeCh on 2011-10-07
Ever since the upgrade to 6, and especially 7, my system has been a high hard-drive using, memory choked mess.

Just wondering if anyone else has had similar issues? Some of the symptoms: Coming out of screen lock or suspend, Firefox can take up to two minutes of intensive Hard Drive seeking to recover. Web Page scrolling is an agonizing herky-jerky, whiplash inducing experience. Videos stutter. Memory usage can spike up to 82% for minutes on end. Switching between Tabs can cause momentary lock-ups. In general, this has been the worst version of Firefox I've ever used?

---

### Post by bollix47 on 2011-10-07
> Web Page scrolling is an agonizing herky-jerky, whiplash inducing experience. Videos stutter

If using Firefox, have you tried turning off the hardware acceleration feature?

Edit>Preferences>Advanced>General

Remove the check mark in the box next to "Use hardware acceleration when available".

Restart Firefox.

---

### Post by Frogs Hair on 2011-10-07
Do as bolix suggested and see if there is any change . I was wondering what graphics card / chip you are using ?  I have been using Nightly builds which is currently FF 10 a1 and have not had any such problem and I use a mainstream graphics card .

---

### Post by huggs on 2011-10-07
I'm using FF7 on a Dell Dimension 4700 (P.O.S. HW specs-wise) Wubi install, and I don't have any of these problems. Did you disable add-on compatibility checks at some point in the past? Maybe its a bad add-on causing your problems, or if you've done a bunch of about:config tweaks, maybe something from a previous version doesn't work well with 6 or 7.

I would try deleting your FF profile (sucks I know) and start fresh, see if the problems still exist, then re-install your add-ons one by one to figure out if any of them are the problem.

---

### Post by neu5eeCh on 2011-10-08
Thanks for all the advice. I'm starting to get error messages, almost always having to do with a script at HuffPost.

In the meantime, I'll try turning off hardware acceleration.

---

### Post by neu5eeCh on 2011-10-09
Well. Turns out I was wrong. It might be Thunderbird that's at the root of all my problems. When I start it up (or come out of standby) I get a series of unresponsive script errors. The script errors always popped up over Firefox, but seem to be caused by Thunderbird. Here's one:

XPCOMUtils.jsm:332

There are others, but at least I may have discovered a culprit, though not the cause. Sometimes I don't get script errors, just lots of hard drive seeking.

---

### Post by bollix47 on 2011-10-09
Hardware acceleration has come to Thunderbird too.

Tools>Options>Advanced>General>Config Editor

gfx.direct2d.disabled
layers.acceleration.disabled

Set both of these to True and restart Thunderbird.

This may have nothing to do with your problem but it has solved some issues with Thunderbird for me.

Also, don't forget to compact your folders at least weekly depending on your mail volume, deletions etc.

---

### Post by neu5eeCh on 2011-10-09
Thanks, just checked Thunderbird but I don't see those options. Turned everything off in FF though.

---

### Post by bollix47 on 2011-10-09
>  ... just checked Thunderbird but I don't see those options ...

Okay I was looking at a later version of Thunderbird.  In version 3.1 which is probably what you're using I don't think hardware acceleration is active so it shouldn't be a problem.

Perhaps one of your extensions is causing a problem?

You could try starting Thunderbird in safe mode and if the problem disappears then it's likely an extension/theme/plugin problem.

You can start Thunderbird normally and disable all your extensions(Tools>Add-ons), restart, enable extensions one at a time with a restart in between and try to determine which one is causing your problem.

gl

---

### Post by neu5eeCh on 2011-10-09
Thanks, I just disabled he browser plug-in. So far, so good. I'll report back if the problems continue.

---

### Post by neu5eeCh on 2011-10-11
The problem continues. Disabling browser add-on in Thunderbird seemed to help, but now I notice that anytime I suspend the computer or walk away from it for a period of time, Firefox starts gasping and choking on Huffpost scripts (sometimes I leave the website up). This last go around, the hard drive whirred for a good 4 minutes, bringing everything to crawl and generally reeking havoc as FF asked me whether I wanted to stop a script on Huffpost. I used noscript to disable everything on the site. We'll see if this helps. The problems, by the way, all strated with FF6. **Edit**: Wondering if HTML5, in some way, is the culprit, but not sure how it would be.

---

### Post by lovinglinux on 2011-10-11
Slow page scrolling and tab switching is most likely to be caused by the graphics driver and web page scripts. I have nVidia card and when using the latest driver I get bad Firefox performance on a particular web site forum. After installing version 173 of the driver, everything is smooth again.

Firefox 7 is a lot faster than Firefox 3.6 in regard to javascript. So it is weird that you are experiencing such problems after upgrading to Firefox 6. Perhaps something else in your system was also upgraded recently and is causing the problem. However, I would start troubleshooting by creating a clean Firefox profile. Use the command below to launch the profile manager:

```
firefox -P
```

Extensions and slow databases can also cause performance issues. I have a script to optimize databases, so let me know if the clean profile works, so we can try to fix your current profile.

Also, try top switch graphics drivers.

Close Thunderbird while troubleshooting Firefox.

---

### Post by neu5eeCh on 2011-10-11
Here is one of the error messages I've gotten:

resource:///components/nsPrompter.js:68

Just by putting this into Google, along with 'firefox' and error, I get the impression that this might be bug related. I suffer from the same symptoms described by others.

Look here:

[http://web.archiveorange.com/archive/v/wmeLDaneEkBNoQHMSyrE](http://web.archiveorange.com/archive/v/wmeLDaneEkBNoQHMSyrE)

[http://lists4.opensuse.org/opensuse-bugs/2011-06/msg01048.html](http://lists4.opensuse.org/opensuse-bugs/2011-06/msg01048.html)

---

