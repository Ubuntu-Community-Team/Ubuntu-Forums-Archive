---
title: "nvidia GS 7200 precise"
date: 2012-05-21
forum: General Help
---

### Post by Crempel on 2012-05-21
I am very sorry if this topic has been discussed already; I have searched all sort of posts  and have not found an answer. When raising this aubject in the "Internet Cafe"  I won the impression that I was the only one with this problem, but:

1. When using the gnome-shell, I get full 3-D performance (1600 fps).
2. Under unity i only get 2-D!
3. I have tried every canonical as well as propriety NVIDIA -driver under the sun -            always with the same result.

I am quite happy with gnome-shell but why does unity insist that my graphics card is not "3-D"?

Any hint would be appreciated.:)

---

### Post by haresear on 2012-05-21
Two possibilities come to mind.

1. Your 3D implementation lacks some specific 3D feature or option that Unity is looking for. There used to be a Unity test script that would tell you exactly why Unity 3D would refuse to run -- not sure if that is still available for 12.04. I haven't seen any mention of it lately.

2. Your card is explicitly blacklisted by Unity. There used to be a way to force Unity 3D to ignore the blacklist via command line, but I'm sorry I don't remember the command offhand, and I'm not sure it still works for 12.04.

---

### Post by Crempel on 2012-05-21
> **haresear said:**
> Two possibilities come to mind.

1. Your 3D implementation lacks some specific 3D feature or option that Unity is looking for. There used to be a Unity test script that would tell you exactly why Unity 3D would refuse to run -- not sure if that is still available for 12.04. I haven't seen any mention of it lately.

2. Your card is explicitly blacklisted by Unity. There used to be a way to force Unity 3D to ignore the blacklist via command line, but I'm sorry I don't remember the command offhand, and I'm not sure it still works for 12.04.

Thanks a lot for those tips; I will investigate and hopefully find the necessary info. I still find it strange that there is so little report about unity not running in 3-D with precise on this forum. The net outside is full of similar reports, and after all my Nvidia card works happily with Precise Gnome-shell.:confused:

---

### Post by Crempel on 2012-05-21
Well, apparently my not very new (and still not ancient) Nvidia card is blacklisted for Unity (but not the gnome-shell!)

Great stuff - since I have to use the shell, I might as well move to Fedora; after all they concentrate on it and I have already found out that it even works with nouveau.

Bye Unity!):P

---

### Post by bogan on 2012-05-21
Hi!, **Crempe**l,

The Unity test script is:```
 /usr/lib/nux/unity_support_test --print
``` Post the result here as it will also tell us which card you have and the driver version installed. { Which you have not mentioned}

Chao!, **bogan**.

---

### Post by Crempel on 2012-05-27
> **bogan said:**
> Hi!, **Crempe**l,

The Unity test script is:```
 /usr/lib/nux/unity_support_test --print
``` Post the result here as it will also tell us which card you have and the driver version installed. { Which you have not mentioned}

Chao!, **bogan**.

Hi bogan,
I'm sorry I did not read your message until today - I have indeed moved on to another distro (not Fedora, but Mint), and I now cannot execute the command you mentioned. I guess I was jsut too frustrated that until now I had not really gotten anywhere with my endeavors to make unity work with my graphics card...
It is quite amazing that this problem exists with unity and no other desktop, and no attempt has been made to fix it, almost 2 month after the release of precise.
I might reinstall Ubuntu and see what happens (and follow your suggestion).
Thanks again for your interest.

---

