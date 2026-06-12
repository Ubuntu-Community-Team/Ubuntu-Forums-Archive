---
title: "Need Help: Program Manager not working."
date: 2006-03-22
forum: General Help
---

### Post by kenweill on 2006-03-22
My program manager is not working anymore. Or software updates.
The update button is not working properly.
It always states that "There is 1 update available" even if I have downloaded and installed the update already.

Its the WINE package.
I update WINE 0.9.10 and installed succesfully. But when I reboot the machine, WINE appears again in the Software Update window. Same version.
I did download and install it again, but when I reboot the machine, it appears again in the program manager.

What is wrong with my Ubuntu?
Need help. I guess my software update is not working anymore.

---

### Post by Blunts on 2006-03-23
I had a similar problem with an older version of WINE. The new install did not identify itself even though it was updated fully. I fixed it by changing my repositories list with : 

```
## Wine Repository
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```

The old links I had were slightly different

---

