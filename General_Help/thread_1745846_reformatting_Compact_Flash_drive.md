---
title: "reformatting Compact Flash drive"
date: 2011-05-01
forum: General Help
---

### Post by engine on 2011-05-01
I've managed to corrupt a 1Gb Compact Flash card and can no longer write to it. I've backed up all the retrievable files, and now I'm hoping I can simply reformat the card, copy the files back and carry on as before &#8210; except more carefully!

What's the best command to use? I was hoping "format" might be a right-mouse option, but no such luck.

Thanks in advance!

---

### Post by engine on 2011-05-30
bump … c'mon, Compact Flash may not be the most up-to-date storage option, but part of the charm/value of Ubuntu is that we don't have to rush out and buy the latest/biggest/fastest every week!

I've found the suggestions

```
mkfs
```

and
```
if your disk has not been partitioned, you should partition it first, using the command fdisk /dev/sdX
```

So far so good? but mkfs has about 20 options I don't understand, and I don't know how to refer to the CF card as a dev/ entry: Nautilus helpfully identifies it as media/

**Questions**

[LIST=1]
[*]how do I use fdisk /dev/… to show partitions on the CF card?
[*]what fdisk options should I use to partition the CF card once I've located it
[*]what mkfs options should I use to format the CF card once I've partitioned it
[/LIST]

Thanks in advance!

---

