---
title: "Recommended swappiness for Lubuntu on 256mb RAM"
date: 2010-04-09
forum: General Help
---

### Post by themusicalduck on 2010-04-09
I've installed Lubuntu 10.04 onto a laptop with 256mb ram and I'm trying to get as best performance I can out of it. I've googled around on this.. but there seem to be many conflicting opinions on it. Some people say that lowering swappiness is a bad idea on a low ram system, as it can cause things to lock up if you open too many ram intensive programs. On the other hand, some people say it helps massively to use a low swappiness value.

I've been using the laptop with swappiness = 10 for a while and it definitely feels quite a bit quicker. Although I'm inclined to be safe and go for default, just because the laptop is for a friend and I don't want him to have problems later on.

It is Lubuntu, so all the programs and the desktop is lightweight, except for a few like open office and gimp which I've installed.

Also the swap FAQ actually recommends using swappiness = 10 [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)
but doesn't mention low end systems having problems with that.

Can anyone give their opinions? I'm feeling a bit lost on it.

---

### Post by darolu on 2010-04-09
With 256MB of RAM I wouldn't use a swappiness of 10; although if I remember correctly the default is 60 and I find it too high, settle for something in the middle, 30 - 40 should provide a good balance between speed and stability. Talking about stability, your friend probably won't appreciate bugs that may appear with 10.04 beta, I'd recommend installing 9.10 and upgrade when 10.04 comes out as a stable release.

---

### Post by themusicalduck on 2010-04-09
I see where you're coming from about using the beta. I've installed it because I probably won't be able to get to his laptop again for a while, and I don't think he'll want to install 10.04 by himself. Especially a clean install. This way he has the LTS already and doesn't have to worry for a few years about upgrading.

It definitely seems stable as is, so I'll tell him not to install any updates until 10.04 is actually finished.

I'll have a try with swappiness somewhere midway to give it a bit of a boost. Thanks for the reply.

---

