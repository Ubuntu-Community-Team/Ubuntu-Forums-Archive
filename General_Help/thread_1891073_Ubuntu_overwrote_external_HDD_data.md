---
title: "Ubuntu overwrote external HDD data"
date: 2011-12-04
forum: General Help
---

### Post by Call My Function on 2011-12-04
I encrypted a *partition* on an external drive in Windows with Truecrypt and switched to Ubuntu to test for any issues and, well, I found one.

After selecting Ubuntu on the Grub menu and seeing the "loading from (hd0,4)" or whatever that says, I saw some *more* text that I had never seen before when loading Ubuntu. Unfortunately, I didn't write down what it was and I can't find any system log where it might've been recorded. However, I DID know it was referring to my external.

After entering Ubuntu and starting up Truecrypt, it told me it couldn't open the encrypted drive because it wasn't a proper encrypted volume. I restored the header with a backup and was able to enter my password, but once mounted I found the filesystem was Raw. My guess is the data was overwritten during boot, which took out the encryption header and filesystem.

Nothing on the drive was important -- I was testing after all. But I want to know what happened before I trust my important bits to an encrypted drive.

I tried to reproduce the problem by reformatting the drive and encrypting both a partition AND the entire drive (partition and all), but it hasn't occured again.

Does anyone know what might've happened? Is there *ever* a case when Ubuntu would write to an external drive while booting?

---

### Post by Call My Function on 2011-12-12
Bumping. This is a serious issue. I don't want to lose encrypted data in the future! :(

A detail I want to add is that I *believe* the strange command I saw included "dd", but since I didn't write it down I can't be sure. I've tried to look up information on the dd command, but nothing helped me with this issue.

---

