---
title: "Samsung SCX-5530FN (Using PPD File)"
date: 2010-03-06
forum: General Help
---

### Post by tamran on 2010-03-06
I actually had no trouble making this printer work as a "generic printer" and searching the network found it with no problems.  However, this printer has some nice features and Samsung does supply a PPD (PostScript Printer Description) file on the cdrom.

I was able to use this PPD file but requires "rastertosamsungspl" to be installed.  After some searching, I found this article (it's for another printer but the motions are similar):

[http://wiki.archlinux.org/index.php/Samsung_ML-2245](http://wiki.archlinux.org/index.php/Samsung_ML-2245)

So, if you use the PPD file and it complains that rastertosamsungspl is not installed, you can do the following:

```

# cp /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter/rastertosamsungspl /usr/lib/cups/filter/

```

I was not able to make the install script work at all and would very much appreciate if anyone has any pointers on this, because the CD contains some applets for network monitoring and scanning that would be useful.

I hope this helps others if possible.

Tamran

---

### Post by epiphanius on 2010-07-21
Thanks for posting this, Tamran. Most helpful.

---

