---
title: "Can't download Dropbox Daemon?"
date: 2009-07-20
forum: General Help
---

### Post by pointyblue on 2009-07-20
Hi,

I'm trying to install Dropbox on Ubuntu 9.04.

I've downloaded an installed the .deb-package. When I click the Dropbox icon it wants to download the proprietary Dropbox daemon - I click yes. It start downloading but it doesn't finish.

I've tried this numerous times and it's always unsuccessfull - sometimes the computer even freezes during download and I have to hit the power button.

Been visiting the Dropbox forum, it seems other people are having the exact same problem with 9.04 + Dropbox but I'havent found a solution yet.

Any ideas how to fix this. Or perhaps ideas for similar services that work with linux?

---

### Post by ddrichardson on 2009-07-20
Ubuntuone is the same thing but only has Ubuntu clients at the moment.  I'm running Dropbox on Jaunty and haven't encountered any issues - are you connected via a proxy?

---

### Post by pointyblue on 2009-07-20
No I'm not using proxy

I thought of Ubuntuone but I need to sync Ubuntu with Win XP + Vista, so...

Was considering Adrive with Gladinet but Gladinet is Windows only. Would be cool if there was a linux application that could mount virtual storage but I haven't been able to find one.

---

### Post by pointyblue on 2009-07-21
Found the problem: The wifi driver. (!)

Changed to the proprietary driver and it's working fine now.

Thanks for helping out.

:)

---

### Post by ddrichardson on 2009-07-21
Glad its fixed, I did wonder if it was connection related - the only time I have an issue with Dropbox is on resume where sometimes it will attempt to connect but never complete.

---

