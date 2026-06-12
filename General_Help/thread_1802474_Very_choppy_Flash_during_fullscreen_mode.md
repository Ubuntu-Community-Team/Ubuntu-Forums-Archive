---
title: "Very choppy Flash during fullscreen mode"
date: 2011-07-12
forum: General Help
---

### Post by azredwing on 2011-07-12
Hi all - 

When I try to play Flash videos in full screen, sometimes - but not all the time, which makes this bug so aggravating! - the video gets very, VERY choppy, and UI controls do not really respond at all. Sound works fine. Disabling Compiz does nothing to alleviate the problem (switching to Ubuntu Classic (No Effects) - I even created a new user just to test this out to make sure it wasn't a local configuration problem).

This problem exists both in the latest beta build of Chrome and the most up-to-date Firefox with latest Flash. No problems when I watch a video in full-screen, it seems to be just Flash.. and videos tend to play just fine when not in full-screen mode.

I'm on a Thinkpad W510 with an nVidia Quadro FX 880M graphics card. 

If anyone could be help this would be much appreciated.

---

### Post by lovinglinux on 2011-07-12
Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix those common issues. 

If you experience black video on full screen after that on YouTube, then run the Wizard again and disable the option to "Override GPU validation".

---

### Post by azredwing on 2011-07-12
> **lovinglinux said:**
> Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix those common issues. 

If you experience black video on full screen after that on YouTube, then run the Wizard again and disable the option to "Override GPU validation".

Wow - night and day difference. I wonder how this made Flash in Chrome so much better, since Chrome uses a built-in Flash?

Anyhow - thanks for the help!!

---

### Post by wildmanne39 on 2011-07-12
Hi, flashaid takes care of the flash problems for chrome and firefox that what is so great about it and it was created by lovinglinux.

---

### Post by lovinglinux on 2011-07-12
> **azredwing said:**
> Wow - night and day difference. I wonder how this made Flash in Chrome so much better, since Chrome uses a built-in Flash?

Anyhow - thanks for the help!!

From the description of your problems, looks like you have a 64bit system. Chrome only ships the 32bit with bundled plugin. Additionally, some of the tweaks applied by Flash-Aid are independent of plugin location.

---

### Post by azredwing on 2011-07-12
> **lovinglinux said:**
> From the description of your problems, looks like you have a 64bit system. Chrome only ships the 32bit with bundled plugin. Additionally, some of the tweaks applied by Flash-Aid are independent of plugin location.

Yeah, that's exactly right. Although I didn't encounter this until I installed Natty; full-screen flash worked just fine when using Maverick.

---

### Post by MrAntonB on 2011-07-21
> **lovinglinux said:**
> Install [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix those common issues.

I did this on 64bit natty, and now I get stuttering video and out of sync sound intermittently on both stable and beta... I'm not sure what to do. Any help will be deeply appreciated.

---

### Post by lovinglinux on 2011-07-21
> **MrAntonB said:**
> I did this on 64bit natty, and now I get stuttering video and out of sync sound intermittently on both stable and beta... I'm not sure what to do. Any help will be deeply appreciated.

Run Flash-Aid Wizard, disable the option to "Override GPU validation" and execute the script.

---

