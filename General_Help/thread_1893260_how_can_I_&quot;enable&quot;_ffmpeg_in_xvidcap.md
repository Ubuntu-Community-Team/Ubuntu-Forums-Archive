---
title: "how can I &quot;enable&quot; ffmpeg in xvidcap?"
date: 2011-12-09
forum: General Help
---

### Post by UmlautBanana on 2011-12-09
I installed xvidcap from the latest source on their website, but when I run it I can only record in single frame mode in .xwd format. I have ffmpeg installed but how do I tell xvidcap it's there?  EDIT: Scroll down to the fifth post.

---

### Post by oldtimer7777 on 2011-12-09
> **UmlautBanana said:**
> I installed xvidcap from the latest source on their website, but when I run it I can only record in single frame mode in .xwd format. I have ffmpeg installed but how do I tell xvidcap it's there?

Are you sure you have all your codecs installed?  Go down the checklist to be sure:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by UmlautBanana on 2011-12-09
I've actually read that before, and I just ctrl+f'd "ffmpeg" just to be sure. I have everything there.

---

### Post by oldtimer7777 on 2011-12-09
> **UmlautBanana said:**
> I've actually read that before, and I just ctrl+f'd "ffmpeg" just to be sure. I have everything there.

Multiframe capture in avi divx works fine when I install this from the repositories. You can convert the avi in handbrake or winff to whatever you need it to be.

---

### Post by UmlautBanana on 2011-12-10
Well, when I do it, it doesn't. The option for multi-frame capture is still greyed out, and I can't choose any file format but XWD.  EDIT: I had to reinstall it by manually deleting all its files, then reinstall it. It's working fine, just the sound doesn't. It says 'Error accessing sound input from /dev/dsp', and I see the option for that in preferences but I don't know what to set it to. Could anyone help?

---

### Post by UmlautBanana on 2011-12-11
bump?

---

### Post by UmlautBanana on 2011-12-12
I hate to bump twice, but... yeah.

---

### Post by oldtimer7777 on 2011-12-12
> **UmlautBanana said:**
> I hate to bump twice, but... yeah.

Sorry for the delay..   Didn't you say you installed the one you a running from source?

Uninstall the one you installed from source completely and lets start fresh again..

And install the one from the repositories:

```
sudo apt-get install xvidcap
```Make sure to clean your configuration settings for that application before you reinstall it.

What is the result? Try invoking it from terminal to watch for errors displayed in the command line.

---

### Post by ranchodas on 2012-10-03
I have same problem there and re-install many time but nothing change. The choice Multi-Frame is grayed out so cannot choose it ](*,)

---

