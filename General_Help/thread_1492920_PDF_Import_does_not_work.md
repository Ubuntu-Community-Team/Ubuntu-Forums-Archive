---
title: "PDF Import does not work"
date: 2010-05-25
forum: General Help
---

### Post by labinnsw on 2010-05-25
The situations are:
Where Sun PDF Import extension is downloaded using the Extension manager on 64 bit Lucid.
1. After installation, any attempt to open a pdf file results in OpenOffice freezing.
2. After restarting OpenOffice Sun PDF Import extension is disabled with the error: The status of this extension is unknown.
or
Where Sun PDF Import extension is installed from the repositories. Any attempt to open a pdf file has no result. (Nothing seems to happen)
But
Where Sun PDF Import extension is installed both from the extension manager and the repositories, simple pdf files will open.
N.B. I use "simple" and "complex" to differentiate between PDF files that OpenOffice can and cannot handle.

While everything seems to work, one problem remains. The Sun PDF Import extension installed via the extension manager still has the error message. Not a biggie, but if it can be fixed, I would love to fix it.

---

### Post by PGScooter on 2010-06-07
what versions of everything are you working with (always try to post this information) ?

I'm on Ubuntu 10.04 64-bit and I downloaded the plugin from here
[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

and everything has been working great.

Good luck! You could always try removing openoffice completely then installing it again and trying again.

---

### Post by labinnsw on 2010-06-08
> **PGScooter said:**
> what versions of everything are you working with (always try to post this information) ?

I have been planning to save this information in a file ready for posting when needed.

CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
Motherboard: ASUS P5K SE
OS: Ubuntu Lucid Lynx 64 bit (ubuntu-10.04-desktop-amd64)
File System: Ext 4
Kernel Linux 2.6.32-22-generic
Desktop: GNOME 2.30.0
OpenOffice.org 3.2.0 [OOO320M12 (Build:9483) from Synaptic] 
Extension: Sun PDF Import Extension 1.00 (from Synaptic)
Extension: Sun PDF Import Extension 1.0.1 (from [http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport))

> **PGScooter said:**
> I'm on Ubuntu 10.04 64-bit and I downloaded the plugin from here
[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

and everything has been working great.No one is happier for you than I am.

> **PGScooter said:**
> Good luck! You could always try removing openoffice completely then installing it again and trying again. That is one of the first things I did. I also did that with both versions of PDF import, including deleting the files in my home directory.

As I have said, this is not a major issue. If a fix is found, great! If not, it never gets in the way.

---

### Post by PGScooter on 2010-06-08
> **labinnsw said:**
> I have been planning to save this information in a file ready for posting when needed.

That's a good idea. I will do the same.


I wish I had more ideas. Sorry, and good luck.

---

### Post by rodney.cabahug on 2010-06-22
hi! how did you solve this problem? anyways, i was able to install the plugin using the one from the repo.. and, all is well.

```
sudo apt-get install openoffice.org-pdfimport
```

---

### Post by labinnsw on 2010-06-23
Question.> **rodney.cabahug said:**
> hi! How did you solve this problem? 


Answer. > **labinnsw said:**
> where sun pdf import extension is installed both from the extension manager and the repositories, simple pdf files will open.

---

