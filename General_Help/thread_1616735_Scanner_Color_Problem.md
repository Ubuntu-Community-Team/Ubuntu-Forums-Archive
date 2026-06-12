---
title: "Scanner Color Problem"
date: 2010-11-08
forum: General Help
---

### Post by 45678912 on 2010-11-08
Hello,

I have the **scanner** **HP Scanjet 2400** installed on a machine with **K/Ubuntu 10.10** and I use the software **Simple Scan** to scan image.

**Problem: **The image scanned by this scanner comes with a inversion of colors (**what was supposed to be orange is blue ; the white sheet of paper that I've put inside it was not in the blank color when I scanned it too**)...

**My Question:** Is this a configuration problem (I did not configured this scanner at any way, so it's working by the Ubuntu drivers itself without my intervention)? Is there any way to solve it?

Thanks for your attention,

André M.

---

### Post by lazyest on 2010-11-22
> **45678912 said:**
> Hello,

I have the **scanner** **HP Scanjet 2400** installed on a machine with **K/Ubuntu 10.10** and I use the software **Simple Scan** to scan image.

**Problem: **The image scanned by this scanner comes with a inversion of colors (**what was supposed to be orange is blue ; the white sheet of paper that I've put inside it was not in the blank color when I scanned it too**)...

**My Question:** Is this a configuration problem (I did not configured this scanner at any way, so it's working by the Ubuntu drivers itself without my intervention)? Is there any way to solve it?



Tha same scanner, the same thing. In previvous Ubuntu versions since 8.10 scaner works with some additional steps but in 10.10 it seems to be supported except the color issue.

---

### Post by 45678912 on 2010-11-22
Hello lazyest,  So, is this a driver problem?  PS: I searched SANE project and they say this scanner was not tested by them... So I reported a bug...  PS²: I tested it in my (K)Ubuntu 10.10 with Simple Scan ; XScan ; Skanline and VueScan  Thanks for your attention,  André M.

---

### Post by ArtedeMagia.com on 2011-09-19
I had the same issue with a HP Scanjet G2410.
  

My solution may work for you:
  Download this file: [http://rapidshare.com/#!download|209l33|117078532|HP_Scanjet_2400.zip|6361]("http://rapidshare.com/#%21download%7C209l33%7C117078532%7CHP_Scanjet_2400.zip%7C6361")  This is a driver for the HP Scanjet 2400, but it worked for my scanner, it's even more possible that it works for yours.
  

(You may need to install sane first) Unzip it and follow the instructions in the README_hp2400.txt file.
  

Those instructions worked perfectly for me.
  

I got that file link from a comment in this blog: [http://racoon97.blogspot.com/2009/04/install-hp-scanjet-g2410-scanner-on.html](http://racoon97.blogspot.com/2009/04/install-hp-scanjet-g2410-scanner-on.html)
  

The original link is broken, and almost all blogs and forums where I  looked for info linked that broken file, so this rapidshare file was the  only one that I could download.
  

The instructions in that blog (and the other blogs) are almost the  same, and are almost the same than those in the readme file. I installed  sane and followed the readme file instructions, and that is what worked  for me.

---

### Post by 45678912 on 2011-09-23
Hello ArtedeMagia.com, 

Thanks for your answer... I've reported this issue to the SANE team and  they have created a driver for the HP Scanjet 2400c scanner that have  solved the issue... In anyway, thanks for your answer... 

The report is:  [https://git.debian.org/tracker/?func=detail&atid=410366&aid=312816&group_id=30186](https://git.debian.org/tracker/?func=detail&atid=410366&aid=312816&group_id=30186)

Best regards, 

-- 
André Madureira

---

