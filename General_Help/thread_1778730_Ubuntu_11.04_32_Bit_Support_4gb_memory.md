---
title: "Ubuntu 11.04 32 Bit Support 4gb memory?"
date: 2011-06-09
forum: General Help
---

### Post by zKarp on 2011-06-09
I know with windows 32 it only supports ~3gb of memory. Unless you hack the kernel. which I did, to fully utilize the 4gb of ram. I guess it's a licensing thing on their part.

I still don't fully understand the meaning of 32 vs 64 just know 64 can use >4gb of ram in a single app when 32 can only use max 4 in one app.

Doese Ubuntu 32bit utilize my 4gb of ram or will it only use 3?

I have a macbook 5,1 with 4gb of ram so 64bit isn't really useful but I want all my hardware being used =).

Thanks hope you understand my quesiton. Typed fast cause I have other things to do.

---

### Post by seawolf167 on 2011-06-09
It isn't "in a single app" its that there are not enough addresses available for more than 4GB of RAM. You can work around this in a 32 bit version using something called Physical Address Extension (or PAE), more info can be found [here]("https://help.ubuntu.com/community/EnablingPAE").

My suggestion is that if you have 64 bit compatible hardware to use Ubuntu x86_64 since you won't loose anything, but instead gain functionality with the OS being 64bit. That said, however, most people here will probably suggest (and I lean this way for beginners) you use the 32 bit version since everything works a little better (IMO almost all the manual workarounds have been removed in the 64bit version now, but you still may run into some, flash is a notorious example).

---

