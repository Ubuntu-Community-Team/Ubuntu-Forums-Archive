---
title: "UNKNOWN? encrypted swap partition ?"
date: 2012-06-23
forum: General Help
---

### Post by svaens on 2012-06-23
Hi all, 

I've dual booted my computer with older ubuntu 10.10 and ubuntu 12.04, and for 12.04 i've selected to encrypt my home. 

When I boot back into 10.10, my swap had been ruined, so I reformatted and reassigned in fstab so that it was recognized. All fine. 

Now i'm back in 12.04.... have I ruined it for 12.04 ?
The thing is, so it is encrypted, does gparted recognize this? 

Is there some sort of default fallback virtual swap used if the real swap partition is not used?

What I want to verify is if my crypt swap is correctly mounted and used. how can I tell this for sure? 

gparted shows me now an 'UNKNOWN' partition that I had chosen as my swap. No longer a swap partition? Encrypted swap partition? What is the case? (where can I read about this?)

I tend to guess it is working, as 'free' shows 6024 megabytes in total for swap, which sounds about right, with gparted showing the 'UNKNOWN' partition at 5.88Gig .. (about the same). 

My fstab looks like this:


```
# swap was on /dev/sda1 during installation
#UUID=763b8f42-8c64-49ce-88ce-f798f18b906f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

and the output from free:

```
sean@svUbuntu10:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3022       2101        920          0        249        800
-/+ buffers/cache:       1051       1971
Swap:         6024          0       6024

```


Does all this sound like it is working as expected ? 

(sorry for the stupid question)

---

### Post by oldfred on 2012-06-24
If you elect to encrypt /home, swap is also encrypted. Gparted and most tools then cannot see an encrypted swap partition as it is just raw data space.

You are then an exception to being able to use the same swap for multiple installs. One is not encrypted and the other is so they cannot be the same.

---

