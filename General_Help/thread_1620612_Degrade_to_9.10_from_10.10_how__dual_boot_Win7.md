---
title: "Degrade to 9.10 from 10.10 how ? dual boot Win7"
date: 2010-11-13
forum: General Help
---

### Post by nacho32 on 2010-11-13
ok I have a dual boot win7 & Ubuntu 10.10 installed while being completely disappointed in the last 2 10.00 releases I want to overwrite the 10.10 to the 9.10 while still not touching the Windows 7 partition any suggestion?

---

### Post by psusi on 2010-11-13
Put in the installation cd and install 9.10.  But that's not a good idea since it will not be supported any more in about 5 months.

---

### Post by nacho32 on 2010-11-14
> **psusi said:**
> Put in the installation cd and install 9.10.  But that's not a good idea since it will not be supported any more in about 5 months.
it might not be supported in 5 months but in my oppion it is the most stable release to date, much snapper then any  10.00 release and it just works, installing it as we speak, I have it on my lap top and the desktop, oh and dump network manager and use Wicd manager instead much more stable and bug free just my 2 cents:popcorn: and your reply really gave me no input, but thanks any how

---

### Post by 73ckn797 on 2010-11-14
Did you have separate "/" and "/home" partitions for Ubuntu?

Open terminal and enter:
```
sudo blkid
```
Post the results.

---

### Post by nacho32 on 2010-11-14
> **73ckn797 said:**
> Did you have separate "/" and "/home" partitions for Ubuntu?

Open terminal and enter:
```
sudo blkid
```
Post the results.
no I have a TR-byte so I'n not hurting on space, I just did Quad boot Windows 7 - Ubuntu 9.10 Ubuntu 10.10 & LinixMint 10
but thanks for the reply:popcorn:

---

### Post by 73ckn797 on 2010-11-14
If you have a separate /home then just reinstall over the old Ubuntu "/" partition. You will still need to designate /home as the same partition but do not format.

---

