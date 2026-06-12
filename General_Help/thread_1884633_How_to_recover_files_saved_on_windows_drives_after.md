---
title: "How to recover files saved on windows drives after installing ubuntu 11.10 many times"
date: 2011-11-21
forum: General Help
---

### Post by dennipambudi on 2011-11-21
A month ago, my desktop PC was installed Windows 7. A few weeks later, i installed ubuntu 11.10 twice and before i installed, i choose replace windows 7 with ubuntu 11.10. And it happened twice. But, my brother ask me to recover his data seved in Windows 7. How can I recover all those data? Please, explain in detail. Thanks.

---

### Post by Mark Phelps on 2011-11-21
First of all, it will likely be impossible to recover ALL the data.

Why? Because when you reformatted, you made all the space in the new partitions available for reuse -- and most certainly, some of that space got overwritten.  The more you used the PC, the more space got overwritten.

That overwritten space can not be recovered back to the original contents.

If you want to try out recovering the former Windows contents, then read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

