---
title: "Firefox 3.5 Inputs Too Wide/Long"
date: 2009-10-29
forum: General Help
---

### Post by davertron on 2009-10-29
I noticed recently that most text/input fields on websites are way too long. I've attached a screenshot so you can see what I mean.  I'm running Ubuntu 9.04 and Firefox 3.5.4.  Here's a list of what addons I have installed as well, just for good measure:

[LIST]
[*]Adblock Plus 1.1.1
[*]ColorZilla 2.0.2
[*]Download Statusbar 0.9.6.5
[*]Firebug 1.4.3
[*]FireGestures 1.5.4
[*]Greasemonkey 0.8.20090920.2
[*]Ivacy 1.1.7
[*]Jetpack 0.5
[*]Linkification 1.3.6
[*]Live HTTP Headers 0.15
[*]Resizeable Textarea 0.1d
[*]Selenium IDE 1.0.2
[*]Show Go! 1.0.3
[*]Stopwatch 0.8.4
[*]Ubiquity 0.5.4
[/LIST]

Any ideas?

---

### Post by lovinglinux on 2009-10-29
Start Firefox in safe mode and check if the problem persists. If not, then it's an extension messing things up.

```
firefox -safe-mode
```

If I had to guess, I would say is the **Resizeable Textarea** extension that is causing this.

---

### Post by davertron on 2009-10-29
Safe mode makes no difference.  I know it's not the Resizable Textarea because I just installed it this morning and it was definitely doing it before that (although it would seem a likely culprit).

Anyway, I still have the 3.0 branch of Firefox installed on my machine, so I fired that up, and it does NOT have this issue, so I'm guessing it's some sort of weird bug in the 3.5 branch on Ubuntu or something to that affect.

It definitely started recently (within the last month or 2 I would say), if that helps.

---

### Post by lovinglinux on 2009-10-29
> **davertron said:**
> Safe mode makes no difference.  I know it's not the Resizable Textarea because I just installed it this morning and it was definitely doing it before that (although it would seem a likely culprit).

Anyway, I still have the 3.0 branch of Firefox installed on my machine, so I fired that up, and it does NOT have this issue, so I'm guessing it's some sort of weird bug in the 3.5 branch on Ubuntu or something to that affect.

It definitely started recently (within the last month or 2 I would say), if that helps.

Try to create a new profile in Firefox 3.5

```
firefox-3.5 -P
```

This will launch the profile manager, from where you create a new profile and start it.

If that works, then you can migrate the settings from your old profile to the new one with [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109).

---

### Post by davertron on 2009-10-29
> **lovinglinux said:**
> Try to create a new profile in Firefox 3.5

```
firefox-3.5 -P
```

This will launch the profile manager, from where you create a new profile and start it.

If that works, then you can migrate the settings from your old profile to the new one with [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109).

Nope, same deal unfortunately.

Anything else?

---

### Post by lovinglinux on 2009-10-29
> **davertron said:**
> Nope, same deal unfortunately.

Anything else?

Can you post a link with a problematic form, so I can check if I experience the same behavior?

---

### Post by davertron on 2009-10-29
> **lovinglinux said:**
> Can you post a link with a problematic form, so I can check if I experience the same behavior?

[https://manage.slicehost.com/login]("https://manage.slicehost.com/login")

---

### Post by lovinglinux on 2009-10-29
> **davertron said:**
> [https://manage.slicehost.com/login]("https://manage.slicehost.com/login")

No issues here, but I'm using Firefox 3.5.3 on Karmic.

What method did you use to install Firefox 3.5.4?

---

### Post by davertron on 2009-10-29
> **lovinglinux said:**
> No issues here, but I'm using Firefox 3.5.3 on Karmic.

What method did you use to install Firefox 3.5.4?

I just got the update notice from firefox the other day, and then went to Help -> Apply Downloaded Update or something like that.  I think Firefox 3.5 is in the repos for karmic but not for jaunty, so I just downloaded it manually and installed it myself.

I dunno, I'll be updating to karmic in the next few days here, so I'll probably just remove my manual 3.5 install, upgrade, and see if the problem exists with the version out of the repos.

---

### Post by lovinglinux on 2009-10-29
> **davertron said:**
> I dunno, I'll be updating to karmic in the next few days here, so I'll probably just remove my manual 3.5 install, upgrade, and see if the problem exists with the version out of the repos.

I think that is a good option.

---

### Post by davertron on 2009-11-02
Just an FYI, I did the upgrade to Karmic, and I still have the same problem, so I have no idea what's causing this.  My guess is, like I said above, it's a bug in firefox 3.5.4 for Linux.  If anyone else out there is running 3.5.4 on Linux, could you post here to say whether you're having this same issue?

---

### Post by Uncle Spellbinder on 2009-11-02
> **davertron said:**
> ...My guess is, like I said above, it's a bug in firefox 3.5.4 for Linux.  If anyone else out there is running 3.5.4 on Linux, could you post here to say whether you're having this same issue?

No issue here. Firefox 3.5.4, Ubuntu 9.10:

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/FirefoxUbuntuSliceManager.jpg[/IMG]

---

### Post by davertron on 2009-11-02
> **Uncle Spellbinder said:**
> No issue here. Firefox 3.5.4, Ubuntu 9.10:

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Blog/FirefoxUbuntuSliceManager.jpg[/IMG]

Alright, it's gotta be something specific with my machine then.  Since it doesn't seem to be caused by an addon, I'm wondering if maybe it's caused by some of my settings?  I'll poke around and report back if I find anything.

---

### Post by haocheng on 2009-11-02
> **davertron said:**
> Alright, it's gotta be something specific with my machine then.  Since it doesn't seem to be caused by an addon, I'm wondering if maybe it's caused by some of my settings?  I'll poke around and report back if I find anything.

I have the same problem, and changed default GTK font solved it. Check out this thread for reference:
[http://ubuntuforums.org/showthread.php?t=1309467&highlight=firefox+input+long](http://ubuntuforums.org/showthread.php?t=1309467&highlight=firefox+input+long)

Hope this helps!

---

### Post by davertron on 2009-11-03
> **haocheng said:**
> I have the same problem, and changed default GTK font solved it. Check out this thread for reference:
[http://ubuntuforums.org/showthread.php?t=1309467&highlight=firefox+input+long](http://ubuntuforums.org/showthread.php?t=1309467&highlight=firefox+input+long)

Hope this helps!

:p:p:p:p

Yep, this is what did it!  I changed my fonts awhile ago and had forgotten about it.  After removing the bad fonts I installed, everything is good again!

Thanks a bunch :popcorn:

---

