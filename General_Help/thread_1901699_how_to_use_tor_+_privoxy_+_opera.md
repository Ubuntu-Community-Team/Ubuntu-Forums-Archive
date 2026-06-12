---
title: "how to use tor + privoxy + opera?"
date: 2011-12-29
forum: General Help
---

### Post by cacodemonio on 2011-12-29
Hello, it seems I cannot get the Opera browser to cooperate with tor and privoxy. See, I installed tor using the debs from the Tor project site, plus privoxy. I started vidalia and tor works, since I could start it from firefox using the tor button.

But under Opera I can't. I followed the instruction telling that I must set the http proxy to 127:0.0.1:8118. I did it. However, that does not work since the site check.torproject.org keeps telling me "Sorry. You are not using Tor."

---

### Post by ManualSparrow on 2011-12-29
You sure about that ip address? Googling it just brings up your post.

---

### Post by sleepingdragon on 2011-12-29
If you're using Tor from the repos, it's out of date.

However, change Opera to use SOCKS (v5) and fill in with 127.0.0.1:9050 (blank everything else), then test your ip address from there.

[torproject.org]("http://torproject.org") are doing a browser bundle that supplies Tor, Aurora browser and Vidalia to get things running. No permanent install, and everything works as it should. You click on one file to start Vidalia, and it will auto-run Aurora for you. My only change to the Tor bundle is to add Chatzilla to Aurora for IRC sessions.

---

### Post by cacodemonio on 2011-12-29
Thanks sleepingdragon, your advice about using only SOCKS (v5) worked perfectly. Problem solved.

---

### Post by ottosykora on 2011-12-29
@cacodemonio

personally I would not recommend you to use opera with tor, as most browsers today with the exeption of firefox (aurora) can not be made to work with tor safe.
Non modified browsers tend to call for many helpers , plugins and other addons and those may then communicate and bypass the tor connection.

So using opera via tor, you may as well gain speed and switch off tor completely.

---

### Post by d3v1150m471c on 2011-12-29
what is the point in using tor if you're using a browser that could nuke your anonymity? You may also want to check if opera isn't leaking your dns queries.

---

### Post by sleepingdragon on 2011-12-30
Yes, Opera would not be my first choice. On top of not being correctly configured and leaking data requests all over the place, it also has Opera Turbo, a unique caching service designed to speed up your connection. Data passes through Opera's servers, so it's another data collection point.

Not good.

Go with the Tor bundle. The web browser has been especially configured to do the job, it's preloaded with the right proxy settings, back-end configurations, and is loaded with HTTPSEverywhere and NoScript.

If Opera is your thing, then enjoy it, but make sure you stop those data leaks!

---

