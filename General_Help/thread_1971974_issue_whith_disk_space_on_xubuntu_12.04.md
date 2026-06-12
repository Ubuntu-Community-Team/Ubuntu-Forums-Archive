---
title: "issue whith disk space on xubuntu 12.04"
date: 2012-05-03
forum: General Help
---

### Post by typhoon71 on 2012-05-03
I get a strange issue on presise, xubuntu variant. It didn't happen with Maverick, the distro I used before.

If I check disk space (via thuna) I get inconsistents values, like:

used space 26GB, free spade 12GB, on a 32GB ext3 partition (the root partition)

if I df, the free space remains the same as in thunar, but the used space goes down to the "right" "expected" value, 20GB. But if I check some directories where I have big files (a total of 18GB), I start to panic (the OS isn't just 2GB right?

The partition is not the full HDD size, it's just a temp setting to try out the OS, and see how it works for me, but reporting free space where there is not is bad.

*** Something must be really wrong here, I created a 96GB partition, and after mounting it it is just 89,5GB... I'd really appreciate some help here... Thanks


I checked the HDD, partitions etc just in case, all is ok, but still I can't get a proper report of used and free space.

Can someone help me there? Thanks a lot.

---

### Post by typhoon71 on 2012-05-12
Can someone help here? I think it's a serious matter but after a week nothing isn't exactly the kind of feedback I expected on something like this...

---

### Post by Gyokuro on 2012-05-12
Hi

Could you please post your df -h output?

---

### Post by typhoon71 on 2012-05-12
df -h output in the attachment, couldn't paste it right. :P
Thanks for answering.

---

### Post by Gyokuro on 2012-05-12
Looks fine and your assumption that the OS is using more as 2GB is correct as a short glance via

du -sh lib usr 

shows 2.4G on my ubuntu amd64 12.4 system (some dirs excluded) 

and 5% disk space get reserved for root + format overhead + swap space  + chunck in /var and you have your missing space (if I have not missed anything).

---

### Post by typhoon71 on 2012-05-12
oh, df output may be coherent with itself, but not with the system; free space on sda4 is reported as 89,5BG by thunar, for example, and is still wrong on df, where it shows 90GB free on a empty partition of 96GB total size, with just 188MB used, which is wrong. 

I'll try xfce 4.10 out to see if it's the same thing or not.

---

### Post by estefano on 2012-07-02
I have a similar problem: xubuntu 12.04

I have a fresh empty 200 Gb partition ext4 and df shows 3G used!!!

Thanks in advance for help

---

### Post by estefano on 2012-07-02
by the way, I tried to use the coomand

tune2fs -m 0 /dev/sda7

but nothing changed, still 3Gb of disk space disappeared

---

