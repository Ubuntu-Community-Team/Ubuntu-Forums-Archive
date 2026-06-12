---
title: "Firefox awesome bar not working in 10.04"
date: 2010-04-29
forum: General Help
---

### Post by Fox5 on 2010-04-29
Hey all, my Firefox Awesome Bar isn't working in ubuntu 10.04. Instead of automatically redirecting keywords (ie, google goes to google, wikipedia to wikipedia) I'm just getting comcast's search page. I assume this can be fixed in about:config, I just don't know what setting.

---

### Post by linuxman94 on 2010-04-29
I do not believe the awesome bar does that.  It just shows your history and bookmarks on the drop-down menu.

If you want firefox to autofill the awesome bar when you type in a term, go to about:config and search for browser.urlbar.autoFill and double click it to change the value to true.  Restart firefox and it will autotfill for you.

---

### Post by darkstaar on 2010-04-29
> **linuxman94 said:**
> I do not believe the awesome bar does that.  It just shows your history and bookmarks on the drop-down menu.

Fox5 is correct. It works like that. Mine is working although I never use it like that.

@Fox5: Not sure but try looking in the **browser.urlbar...** sections in about:config

---

### Post by lovinglinux on 2010-04-29
> **darkstaar said:**
> Fox5 is correct. It works like that. Mine is working although I never use it like that.

@Fox5: Not sure but try looking in the **browser.urlbar...** sections in about:config

I think is Comcast that is redirecting, like OpenDNS does. Se [http://ubuntuforums.org/showthread.php?t=1428577](http://ubuntuforums.org/showthread.php?t=1428577)

---

### Post by Fox5 on 2010-04-29
> **lovinglinux said:**
> I think is Comcast that is redirecting, like OpenDNS does. Se [http://ubuntuforums.org/showthread.php?t=1428577](http://ubuntuforums.org/showthread.php?t=1428577)

That may be true, but it doesn't happen on my desktop with Firefox and Windows, nor on my phone with Fennec.

The browser.urlbar was off, but setting it to true hasn't fixed the problem.

---

### Post by lovinglinux on 2010-04-29
> **Fox5 said:**
> That may be true, but it doesn't happen on my desktop with Firefox and Windows, nor on my phone with Fennec.

The browser.urlbar was off, but setting it to true hasn't fixed the problem.

See [this then](http://lovinglinux.megabyet.net/?page_id=220#Address-bar-does-not-work--2). Make a backup first and close Firefox fist.

---

### Post by Fox5 on 2010-04-29
> **lovinglinux said:**
> See [this then](http://lovinglinux.megabyet.net/?page_id=220#Address-bar-does-not-work--2). Make a backup first and close Firefox fist.

My address bar works, it's just the firefox autoredirect doesn't.
Normally typing
google
Should redirect to [www.google.com](www.google.com). Instead it's being dns hijacked, but this doesn't happen on my other pcs.

---

### Post by egaudet on 2010-05-19
> **Fox5 said:**
> My address bar works, it's just the firefox autoredirect doesn't.
Normally typing
google
Should redirect to [www.google.com]("http://www.google.com"). Instead it's being dns hijacked, but this doesn't happen on my other pcs.

It's Comcast's Domain helper service, which you can disable.  You can do this via comcast.com, log into your account and go to users & settings then shut off domain helper.

---

