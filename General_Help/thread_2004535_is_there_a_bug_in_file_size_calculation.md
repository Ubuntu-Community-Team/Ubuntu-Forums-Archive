---
title: "is there a bug in file size calculation"
date: 2012-06-16
forum: General Help
---

### Post by reptilezone2002 on 2012-06-16
i have noticed this in 11.10 the file size shows in ubuntu is wrong i have downloaded ubuntu iso from the main site the file size is 701mb is it but after ive downloaded the file the size is 732mn (iso file) and ive downloaded other files just ckeck all r the same live cd images r over 725mb and the real file size i get in the sistem is when im using brasario too burn the cds .. this happens to all the files .. all displays the wrong size ill include a picture so u can get an idea of what im saying .. does anyone else have the same prob .. do i need to file a bug on this .. its annoying this .. 

plz note the file size at the status bar ....(in the images )

---

### Post by GWBouge on 2012-06-16
If I had to guess, I'd say you've stumbled onto the kilo=1024 vs kilo=1000 thing ... some say that when it comes to computers, kilo is 2^10 = 1024, others calculate it as 10^3.  Nautilus now seems to use 10^3.

I just went to download the Ubuntu 12.04 64-bit ISO, Firefox tells me 698MB, while Nautilus says 732MB.  Either way, it's still the same amount of bytes.

698 * (1024 * 1024) / (1000 * 1000) = ~732

It's not just Ubuntu, either ... I've attached a picture which shows 3 different ways of checking disk usage in OSX 10.7, each one showing a different size in GB.

---

### Post by dcstar on 2012-06-16
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/875224](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/875224)

My 10.04 Nautilus says "MB" but actually displays sizes in MiB". According to the bug report the newer Nautilus versions now correctly use the old "MB" calculation - probably because people were confused by the previous situation.

---

### Post by reptilezone2002 on 2012-06-16
> **dcstar said:**
> [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/875224](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/875224)

My 10.04 Nautilus says "MB" but actually displays sizes in MiB". According to the bug report the newer Nautilus versions now correctly use the old "MB" calculation - probably because people were confused by the previous situation.

well im using 12.04 & just updated nautilus by update manager still it says wrong size ... it says in the bug report that they fixed it in the new release i think its .3.4 is it.. but still the thing is there .. its a translation pack issue or something i dont know all i know is its annoying.. well i have wasted a dvd coz of this issue i could burned it to a cd easily but the file size says 730MB so i burned it in to a dvd that i could sue in another thing

---

