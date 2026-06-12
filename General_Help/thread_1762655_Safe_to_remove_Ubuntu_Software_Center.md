---
title: "Safe to remove Ubuntu Software Center?"
date: 2011-05-19
forum: General Help
---

### Post by OldTimeyJunk on 2011-05-19
Hello!

Just a wonder, is it safe to remove Ubuntu Software Center?
I am guessing NO, but is there any applications that require the Software Center? Or can I just live with Synaptic?

---

### Post by mikewhatever on 2011-05-19
It should be safe, but test it first with
```
sudo apt-get -s remove software-center
```

The '-s' is there for simulation, so that nothing will actually happen.

PS: Is the Software Center installed in Kubuntu?

---

### Post by OldTimeyJunk on 2011-05-19
No, I originally had Ubuntu 10.04. I then installed KDE (kubuntu-desktop) on it, so it's now Kubuntu 10.04 (with the Gnome stuff left behind). I don't think Kubuntu comes with Ubuntu Software Center.

---

### Post by OldTimeyJunk on 2011-05-19
Thanks!
Software Center is gone!
I don't think Kubuntu comes with it. When I removed Software Center, it took ubuntu-desktop (Gnome) with it.
Thanks again for your help!

---

### Post by nrundy on 2011-05-19
why did u want to remove it? need disk space?

---

### Post by mikewhatever on 2011-05-19
You can remove all Ubuntu related packages and only keep those of Kubuntu.
[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

---

### Post by OldTimeyJunk on 2011-06-03
I wanted to remove it as I had a dock that acted like the Android menu. It had a browser button etc. But, when it came to an "Android Market" icon I made it open Synaptic and never used USC again, so I wanted to get rid.

---

