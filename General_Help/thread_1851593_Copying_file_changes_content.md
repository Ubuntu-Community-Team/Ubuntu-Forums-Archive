---
title: "Copying file changes content"
date: 2011-09-28
forum: General Help
---

### Post by krille.e on 2011-09-28
When I copy a file on my computer the content of that file sometimes changes.

I have a system running ubuntu server 
Ubuntu 9.10
2.6.31-16-generic-pae

I have noticed a lot of data corruption in subversion repositories on this server. I did a small experiment 

1. Created a file test.tar.bz
2. Calculated sha1sum ade70e0e5f579c63e3b238b733a034714f33338a
3. Copied file to test.tar.bz.copy
4. Calculate sha1sum of copy. 

Doing this about 4000 times I mostly get the same sha1sum as the original file but in about 0.8 % of the cases I get a sha1sum different from the original.

Some examples.
018378895b97c56a75d5a1807bf723f428d5d273  test.tar.bz.copy
148a630558ca4d69822757ac4214ce9633f28c45  test.tar.bz.copy
3448ac3ff5be0b06758fb7d6d8482479979242e9  test.tar.bz.copy
8a25f27588f9c937161951f562a91825045d6220  test.tar.bz.copy
ade70e0e5f579c63e3b238b733a034714f33338a  test.tar.bz
ade70e0e5f579c63e3b238b733a034714f33338a  test.tar.bz.copy
da2b5eb02560941b8c2373484073f45ab97b125b  test.tar.bz.copy

I have tried this on one raid array but also on a spare disk mounted in the computer I also did a test on a ramdisk with the same result.

Does anyone have any clue on what is going on?

I have started backup info from the server and it seems that using rsync to download also corrupts the data. I have downloaded two copies of things and get differences between the two copies.

---

