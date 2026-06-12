---
title: "Azureus"
date: 2006-05-16
forum: General Help
---

### Post by markr on 2006-05-16
Has anyone actually got this working in KDE?

I was using it happily in Gnome, but when I moved over to KDE I keep getting exceptions.

I've tried the version in the repositories and also manually installing to no avail.

I don't have access to my system at the moment so can't post the error messages.I have the SUN Java 1.4 packages installed.

Thanks

Mark.

---

### Post by barbarian on 2006-05-16
hi,
what's wrong with ktorrent?

---

### Post by markr on 2006-05-16
I'm in the middle of a transitions from WinXP,  I use Azereus on WinXP and effectively wanted to 'share' my partially downloaded torrents.

Say I was have way through downloading Dapper in WinXP,  I may want to finish it off in Linux, with Azuerus I can do this.  I tried to pick up the .torrent file in Ktorrent, but it did not detect that I'd already partially downloaded the file and so tried to start again.

If I can share .torrent files between KTorrent and Azureus (on WinXP) tell me now 'cause I'll be one happy chappy !!!

---

### Post by markr on 2006-05-16
I'm in the middle of a transitions from WinXP,  I use Azereus on WinXP and effectively wanted to 'share' my partially downloaded torrents.

Say I was have way through downloading Dapper in WinXP,  I may want to finish it off in Linux, with Azuerus I can do this.  I tried to pick up the .torrent file in Ktorrent, but it did not detect that I'd already partially downloaded the file and so tried to start again.

If I can share .torrent files between KTorrent and Azureus (on WinXP) tell me now 'cause I'll be one happy chappy !!!

---

### Post by markr on 2006-05-16
I'm in the middle of a transitions from WinXP,  I use Azereus on WinXP and effectively wanted to 'share' my partially downloaded torrents.

Say I was have way through downloading Dapper in WinXP,  I may want to finish it off in Linux, with Azuerus I can do this.  I tried to pick up the .torrent file in Ktorrent, but it did not detect that I'd already partially downloaded the file and so tried to start again.

If I can share .torrent files between KTorrent and Azureus (on WinXP) tell me now 'cause I'll be one happy chappy !!!

---

### Post by markr on 2006-05-16
I'm in the middle of a transitions from WinXP,  I use Azereus on WinXP and effectively wanted to 'share' my partially downloaded torrents.

Say I was have way through downloading Dapper in WinXP,  I may want to finish it off in Linux, with Azuerus I can do this.  I tried to pick up the .torrent file in Ktorrent, but it did not detect that I'd already partially downloaded the file and so tried to start again.

If I can share .torrent files between KTorrent and Azureus (on WinXP) tell me now 'cause I'll be one happy chappy !!!

---

### Post by ash211 on 2006-05-16
I'm running Azureus just fine on KDE, both in Dapper and in Breezy before I upgraded.  I suspect the problem lies with your Java.  Type ```
sudo update-alternatives --config java
``` and make sure that the Sun Java is selected.  

If that doesn't work, try getting ahold of Sun's Java 1.5

---

### Post by DivadLarsen on 2006-05-16
Well, on my Kubuntu I just downloaded the *.deb file from [www.debian.org](www.debian.org). But note that you have to remove libseda-java before you can install.. It conflicts with azureus... But after that I haven't had any problems....

---

### Post by barbarian on 2006-05-16
I never used torrent clients under windoze. In linux I tried bittornado(command line client) and ktorrent, and never had probs with autocompletion.. One issue I had - ktorrent randomly crashed, but it was under kde 3.4.3, with 3.5.2 everything works fine..

---

### Post by stoeptegel on 2006-05-16
[QUOTE=markr]I tried to pick up the .torrent file in Ktorrent, but it did not detect that I'd already partially downloaded the file and so tried to start again.

If I can share .torrent files between KTorrent and Azureus (on WinXP) tell me now 'cause I'll be one happy chappy !!![/QUOTE]

That's because KTorrent works with an partial import plugin(from file menu) which you have to enable in plugin settings.

---

### Post by markr on 2006-05-17
Not sure how I managed to post my initial reply 4 times!!!

Thanks for the replies.

I never noticed the partial download import, that will do the trick if I can't get Azuereus working (And I intend to move to KTorrrent when I've completed the transition to Linux).

regarding the suggestion by ash211, when I issue that command I am told that my current default is:

/usr/lib/j2se/1.4/bin/java

Doing a java -version shows me "Blackdown-1.4.2-02, mixed mode."

---

### Post by MillDaKill on 2006-05-19
[QUOTE=ash211]I'm running Azureus just fine on KDE, both in Dapper and in Breezy before I upgraded.  I suspect the problem lies with your Java.  Type ```
sudo update-alternatives --config java
``` and make sure that the Sun Java is selected.  

If that doesn't work, try getting ahold of Sun's Java 1.5[/QUOTE]


Thank you so much.

---

