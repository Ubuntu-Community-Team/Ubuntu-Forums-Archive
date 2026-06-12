---
title: "Firefox-3.5.2 (Jaunty Repos) - Blank Preferences Menu"
date: 2009-08-08
forum: General Help
---

### Post by ssri on 2009-08-08
Hey, I just installed Shiretoko, errrr firefox-3.5.2, from jaunty repos just now.  It imported my firefox 3.0.x profile thereafter.  One thing I noticed upon using the new firefox is the inability to access the preferences menu.  All I get is a blank page.  I restarted my laptop only to find out that the problem persists, even after turning compositing off.  Has anyone experienced this problem?  If so, are there solutions?  Thanks..

OS: Jaunty x86_64
DE: KDE 4.3.0

---

### Post by ssri on 2009-08-08
here's a pic of it...

---

### Post by michy99 on 2009-08-08
What is the output of```
ls -la ~/.mozilla
```

---

### Post by ssri on 2009-08-08
firefox and firefox-3.5 are in separate directories, thus using separate (though copied from firefox->firefox-3.5) profiles..

---

### Post by michy99 on 2009-08-08
> **ssri said:**
> firefox and firefox-3.5 are in separate directories, thus using separate (though copied from firefox->firefox-3.5) profiles..

Ok, but what is the output you get from```
ls -la ~/.mozilla
```

---

### Post by ssri on 2009-08-08
here it is..

```
~/.mozilla$ ls -al
total 28
drwx------  6                   4096 2009-08-08 15:50 .
drwxr-x--- 70                   4096 2009-08-08 15:25 ..
-rw-r--r--  1                    335 2008-12-01 23:14 appreg
drwx------  3                   4096 2009-02-16 13:44 extensions
drwx------  3                   4096 2008-12-01 21:40 firefox
drwx------  3                   4096 2008-12-01 21:40 firefox-3.5
drwxr-xr-x  2                   4096 2009-08-07 23:42 plugins
~/.mozilla$ more appreg
ADdv

~/.mozilla$

```

---

### Post by michy99 on 2009-08-08
The whole point was to check to make sure that the ownership of the folders is correct. Since you removed that part of the listing, I'm not sure how else too help you.

---

### Post by ssri on 2009-08-08
owner:group settings are correct, as adding/updating extensions, themes, flash x86_64 plugins went without a hitch.  There are two things peculiar about firefox-3.5.  The blank preference menu was the first.  Second, the firefox-3.5 process takes forever to close.  I always had to send a termination signal to allow the process to exit.  Strange.. Oh well, I'm on 3.0.x for now.  In the meantime, I'll miss the speed from firefox-3.5

---

### Post by michy99 on 2009-08-08
Ok, I know that often people mess up their profile by running sudo firefox. When you do that, root takes over your profile.

---

### Post by lovinglinux on 2009-08-08
See **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002).

---

### Post by ssri on 2009-08-08
> **michy99 said:**
> Ok, I know that often people mess up their profile by running sudo firefox. When you do that, root takes over your profile.

Yeah, I knew that already.  Besides, I cannot understand why someone would want to run firefox as root by default.  Think of the massive security hole left open by running a web browser as root (see most windows users).  Even I run everything in windows under a limited account.  Still, that would not stop any privilege-escalating exploits.

---

### Post by ssri on 2009-08-08
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002).

Thanks for your very helpful and extensive thread!  Sadly the tip didn't work.  I'm thinking about exporting my bookmarks, delete the profile and start over.

---

### Post by lovinglinux on 2009-08-08
> **ssri said:**
> Thanks for your very helpful and extensive thread!  Sadly the tip didn't work.  I'm thinking about exporting my bookmarks, delete the profile and start over.

You are welcome.

Creating a new profile should fix it. If not, then check solution [FOT001].

---

### Post by ssri on 2009-08-29
> **lovinglinux said:**
> You are welcome.

Creating a new profile should fix it. If not, then check solution [FOT001].

Okay, I solved it (Google provided a little help ;)).  Apparently, there was a conflict between firefox-3.5 and qtcurve (mine is v0.6.7).  To fix it, go to ~/.mozilla/firefox-3.5/xxx.default/chrome and edit userChrome.css and comment out the first two lines:

```
/*@import url("file:///usr/share/themes/QtCurve/mozilla/QtCurve-KDEButtonOrder.css"); /* Added by QtCurve -- do not remove */
/*@import url("file:///usr/share/themes/QtCurve/mozilla/QtCurve.css"); /* Added by QtCurve -- do not remove */
```

This seemed to fix it.  You can add this fix to your list if it is not already one there.

[http://bugs.gentoo.org/279266](http://bugs.gentoo.org/279266)
[https://support.mozilla.com/tiki-view_forum_thread.php?locale=fi&comments_parentId=379718&forumId=1](https://support.mozilla.com/tiki-view_forum_thread.php?locale=fi&comments_parentId=379718&forumId=1)

---

