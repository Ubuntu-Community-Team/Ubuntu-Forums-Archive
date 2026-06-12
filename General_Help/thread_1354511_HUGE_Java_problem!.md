---
title: "HUGE Java problem!"
date: 2009-12-14
forum: General Help
---

### Post by Silvenium on 2009-12-14
I converted mom's computer to Ubuntu (9.10) for Christmas, and everything was fine... I could even play on her Facebook applications/games without a problem. ...Until I wanted to play Runescape. The advertisements and 'Play Runescape' are Java-based, I'm presuming. When I even get ON the page for Runescape, my screen goes black, then the 'Ubuntu' loading screen (brown/black with white lights and logo in the middle) appears and will never go away. It switches between this, and a black screen, and cannot be fixed unless I do a hard shut down (at the button). I've taken Firefox and java off multiple times and re-installed them, to no avail. PS: I use 9.10 as well and both Flash and Java work fine on mine.

---

### Post by dcstar on 2009-12-14
> **Silvenium said:**
> I converted mom's computer to Ubuntu (9.10) for Christmas, and everything was fine... I could even play on her Facebook applications/games without a problem. ...Until I wanted to play Runescape. The advertisements and 'Play Runescape' are Java-based, I'm presuming. When I even get ON the page for Runescape, my screen goes black, then the 'Ubuntu' loading screen (brown/black with white lights and logo in the middle) appears and will never go away. It switches between this, and a black screen, and cannot be fixed unless I do a hard shut down (at the button). I've taken Firefox and java off multiple times and re-installed them, to no avail. PS: I use 9.10 as well and both Flash and Java work fine on mine.

Possibly a video driver issue.

---

### Post by Silvenium on 2009-12-14
> **dcstar said:**
> Possibly a video driver issue.

 What would I have to do to fix it? She used to be able to play the game in HD, but not the few seconds that it worked tonight. It said there was a problem or something.  I also did a video test, but it was failed.

---

### Post by jamesstansell on 2009-12-15
There a 3 java plugins available for firefox in recent ubuntu releases.  Two are associated with sun-java and an additional one is associated with openjdk.  The first step is probably to figure out which one firefox is using.  (It's possible to install more than one to firefox but it will only use one at a time.)

If you choose Tools -> Add-ons and go to plugins, which java-related plugins do you see?  (If you happen to see something like npjp2.so it is the newer plugin from Sun.)
I would suggest that you uninstall all but one plugin from firefox.

For playing runescape I think (sigh) that the sun plugins are still preferred.  As I mentioned above the newer one has libnpjp2.so for the filename, and is probably being used for a fresh install of sun-java6-plugin.  libjavaplugin_oji.so is the name of the older plugin from sun.

Regards,

-james.

---

