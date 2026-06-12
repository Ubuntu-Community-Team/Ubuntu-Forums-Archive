---
title: "Virus Scanning Assistance Needed!"
date: 2010-07-06
forum: General Help
---

### Post by CrazyOldMaurice on 2010-07-06
Hi,

I'm attempting to remove a virus from my Windows PC using Ubuntu, however I'm not exactly sure how to go about it, for I am a brand-new linux user. If anyone could help a total noob like me run an effective virus scan so I could get rid of this thing, that would be awesome beyond belief. Seriously.

---

### Post by Skyhighnemo on 2010-07-06
Try avast.com   They have a linux home free version.  I have used Avast before.  It is easy to use and free and works well.  They also have a free windows version too.

Sky

---

### Post by CrazyOldMaurice on 2010-07-06
I found it on the site, but how the heck do I install/run it?

---

### Post by Rubi1200 on 2010-07-06
In my opinion, the better method is to run a so-called rescue CD.

Here is a link:

[http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/](http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/)

---

### Post by lisati on 2010-07-06
> **Rubi1200 said:**
> In my opinion, the better method is to run a so-called rescue CD.

Here is a link:

[http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/](http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/)

AVG also have a free Linux-based rescue cd: [http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

### Post by piju on 2010-07-06
why dont give a try to clamav ?

just open ubuntu software center, and search for clamav

---

### Post by carlexpc on 2010-07-06
If you could still boot your Windows pc, boot in safemode with networking. Disable System Restore and run an on-line scanner like NOD32.

After that, back-up your files and I suggest you switch to Linux to get rid of the virus headaches Windows is giving you.

---

### Post by Firedrake445 on 2010-07-06
Much like piju's suggestion, I'd suggest you boot a live cd and install a package called clamtk and then run it as root, update it and then run a total scan. This will be much more effective IMHO

---

### Post by carlexpc on 2010-07-06
> **Firedrake445 said:**
> Much like piju's suggestion, I'd suggest you boot a live cd and install a package called clamtk and then run it as root, update it and then run a total scan. This will be much more effective IMHO

The virus problem will return even if he gets it removed using Ubuntu. Remember that Windows has this System Restore feature that returns the OS in its most recent state (with the virus active).

---

### Post by HermanAB on 2010-07-07
Hmm, the best way to fix Windows, is with Windows.  Google for BartPE, a live Windows CD, then make a WinXP CD with all the required junk removal tools on it.

---

### Post by carlexpc on 2010-07-07
> **HermanAB said:**
> Hmm, the best way to fix Windows, is with Windows.  Google for BartPE, a live Windows CD, then make a WinXP CD with all the required junk removal tools on it.

I agree to that. Cheers!

---

### Post by bodhi.zazen on 2010-07-07
> **HermanAB said:**
> Hmm, the best way to fix Windows, is with Windows.  Google for BartPE, a live Windows CD, then make a WinXP CD with all the required junk removal tools on it.

This, and you need to first identify and then google search for information on the virus or work or whatever. Many of these things require editing the windows registry.

You should be looking at something like this:

[http://www.bleepingcomputer.com/tutorials/tutorial101.html](http://www.bleepingcomputer.com/tutorials/tutorial101.html)

---

### Post by CrazyOldMaurice on 2010-07-07
Thanks everyone!

I used that last link, and ran Malwarebytes' Anti-Malware, found that the virus was caused by Antivirus Suite, and then used this guide to restore my internet access-
[http://www.malwarehelp.org/antivirus-suite-removal-2010.html](http://www.malwarehelp.org/antivirus-suite-removal-2010.html)

XD

---

