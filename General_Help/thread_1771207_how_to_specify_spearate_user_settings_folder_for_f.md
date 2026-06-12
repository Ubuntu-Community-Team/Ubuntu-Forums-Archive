---
title: "how to specify spearate user settings folder for firefox 3.6 alongside firefox 4.0"
date: 2011-05-30
forum: General Help
---

### Post by bvraghav on 2011-05-30
Hi I had installed Firefox 3.6, for testing purposes, while having Firefox 4.0 already installed. And, while starting, figured out that, both of them support different versions of firebug, and both of them want to save the setting within the same folder.

What is the work around. Or, more specifically, how to tell my installation of ff-3.6 in /opt/firefox-3.6, to look for user settings in ~/.firefox-3.6/extensions, rather than looking into ~/.mozilla/extensions? (And of course do the same while installing the addons too...)

---

### Post by hwttdz on 2011-05-30
I think it should be sufficient to use different firefox profiles for each (firefox -ProfileManager, then firefox -P firefox4acctname).  Failing that you could make a new user account, say firefox40, and use ssh -X firefox40@127.0.0.1 "firefox-4". And then you'll really keep things entirely separate.

---

