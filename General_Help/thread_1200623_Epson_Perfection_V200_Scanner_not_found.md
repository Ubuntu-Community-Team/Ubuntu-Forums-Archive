---
title: "Epson Perfection V200 Scanner not found?"
date: 2009-06-30
forum: General Help
---

### Post by CrusaderAD on 2009-06-30
I have a Epson Perfection V200 Scanner and every program I try to use to scan, it says scanner not found. Any ideas?

---

### Post by Tamlynmac on 2009-06-30
You may wish to try the driver listed here [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
with the instructions listed here: [http://uellue.de/blog/single.php?date=1192278660](http://uellue.de/blog/single.php?date=1192278660)

I don't have any experience with either one, but apparently this driver is from the Japanese Vendor site. As always I suggest you read the documentation closely and note any and all files installed, in case of the need to uninstall. Plus any other changes that may be required to alter as needed.

Good Luck and hope this helps.

---

### Post by ManiacDan on 2009-06-30
Did you try installing the scanner?

---

### Post by CrusaderAD on 2009-06-30
> **ManiacDan said:**
> Did you try installing the scanner?

How do you install it? I installed the drivers.

---

### Post by CrusaderAD on 2009-06-30
I just tried vuescan... nothing sees this dumb scanner.

---

### Post by CrusaderAD on 2009-06-30
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do) 

the plugin worked like a charm. Thanks for the replies.

---

### Post by wsscott on 2009-11-01
The scanner worked immediately for me also after installing the two files for Ubuntu 8.10 or later.

Thanks!

---

### Post by CrusaderAD on 2009-11-06
Here's the files in case anyone needs them.

---

### Post by mawebb on 2009-11-08
> **raptormanad said:**
> Here's the files in case anyone needs them.

@raptormana

I installed all 3 deb's on my Ubuntu Netbook Remix 9.10 but neither Xsane or Image Scan work with my Epson Perfection V200 PHOTO. Its listed in lsusb ok and Xane also can see it (it gives me the option of the scanner or built in web cam) but fails after this. Is there something else I am missing?

Rgds

---

### Post by mawebb on 2009-11-09
> **mawebb said:**
> @raptormana

I installed all 3 deb's on my Ubuntu Netbook Remix 9.10 but neither Xsane or Image Scan work with my Epson Perfection V200 PHOTO. Its listed in lsusb ok and Xsane also can see it (it gives me the option of the scanner or built in web cam) but fails after this. Is there something else I am missing?

Rgds

Well solved it myself. I visited the manufactures site at [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do) and downloaded the newer

iscan_2.22.1-2.ltdl7_i386.deb

and the same iscan-plugin-gt-f670_2.1.0-3_i386.deb again. Installed both and now Image Scan and Xsane both work.

Might now try these in Puppy as well.

---

### Post by CrusaderAD on 2009-11-09
Glad to see you got it working. I haven't used the netbook remix yet, but it's good to know. Thanks for posting your resolution.

---

### Post by mawebb on 2009-11-09
@raptormanad

Is libbltdl3_1.5.26-1ubuntu1_i386.deb really required as you have listed above? I installed it but on the vendors site there are only two files mentioned so maybe I can take it out?

---

### Post by CrusaderAD on 2009-11-09
I'm not 100% sure on that. I know I have all 3 newly installed on a fresh copy of 9.10 Ubuntu. Works great, that's when I stop asking questions :) I guess you could take it out and see if it still works. You can always add it again.

---

### Post by jacktar on 2009-11-09
I also have UNR 9.10 and I have installed the three debs but it still cant find the scanner, only the webcam. I have had it working for a long time on my desktop running 8.04.

---

### Post by CrusaderAD on 2009-11-09
I don't know why it works this way, and I know you're not supposed to do this, but run image scan with sudo priviledges... it doesn't work for me unless I do that.

---

### Post by mawebb on 2009-11-10
> **jacktar said:**
> I also have UNR 9.10 and I have installed the three debs but it still cant find the scanner, only the webcam. I have had it working for a long time on my desktop running 8.04.

Did you used the newer iscan_2.22.1-2.ltdl7_i386.deb I mentioned in my earlier post? That was the trick for me.

---

### Post by jacktar on 2009-11-10
Yes I used that deb. It does not work with sudo either.

---

### Post by CrusaderAD on 2009-11-10
They must do something different in the netbook remix when it comes to the printing applications. Anyone know what this could be? Maybe something with the CUPs software?

---

### Post by herdivet on 2009-11-14
Great information - and finally this Epson works with Ubuntu 64bit!  That's great news.

I had a problem with needing to use sudo, but after a reboot, that problem disappeared.  I'm not sure why.

---

