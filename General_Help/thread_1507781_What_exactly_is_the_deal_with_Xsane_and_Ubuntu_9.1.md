---
title: "What exactly is the deal with Xsane and Ubuntu 9.10?"
date: 2010-06-12
forum: General Help
---

### Post by Objekt on 2010-06-12
Xsane in Ubuntu 9.10 is absolutely useless.  It simply crashes any time I try to do anything, so I can't even begin to try to scan anything with it.  I know the scanner part of my Brother MFC-7440N works, as I've used it with other software.

The Ubuntu community doc on Xsane is obsolete, not having been updated since last August.  I guess Xsane worked on earlier versions of Ubuntu, but it sure doesn't work in 9.10.

So, has anything been done about fixing Xsane?  The version in the Ubuntu 9.10 repository is 0.996, and I can't find any indication that a newer version is available in any form.  The Xsane homepage ([http://www.xsane.org/](http://www.xsane.org/)) apparently hasn't been updated since February 2009.

This is incredibly frustrating, as the only other scanning program I've found so far (Scanner Utility 0.6.2) is not very good.  I've had to resort to using the scanner on a virtual Windows XP machine through VirtualBox.  The Brother device came with a pretty decent scanning suite, PaperPort 11, which of course is Windows-only.

---

### Post by drpjkurian on 2010-06-12
Hi
I was also having a problem with xsane when I was in Karmic. I solved it by reinstalling xsane.

Meanwhile I also suggest skanlite and scanutility.
I am in Lucid now, Xsane worked without any glitch so far...

---

### Post by bobpress on 2010-06-12
I use xsane, however, I had to setup a specific profile for my printer/scanner since it is on a network.  Some alternatives I have seen in the Ubuntu Software Center are the KIPI Plugins (Acquire Image), Simple Scan, and gscan2pdf.  Don't know if any of these would be helpful, but you could install and try them.

---

### Post by Objekt on 2010-06-12
Thanks, skanlite and gscan2pdf were just what I was looking for!  I don't know why I couldn't find them previously.

---

