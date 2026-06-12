---
title: "Chromium nightly doesn't like &quot;old&quot; Flash"
date: 2011-01-14
forum: General Help
---

### Post by olwe on 2011-01-14
I've got Chromium set up for nightly build updating on my Ubuntu 10.04 and I do run Update Manager daily. Lately, I get the message "The Flash plug-in was blocked because it is out of date." It gives me the option to "Run this time" or "Update plug-in." Is this a Chromium nightly build "to be expected" problem, or should I truly try to update Flash? If it's Flash that needs updating, what should I add to my Software Sources to get this newer Flash that I'm not getting normally?

---

### Post by bowens44 on 2011-01-14
> **olwe said:**
> I've got Chromium set up for nightly build updating on my Ubuntu 10.04 and I do run Update Manager daily. Lately, I get the message "The Flash plug-in was blocked because it is out of date." It gives me the option to "Run this time" or "Update plug-in." Is this a Chromium nightly build "to be expected" problem, or should I truly try to update Flash? If it's Flash that needs updating, what should I add to my Software Sources to get this newer Flash that I'm not getting normally?

I update mine daily also and I have not had this issue. Haven't done it yet today but did update yesterday.

---

### Post by germania on 2011-01-16
I'm having the same problem as well on my laptop, but curiously not on my desktop (both maverick with ppa chromium nightly).  Very annoying.  I tried to upgrade flash and got some message about "The package adobe-flash is virtual".

---

### Post by germania on 2011-01-16
I should have waited before posting, I just grabbed the preview release tar.gz from [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html) for 64 bit linux and manually replaced /usr/lib/chromium-browser/plugins/libflashplayer.so with that version, and the problem appears to be fixed.  Hopefully this helps other people too!

---

### Post by lovinglinux on 2011-01-16
> **germania said:**
> I should have waited before posting, I just grabbed the preview release tar.gz from [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html) for 64 bit linux and manually replaced /usr/lib/chromium-browser/plugins/libflashplayer.so with that version, and the problem appears to be fixed.  Hopefully this helps other people too!

You could also install the 64bit using my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension for Firefox and disable the flash version bundled with Chrome, from about[noparse]:[/noparse]plugins. This has the advantage that a Chrome update wouldn't replace the flash plugin and you can keep flash 64 updated due to Flash-Aid update check.

---

### Post by rabb_i on 2011-01-25
Thanks, worked perfectly!

> **germania said:**
> I should have waited before posting, I just grabbed the preview release tar.gz from [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html) for 64 bit linux and manually replaced /usr/lib/chromium-browser/plugins/libflashplayer.so with that version, and the problem appears to be fixed.  Hopefully this helps other people too!

---

