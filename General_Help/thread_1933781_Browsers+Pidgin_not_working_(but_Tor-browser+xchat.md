---
title: "Browsers+Pidgin not working (but Tor-browser+xchat are)"
date: 2012-03-01
forum: General Help
---

### Post by MosesMiller on 2012-03-01
So it's not a new install, and I haven't made any major changes recently...but this afternoon my firefox and pidgin failed to connect. (Pidgin returns "no address associated with hostname"). I tried elinks (another browser) and it also failed to connect...so it's not a firefox issue or anything...but then when I tried my Tor-Browser-Bundle, *IT* worked. (Which is how I'm posting here). And when I tried XChat, *it* worked (also through Tor)...other than the gods giving me a sign to stop using non-Torified services...what the heck is going on?:confused:

But I'm still pretty newb, so it'd be helpful if you gave "for dummies" suggestions :)

Update: Just in case anybody stumbles across this thread time-travelling from the future, it turned out to be a problem with my router's DNS resolving...so it was a simple "sudo gedit /etc/resolv.conf" and then replace the IP address listed with 8.8.8.8 - though that IS a Google-system, so if you hate Google, you might want to try an OpenDNS number instead :)

---

