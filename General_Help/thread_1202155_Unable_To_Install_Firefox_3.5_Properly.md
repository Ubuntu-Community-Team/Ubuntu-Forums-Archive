---
title: "Unable To Install Firefox 3.5 Properly?"
date: 2009-07-01
forum: General Help
---

### Post by dharvell on 2009-07-01
I am currently running Firefox 3.0.11 and am attempting to upgrade to Firefox 3.5.  I have attempted to do this via the add/remove software manager, as well as by removing all installations of Firefox and using apt to install Firefox 3.5 by typing:

```
sudo apt-get update && apt-get install firefox-3.5
```

Everything appears to download and install properly.  However, when I open Firefox and look at the HELP > ABOUT FIREFOX, it still says 3.0.11.  What gives???

Any information would be most appreciated!

+dharvell

---

### Post by gila_monster on 2009-07-01
I think it may be installing 3.5 in parallel with 3.0. If so, you need to start firefox-3.5 specifically.

Haven't tried this yet, just a thought.

---

### Post by lovinglinux on 2009-07-02
> **gila_monster said:**
> I think it may be installing 3.5 in parallel with 3.0. If so, you need to start firefox-3.5 specifically.

Haven't tried this yet, just a thought.

Yes, it install side-by-side with Firefox 3.0.11

To start Firefox 3.5 from command run the following:

```
firefox-3.5
```

To start via menu, look for **Shiretoko Web Browser** in "Applications >> Internet". Shiretoko is the codename of Firefox 3.5.

---

### Post by Jebtrix on 2009-07-02
There is a sym link /usr/bin/firefox. If you rename the firefox-3.5 sym link to firefox, it will be default. Just rename the original firefox link to .old or something first.

---

### Post by kpkeerthi on 2009-07-02
Is firefox 3.5 in Ubuntu's repo still beta?
[URL="http://packages.ubuntu.com/jaunty/firefox-3.5"]
firefox-3.5 (3.5~**[COLOR="Red"]b4[/COLOR]**~hg20090330r24021+nobinonly-0ubuntu1)[/URL]

---

### Post by lovinglinux on 2009-07-02
> **kpkeerthi said:**
> Is firefox 3.5 in Ubuntu's repo still beta?
[URL="http://packages.ubuntu.com/jaunty/firefox-3.5"]
firefox-3.5 (3.5~**[COLOR="Red"]b4[/COLOR]**~hg20090330r24021+nobinonly-0ubuntu1)[/URL]

Yes, you need to add the *[ubuntu-mozilla-daily](https://help.ubuntu.com/community/FirefoxNewVersion)* PPA repository to your software sources, then update. The PPA will allow you to update to version 3.5 final.

---

### Post by kooldino on 2009-07-05
Why was that such a pain in the ***?  Why couldn't that be updated automatically?  *sigh*

---

### Post by lovinglinux on 2009-07-05
> **kooldino said:**
> Why was that such a pain in the ***?  Why couldn't that be updated automatically?  *sigh*

Because people can't wait until the Ubuntu developers test and make any necessary changes before making it available through the right channels.

BTW, I have updated the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)  with easy instructions on how to install Firefox 3.5 final, not Shiretoko not anything else. Just scroll down to the "**[COLOR="Sienna"]Installing Other Versions[/COLOR]**" section and install it using the first method. It works perfectly.

---

### Post by kpkeerthi on 2009-07-06
> **kooldino said:**
> Why was that such a pain in the ***?  Why couldn't that be updated automatically?  *sigh*

Because Ubuntu is not a rolling distro. [https://wiki.ubuntu.com/UbuntuBackports]("https://wiki.ubuntu.com/UbuntuBackports")

---

### Post by traxxas on 2009-07-06
> **lovinglinux said:**
> Because people can't wait until the Ubuntu developers test and make any necessary changes before making it available through the right channels.

BTW, I have updated the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)  with easy instructions on how to install Firefox 3.5 final, not Shiretoko not anything else. Just scroll down to the "**[COLOR="Sienna"]Installing Other Versions[/COLOR]**" section and install it using the first method. It works perfectly.

That method only works for x86 distros, as mozilla only releases 32-bit versions of its browser.  If you are running amd64 you need to use the mozilla-security-ppa.

---

### Post by lovinglinux on 2009-07-06
> **traxxas said:**
> That method only works for x86 distros, as mozilla only releases 32-bit versions of its browser.  If you are running amd64 you need to use the mozilla-security-ppa.

Thanks, I will update the tutorial.

---

