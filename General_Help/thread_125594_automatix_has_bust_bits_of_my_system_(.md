---
title: "automatix has bust bits of my system :("
date: 2006-02-04
forum: General Help
---

### Post by jonqrandom on 2006-02-04
so, i have (well... i had) a fairly regular ubuntu breezy install, installed from a recent CD, everything working fine... and i installed automatix, just like i have on my son's edubuntu machine, where it worked just fine thankyou.  unfortunately, on mine, it has killed firefox, and made synaptic believe that every available package but one is installed.  synaptic also starts up with *loads* of errors, repeatedly complaining it "Couldn't stat source package list [http://wherever.com](http://wherever.com) etc".

at this point i'm wondering if i should just re-install ubuntu, the only thing i really have to lose are my bookmarks, and i can just email them to myself...

please let me know if there's a quicker solution, though :)

luv'n'hugs
jonny random

---

### Post by varunus on 2006-02-04
Um...this sounds like a network connection problem to me.  Synaptic can't get any package lists because it can't connect to the internet, thus making it think that the only packages available are the ones you have installed.

Couldn't stat source package list means synaptic doesn't have an internet connection.

Check your net...how do you connect?  are you sure its working?  Can you hit "reload" in synaptic to get your package lists back?

I don't think this problem is with Automatix.

---

### Post by jonqrandom on 2006-02-04
ah...

:oops: 

my network cable unplugged, i guess during the install of firefox 1.5 ...

so, i've sorted the network and firefox now, however i'm still suffering from the synaptic errors...

---

### Post by codejunkie on 2006-02-04
refresh your sources in synaptic or run```
sudo apt-get update
```through a terminal.

---

### Post by jonqrandom on 2006-02-05
thankyou very much, all sorted now :)

---

