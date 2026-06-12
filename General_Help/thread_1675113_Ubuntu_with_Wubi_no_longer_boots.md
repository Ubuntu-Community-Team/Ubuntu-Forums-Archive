---
title: "Ubuntu with Wubi no longer boots"
date: 2011-01-25
forum: General Help
---

### Post by an0maly321 on 2011-01-25
So up till this weekend my Ubuntu 10.10 maverick install with Wubi was working flawlessly and I was very happy with it and have been using it for a few months.  Today when I started up my laptop it gave me the familiar selection for Windows 7 or Ubuntu at system start.  When I selected Ubuntu instead of launching ubuntu it immediately dumped me straight into the grub command line.  Can anyone tell me what I need to do to correct my problem so that my ubuntu installation can boot again.  It took me forever to download and setup everything and it sucks for me to have to do it all over again.

I get the following error message right before i get dumped into the grub command prompt : 
```

Try (hd0,0) NTFS5: No wubildr
Try (hd0,1) NTFS5:

```

---

### Post by Rubi1200 on 2011-01-25
Hi and welcome to the forums :)

See here for Wubi issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you are still able to boot Windows normally, then you likely have problem #2 and can apply either solution #1 or #2.

Don't forget to apply the Permanent Fix once back in Ubuntu, including locking the grub-pc and grub-common packages.

---

