---
title: "Using too much RAm at idle..."
date: 2010-07-17
forum: General Help
---

### Post by uRock on 2010-07-17
At bootup I am using too much RAM. How can I lighten the usage?

```
rabbit@rabbit-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1944       1272        672          0         42        342
-/+ buffers/cache:        887       1057
Swap:         2078          0       2078

```

Thanks,
uRock

PS, This thread will be worthless until UF's server starts allowing me to upload screenshots.

---

### Post by dcstar on 2010-07-17
> **uRock said:**
> At bootup I am using too much RAM. How can I lighten the usage?
.........

No you are not, look at the many other threads addressing this non-problem.

---

### Post by uRock on 2010-07-17
It is a problem for me. Jaunty and Karmic used around 400MB and Peppermint uses 150MB, though it is using LXDE.

Here is the screenshot that wouldn't upload for some reason earlier.

---

### Post by Rubi1200 on 2010-07-17
A couple of possible culprits pop out at first glance; compiz and clamd.

You might want to consider turning desktop effects off.

As for clamd (I assume that is the antivirus program), do you really need it at startup?

You can also look at this:

```
initctl list
```

and see if you really need every service running.

Hope this helps.

---

### Post by uRock on 2010-07-17
I was able to kill clamd, but I can't figure how it was installed. I tried sudo apt-get remove clamd, but it said it doesn't exist. I am going to run a test install of Xubuntu and see how it looks.

Thanks,
uRock

---

### Post by uRock on 2010-07-18
Xubuntu is a little better, but I don't think it would be worth while to change my production system. I guess Ubuntu is following the Windows path of wasting RAM. I will work with it more and try to bring it down.

---

### Post by cariboo on 2010-07-18
Could it be you are being affected by bug #[lpbug]501715[/lpbug]?

---

### Post by mcduck on 2010-07-18
> **uRock said:**
> I was able to kill clamd, but I can't figure how it was installed. I tried sudo apt-get remove clamd, but it said it doesn't exist. 
That's because the package isn't called clamd, it's clamav. ;)

---

### Post by uRock on 2010-07-18
@Cariboo, Thanks! It looks like there is supposed to be an update that fixes it, so I am not sure if it is the same thing.

@McDuck, After opening Synaptic I realized clamd was part of ClamAV. I don't remember installing it.

I have removed a few programs and it is using a bit less RAM.

---

### Post by MaxIBoy on 2010-07-18
Of course there are some things you can do to reduce the load on your system, and that's fine, but you won't succeed in significantly lowering down your RAM usage. Unused RAM is wasted RAM-- the Linux kernel tries to cache commonly-used files in RAM to speed up access times and overall performance. This cache can easily be relinquished if the RAM is needed for something else, but in general you want close to 100% RAM usage at all times. If you disable some startup services, then the RAM you free up is going to get used for cache, which is perfectly fine and can improve performance.

---

### Post by uRock on 2010-07-18
> **MaxIBoy said:**
> Of course there are some things you can do to reduce the load on your system, and that's fine, but you won't succeed in significantly lowering down your RAM usage. Unused RAM is wasted RAM-- the Linux kernel tries to cache commonly-used files in RAM to speed up access times and overall performance. This cache can easily be relinquished if the RAM is needed for something else, but in general you want close to 100% RAM usage at all times. If you disable some startup services, then the RAM you free up is going to get used for cache, which is perfectly fine and can improve performance.
Thanks for the explanation. I have a VBox that I am using for a few apps that don't run correctly on my 64bit install. By the time I fire up the VBox and open Firefox the RAM gets fully loaded. I am sure the system is safe with moving cache to Swap, if that is what it does.

Cheers & Beers,
uRock

---

### Post by uRock on 2010-07-19
After running Ubuntu 10.04 in a VBox, I see how it uses cache and I am seeing that it isn't really a problem.

Cheers & Beers,
uRock

---

### Post by uRock on 2010-07-19
> **dcstar said:**
> No you are not, look at the many other threads addressing this non-problem.
I apologize, you were right. I guess I just needed to learn how the new Ubuntu utilizes RAM. The more one has, the more Ubuntu will cache to help make things run faster.

---

### Post by philinux on 2010-07-19
```
            total       used       free     shared    buffers     cached
Mem:           993        810        183          0         67        498
-/+ buffers/cache:        **[COLOR="Red"]244[/COLOR]**        748
Swap:          996          0        996

```

From my 32 bit install. My 64 bit uses twice as much 500 meg instead of 244. But this is normal.

---

