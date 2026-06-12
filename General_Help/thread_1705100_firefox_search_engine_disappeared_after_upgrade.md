---
title: "firefox search engine disappeared after upgrade"
date: 2011-03-11
forum: General Help
---

### Post by mimmo.marozzi on 2011-03-11
After today's update the search engines displayed in the search box disappeared....
How to restore the default ones?

---

### Post by Frogs Hair on 2011-03-11
You can restore defaults in manage search engines . Click the down arrow in the search box on the right  and select manage search engines and choose restore to defaults.

---

### Post by texpat on 2011-03-12
I have the same problem, so I'll just piggyback on this thread:

The "Restore Defaults" button is disabled on my FF. There's a "get more search engines..." link that takes me to a firefox plugins site - no help in adding the lost search engines, though.

Can this be done manually somewhere?

---

### Post by Vest on 2011-03-12
The only search engine that I have is the ask.com. It seems that my Google and Wiki search engines disappeared.

---

### Post by Krytarik on 2011-03-12
You should also check out the OP's duplicate thread:
[http://ubuntuforums.org/showthread.php?t=1704788](http://ubuntuforums.org/showthread.php?t=1704788)

---

### Post by texpat on 2011-03-12
Cheers Krytarik, that's where I found my answer.

For the benefit of others, here's what I did:

Located /usr/lib/firefox-3.6.15/searchplugins/en-US/ and copied the xml files to /usr/share/xul-ext/ubufox/searchplugins/

(Re-)Started FF and I was good to go.

---

### Post by carra on 2011-03-17
This did the trick for me!
Thanks a lot from Italy!


> **texpat said:**
> Cheers Krytarik, that's where I found my answer.

For the benefit of others, here's what I did:

Located /usr/lib/firefox-3.6.15/searchplugins/en-US/ and copied the xml files to /usr/share/xul-ext/ubufox/searchplugins/

(Re-)Started FF and I was good to go.

---

### Post by Krytarik on 2011-03-17
I should mention that the OP of another thread regarding those issue  found a bug report earlier, it seems to get fixed in the near future, it also includes a temporary workaround:
[https://bugs.launchpad.net/ubuntu/+source/language-pack-zh-hans-base/+bug/732768](https://bugs.launchpad.net/ubuntu/+source/language-pack-zh-hans-base/+bug/732768)

---

