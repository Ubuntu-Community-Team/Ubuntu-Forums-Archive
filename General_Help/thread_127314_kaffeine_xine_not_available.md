---
title: "kaffeine xine not available"
date: 2006-02-08
forum: General Help
---

### Post by stangbang on 2006-02-08
I installed kmplayer, and since then have been having a problem with kaffeine. (kmplayer was not working properly so I removed it). Anyways after installing kmplayer the xine engine was missing, and a kmplayer engine was there. This remained to stay there even after uninstalling kmplayer. After reinstalling kaffeine a few and doing other things I was able to get the kmplayer engine to disapear. Then I was faced with not having the xine engine. So I reinstalled kaffeine AGAIN... and was able to get it to appear and work.

The problem now is that after a while (possibly after rebooting or doing other things) the xine engine disapears again, and I have to uninstall kaffeine and reinstall it to get the xine engine back. I dont want to be stuck with uninstalling and reinstalling kaffeine every time I want to watch a dvd.

---

### Post by Rog131 on 2006-02-09
Do you mean KPlayer or KMPlayer ?

KPlayer is a KDE media player based on MPlayer.
[http://kplayer.sourceforge.net/](http://kplayer.sourceforge.net/)

The KMPlayer is a KPart plugin for Konqueror.
[http://kmplayer.kde.org/](http://kmplayer.kde.org/)

KUDOS ([http://kudos.berlios.de/kf/kf1.html#kplayer](http://kudos.berlios.de/kf/kf1.html#kplayer)) says: KPlayer currently conflicts with Kaffeine. I.e. you can either have KPlayer or Kaffeine, but not both. Installing KPlayer will uninstall Kaffeine.

---

### Post by stangbang on 2006-02-09
It was kmplayer.

Anyways I was able to fix it. Turns out that when I installed it I also updated the libxine binary to a different version. This is what was causing the problem. I installed the ubuntu one again and all is working well.

---

