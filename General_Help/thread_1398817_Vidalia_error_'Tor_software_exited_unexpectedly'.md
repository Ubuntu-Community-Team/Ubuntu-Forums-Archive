---
title: "Vidalia error: 'Tor software exited unexpectedly'"
date: 2010-02-05
forum: General Help
---

### Post by L4U on 2010-02-05
Everytime I shutdown/restart my computer without properly turning off the Tor network and get the following message from Vidalia:

"Vidalia detected that the Tor software exited unexpectedly"

The only way I can get Vidalia to work again is to reinstall Vidalia.


Anybody know a permanent way to correct this error?

---

### Post by Philip550c on 2010-02-13
I'm having the same problem, didn't know I had to turn it off everytime. Hopefully someone else can help us but at least you helped me for now, havent tried reinstalling vidalia.

---

### Post by 3dgard on 2010-09-19
I found a permanent solution online :P It fixed my problem with Vidalia/Tor/Ubuntu

[http://www.noobrescue.com/blog/vidalia-detected-that-the-tor-software-exited-unexpectedly](http://www.noobrescue.com/blog/vidalia-detected-that-the-tor-software-exited-unexpectedly)

I hope this helps!

---

### Post by brambram on 2012-02-01
worked perfectly, and wasn't hard to do, thank you!

---

### Post by ooolongT on 2012-03-31
Didn't work for me.  I ended up with the author's example and that didn't work, when I tried to restart Tor, the terminal replied with:
```
ABORTED: Tor configuration invalid:
Mar 30 21:47:15.568 [notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Mar 30 21:47:15.568 [warn] Linelist option 'HashedControlPassword' has no value. Skipping.
Mar 30 21:47:15.568 [warn] Failed to parse/validate config: Unknown option '16:315A98F7F03E3EDA60DD1C7637AB174A9BC880E68B434EFA1B63884CC3'.  Failing.

``` 

So I removed the # in front of HashedControlPassword and now I get this:

```
ABORTED: Tor configuration invalid:
Mar 30 21:56:51.560 [notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Mar 30 21:56:51.560 [warn] Failed to parse/validate config: Unknown option '16:315A98F7F03E3EDA60DD1C7637AB174A9BC880E68B434EFA1B63884CC3'.  Failing.
Mar 30 21:56:51.560 [err] Reading config failed--see warnings above.

```

Any insights?

---

