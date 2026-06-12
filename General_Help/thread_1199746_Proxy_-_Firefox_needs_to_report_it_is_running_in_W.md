---
title: "Proxy - Firefox needs to report it is running in Windoze"
date: 2009-06-29
forum: General Help
---

### Post by lsemmens on 2009-06-29
My bank insists that I use either IE or Firefox as a browser to access their services and also want Windoze or Macinslosh OS. Is there any way that I can convince Firefox 3.0.11 on Jaunty to tell the bank that it is running in Windoze. Sort of like a proxy?

---

### Post by decoherence on 2009-06-29
> **lsemmens said:**
> My bank insists that I use either IE or Firefox as a browser to access their services and also want Windoze or Macinslosh OS. Is there any way that I can convince Firefox 3.0.11 on Jaunty to tell the bank that it is running in Windoze. Sort of like a proxy?

You need to spoof your user agent. Easily done with this [addon]("https://addons.mozilla.org/en-US/firefox/addon/59")!

---

### Post by itsjareds on 2009-06-29
If you don't want to install an addon for whatever reason, you can also change your user agent in Firefox's config.

Go to [about:config]("about:config"), right click and go to New > String, then name it "general.useragent.override" (no quotes). Then enter the user agent you want to appear to be using.

---

### Post by lsemmens on 2009-06-30
Thanks for the suggestions, I have been using "User Agent Switching" but that does not report to the satisfaction of the bank. Attached is a screenshot of about:config. what am I missing?

---

### Post by itsjareds on 2009-06-30
Not sure. Try changing your user agent to this (this is my user agent on Windows):

```
Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.0.11) Gecko/2009060215 Firefox/3.0.11
```

Then [check your user agent]("http://whatsmyuseragent.com/") to make sure things have changed.

---

### Post by lsemmens on 2009-07-01
No Joy with that either. Have a try here and see how you go: the site is nab.com.au and the login option is on the right hand side of the screen.

They say they support Firefox but insist that my browser is not supported (Firefox). If I elect to continue with my existing browser the screen is supposed to switch to a Username/Pwd prompt but, instead switches to a page called about:blank. The only way I can log on is via Windoze with Firefox using IEview.

---

### Post by DeMus on 2009-07-01
> **lsemmens said:**
> No Joy with that either. Have a try here and see how you go: the site is nab.com.au and the login option is on the right hand side of the screen.

They say they support Firefox but insist that my browser is not supported (Firefox). If I elect to continue with my existing browser the screen is supposed to switch to a Username/Pwd prompt but, instead switches to a page called about:blank. The only way I can log on is via Windoze with Firefox using IEview.

It sounds like pure discrimination to me. Why always only Windows? Are they getting paid by MS to do this?
This is so ridiculous: things like this still happen in the 21st century.

---

### Post by itsjareds on 2009-07-01
Sounds like they might be using some form of JavaScript browser validation. (e.g., call for a function only used in IE)

---

### Post by lsemmens on 2009-07-03
I agree. I'll tell them what I think, yet again! Eventually they'll get the flick when I'm certain all of my payments, etc are transferred to my other bank. Meantime, Virtualbox works. So that saves one headache.

---

