---
title: "How do I downgrade to 8.04?"
date: 2010-01-05
forum: General Help
---

### Post by Knuffle on 2010-01-05
I recently installed updates for my laptop (its very old) and upgraded it form Ubuntu 8.04 to 9.10. This has caused a major decrease in permormance and I was wondering if there is any way of removing these upgrades. Thanks for the help.

---

### Post by Cheesemill on 2010-01-05
I'm afraid not. The only way of getting back to 8.04 is a clean install.

---

### Post by howefield on 2010-01-05
You are looking at backing up your data, and a clean install.

---

### Post by Knuffle on 2010-01-05
Thanks. Thats unfortunate.

---

### Post by Leppie on 2010-01-05
there's a downgrade guide: [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

but it's for 8.10 to 8.04
remember to uninstall any 3rd party drivers first.

if you have a separate /home partition, a fresh install may be easier ;)
and if you don't have a separate /home partition, now may be a good moment to start using one...

---

### Post by dcstar on 2010-01-06
> **Knuffle said:**
> I recently installed updates for my laptop (its very old) and upgraded it form Ubuntu 8.04 to 9.10. This has caused a major decrease in permormance and I was wondering if there is any way of removing these upgrades. Thanks for the help.

Doing an "upgrade" is always problematical, a fresh 9.10 install may well provide better performance.

As mentioned previously, use a separate /home partition and you can install 9.10 (or anything) without affecting your user data.

---

### Post by 3rdalbum on 2010-01-06
> **Knuffle said:**
> I recently installed updates for my laptop (its very old) and upgraded it form Ubuntu 8.04 to 9.10. This has caused a major decrease in permormance

Before going to those sort of lengths, have you tried just checking your System Monitor to find out what's using all your CPU power and then killing the program? There normally should be *minimal* performance difference between versions of Ubuntu.

---

