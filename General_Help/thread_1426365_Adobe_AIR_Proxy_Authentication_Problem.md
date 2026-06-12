---
title: "Adobe AIR Proxy Authentication Problem"
date: 2010-03-10
forum: General Help
---

### Post by achinton on 2010-03-10
Hi all,

I have an issue with Adobe AIR, which I use to run Tweetdeck. It keeps on asking me to authenticate for my proxy server - every time Tweetdeck tries to load someone's avatar, for instance, which is making it pretty unusable right now.

I'm not sure why it's doing this, other than that I've just upgraded to 9.10 (well, to Mint 8, actually, but I would think the issue is the same). I've got all my proxy settings working, and indeed AIR seems to be able to read the settings from somewhere (it autocompletes the authenticate box with the correct details), but it just doesn't seem to be able to authenticate once and then be done with it, like it had done previously.

Any ideas?

---

### Post by wanye on 2010-06-01
*bump*

I'm having the same problem too.

I upgraded from 8.10 to 10.04 (via 9.04/9.10) the other day, and now every time adobe air tries to access the internet, it pops up the proxy server dialog box. And when a program is hitting the proxy (up to) a hundred times a minute, this can get tiresome very quickly.

system>prefs>network proxy is set. Ive also got /etc/wgetrc ~/.bashrc and /etc/environment all with the correct proxy info in it

any ideas?

---

