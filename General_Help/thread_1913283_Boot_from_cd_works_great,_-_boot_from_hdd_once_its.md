---
title: "Boot from cd works great, - boot from hdd once itstalled - not so great"
date: 2012-01-22
forum: General Help
---

### Post by nonaimer on 2012-01-22
Hello, 

I have currently installed ubuntu 10.04 on my laptop, dell 15z.
Brightness control does not work and the resolution highest is 1024x768, BUT on the live cd works perfectly, with 1366x768 highest.

What can i do to preserve these settings?

Please help me out, this is the last thing i need to do to start working!

---

### Post by NightFoxyarrith on 2012-01-22
You could try installing the nvidia drivers. Use this command to open the driver manager from the terminal
```

sudo jockey-gtk

```
From there you should install the current nvidia driver. If this doesn't do the trick, you could always try the nvidia driver downloaded from their website and doing a manual install, you can find instructions here: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
and for manual install they can be found here: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

