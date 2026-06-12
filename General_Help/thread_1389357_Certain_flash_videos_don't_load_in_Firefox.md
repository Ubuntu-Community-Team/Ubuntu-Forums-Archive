---
title: "Certain flash videos don't load in Firefox"
date: 2010-01-24
forum: General Help
---

### Post by ternarybit on 2010-01-24
Hey, got a strange issue here. A little background:
[LIST]
[*]Running 9.04 x86_64
[*]On Q9550 w/ 4GB
[*]Running updated Firefox from the repos
[*]Manually installed Flash 10 rc2 x86_64 from Adobe
[*]Running Adblock Plus
[*]WAS running NoScript (latest version)
[/LIST]

The story goes: I was happily browsing any and all flash content when I got the paranoid feeling that I should probably install NoScript to have fine-grained control over what content executes (specifically tracking JavaScript).

Well of course NoScript by default blocks everything, so I manually unchecked Flash, etc. No problem, right? Well I come to find out that some flash works now, some doesn't (e.g. youtube works, marshillchurch.org doesn't for some reason).

No big deal, must be ABP acting up? Nope. Nothing at all on marshillchurch.org blocked. Fine. Uninstall NoScript, it's not a big deal anyway. Oops! Still no video! Just blank box where video used to be.

Since then I have tried:
[LIST]
[*]apt-get remove firefox && apt-get install firefox
[*]manually install libflashplayer.so again
[/LIST]

I'm out of ideas. Any thoughts? thank you!

---

