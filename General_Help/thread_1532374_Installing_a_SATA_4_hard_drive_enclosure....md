---
title: "Installing a SATA 4 hard drive enclosure..."
date: 2010-07-16
forum: General Help
---

### Post by PrvSAT on 2010-07-16
Hello,

INFO: I have installed 10.04 on a PC that I wish to make it a HTPC. 
MB: Asus P5G43T-M PRO
CPU: Intel Dual Core @ 3Ghz
DDR3 2GB

PROBLEM: I have a 4X bay enclosure for hard drives with USB and eSATA interface and it has a JMicron bridge chipset: JMB321. Currently there are three hard drives installed in this enclosure. When I connect it via USB it is working perfectly, all hard drives are recognized and you can read and write.
When I connect it via eSATA is the problem. If I pull two hard drives out, it is working fine, the drive is recognized but when are all three plugged does not work. It shows a continuous hard drive activity for two drives and there is none recognized.
When I plug this enclosure in MAC or Windows PC, it is working fine. It seems to me that I need a SATA driver or something. Could anyone help me, please?

The enclosure: ```
http://mediasonicinc.com/store/product_info.php?cPath=26_51&products_id=150
```

I see on the product page the following message:
 **[FONT=arial,helvetica,sans-serif][SIZE=2]Important Note:  [/SIZE][/FONT]****[FONT=arial,helvetica,sans-serif][SIZE=2]When connecting via eSATA interface, customer's computer  hardware needs to have [COLOR=#ff0000]Port Multiplier w/  FIS-based switching[/COLOR] in order to access multiple HDDs  simultaneously.[/SIZE][/FONT]**  
It seems that Both Windoze and OsX have this feature or driver but not Ubuntu. Please help.

---

### Post by PrvSAT on 2010-07-18
Could anyone hep please? [-o<

---

### Post by PrvSAT on 2010-07-27
I reply to myself now.

I have purchased a PCI tp SATA port with one eSATA and two SATA ports. I have tried it on a windows computer and when I connect by 4 drive enclosure, it works fine.

So with some hope, I connected to my uBuntu 10.04 HTPC and again it is not recognized.
I noticed that when I leave installed only one drive in the enclosure, it is recognized but not with more than one. Is this a missing driver issue in ubuntu or is it a bug? How should I proceed further?

---

### Post by kpuz on 2010-12-23
[http://www.linux-usb.org/FAQ.html#ts9](http://www.linux-usb.org/FAQ.html#ts9)
This question seems similar to what you have described but it seems to be about a usb connection not detecting all drives. Regardless, it may help you in researching your problem.

---

