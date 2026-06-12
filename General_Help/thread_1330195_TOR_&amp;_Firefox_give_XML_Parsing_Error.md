---
title: "TOR &amp; Firefox give XML Parsing Error"
date: 2009-11-18
forum: General Help
---

### Post by MIH1406 on 2009-11-18
I have installed TOR and Vidalia when I tried to use it with Fx 3.5.5 using Torbutton after running tor via vidalia and make sure that vidialia's icon is green. I cannot surf the Internet using Tor and this is what I get:

```
XML Parsing Error: undefined entity
Location: jar:file:///usr/lib/xulrunner-1.9.1.5/chrome/toolkit.jar!/content/global/netError.xhtml
Line Number 60, Column 12:    <title>&loadError.label;</title>
-----------^
```

SOLVED by installing privoxy.

---

### Post by baisong on 2009-12-14
I have the same exact error message, on FF 3.5.5 and Karmic.

I'm in China and use a proxy to access censored news (like reuters, slashdot) and personal files on Google docs, picasa and youtube) and a few small websites I maintain. After the party began blocking tor and i switched from Kubuntu to ubuntu (around the release of karmic) I added bridges and can view some blocked sites, but frequently get this error, and reloading doesn't appear to make a difference.

I have the newest versions of tor, privoxy, torbutton and vidalia. everything should be fine, but for the time i have to log into vista to access things... :?

---

### Post by baisong on 2009-12-15
Update: 

I removed and reinstalled privoxy and it worked! ...until the next time I turned on my computer. 

Do I have to remove and reinstall every time I want to read good news? What's a terminal script I can automate that with? =p

---

