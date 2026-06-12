---
title: "I cannot burn ISO's to CD+RW"
date: 2010-12-22
forum: General Help
---

### Post by OldTimeyJunk on 2010-12-22
I've tried numerous times and different ISO's but I cannot seem to burn ISO's to CD+RW. I'm using Braseo CD Burner.
All it does is make the disc have 0 bytes remaining and it acts as if it is a CD-R/CD+R
Whats happening?

---

### Post by 3Miro on 2010-12-22
Can you burn other disks and have you tried other iso files or general data burn.

I had a burner once that refused to work with 9.10 and 10.04, but it was fine with 10.10. There may be a driver issue.

---

### Post by OldTimeyJunk on 2010-12-22
It's a Windows 7 ISO I took off a disc, it works fine in VirtualBox but when I mount the disc it only has a Readme file in it

---

### Post by Slim Odds on 2010-12-22
Did you erase/blank the disk before you tried to burn it?

---

### Post by OldTimeyJunk on 2010-12-22
It's totally brand new. Nothing has ever been wiped or put on the disc. I tried loads of disc's and I've now wasted 4.

---

### Post by Slim Odds on 2010-12-22
> **OldTimeyJunk said:**
> It's totally brand new. Nothing has ever been wiped or put on the disc. I tried loads of disc's and I've now wasted 4.

How do you "waste" a RE-WRITABLE disk?

You can erase and reuse them!

---

### Post by OldTimeyJunk on 2010-12-22
No, after I burn it acts as a CD-R, pretty strange

---

### Post by Slim Odds on 2010-12-22
> **OldTimeyJunk said:**
> No, after I burn it acts as a CD-R, pretty strange

What happens when you try to erase it?

Have you tried it in another drive?

---

### Post by OldTimeyJunk on 2010-12-22
Erase is blanked out.
I'm starting to think the discs are broken. I've booted up Win7 into Virtualbox and tried some discs and all of them don't work.

---

### Post by pdiddypaul on 2010-12-22
Just shooting from the hip here, as I am not on my main machine. But I think that a Windows 7 iso would require a DVD to burn the iso.

---

### Post by Slim Odds on 2010-12-22
> **pdiddypaul said:**
> Just shooting from the hip here, as I am not on my main machine. But I think that a Windows 7 iso would require a DVD to burn the iso.

Excellent point, the burning software should warn about that.

---

### Post by philinux on 2010-12-22
> **OldTimeyJunk said:**
> Erase is blanked out.
I'm starting to think the discs are broken. I've booted up Win7 into Virtualbox and tried some discs and all of them don't work.

Put the disk in and then open a terminal. Use copy and paste.

```
umount /dev/cdrw
```

Then

```
cdrecord blank=fast dev=/dev/cdrw
```

---

### Post by Spyderkid on 2010-12-22
sounds like the disks are broken. Can you CD drive write to CD's or is it just a reader?

---

### Post by 3Miro on 2010-12-22
It is possible that the .iso requires a non-rewritable DVD to burn. Rewritable ones are tricky sometimes and may disagree with copy protection on the MS disk.

---

### Post by OldTimeyJunk on 2010-12-23
I did read somewhere thats why I was a little reluctant to buy them. I really wish I hadn't.
But I have tried numerous ISO's.
I had Fedora 14 (which is absolute bulls***) and burned a Linux Mint ISO onto it and it did the same thing.
Do you know if there is any way of installing Windows 7 onto an actual HDD from Virtualbox?

---

### Post by OldTimeyJunk on 2010-12-23
> **philinux said:**
> Put the disk in and then open a terminal. Use copy and paste.

```
umount /dev/cdrw
```Then

```
cdrecord blank=fast dev=/dev/cdrw
```

Nothing has happened...
"Cannot blank disk"
I've also tried WoDim and it says the same thing.

---

### Post by psusi on 2010-12-23
> **3Miro said:**
> It is possible that the .iso requires a non-rewritable DVD to burn. Rewritable ones are tricky sometimes and may disagree with copy protection on the MS disk.

There is no such thing as copy protection in an iso image.

Are you sure that the discs started off as being identified as cd-rw?  ( There is no such thing as cd+rw btw ).  If you put a fresh one in can you blank it?  And as someone else mentioned, the win7 iso should be far too big to fit on a cd.

---

