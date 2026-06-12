---
title: "HELP Brother MFC-440CN in 9.10"
date: 2010-01-03
forum: General Help
---

### Post by rogersab1223 on 2010-01-03
Hey everyone - 

Someone please help me install my Brother MFC-440CN.  I'm running 9.10.

I've downloaded the drivers from the brother website (the cupswrapper and cnlpr).  They don't work.  My printer is connected to my linksys and has the IP 192.168.1.107.  The printer configuration tool sees it.  However, I can't get it working.

I need a little guidance.

Thanks,
Andy

---

### Post by plucky on 2010-01-03
> **rogersab1223 said:**
> Hey everyone - 

Someone please help me install my Brother MFC-440CN.  I'm running 9.10.

I've downloaded the drivers from the brother website (the cupswrapper and cnlpr).  They don't work.  My printer is connected to my linksys and has the IP 192.168.1.107.  The printer configuration tool sees it.  However, I can't get it working.

I need a little guidance.

Thanks,
Andy

Use **Synaptic Package Manager** to install the two packages.Search for **MFC-440CN** and it should find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
``` select and install.Then see if it will find and install your printer.

If it doesn't,the instructions for network printer installation is on the Brother website where you downloaded the drivers from.


Good Luck

---

### Post by klarth.lester on 2010-01-03
Thanks for posting this. Oddly enough, I was in the same situation at the same time.
I couldn't make heads or tails of the Brother site, and so I downloaded everything for the 440CN. But the system was looking for a PPD file, and none of them were.

---

### Post by Jose Catre-Vandis on 2010-01-06
This might help

[http://ubuntuforums.org/showthread.php?t=1373928](http://ubuntuforums.org/showthread.php?t=1373928)

---

### Post by hesth on 2010-07-08
> **plucky said:**
> Use **Synaptic Package Manager** to install the two packages.Search for **MFC-440CN** and it should find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
``` select and install.Then see if it will find and install your printer.

If it doesn't,the instructions for network printer installation is on the Brother website where you downloaded the drivers from.


Good Luck

THANK YOU THANK YOU - I battle with this every time I do a fresh install. This is a great printer, but the cups driver seems to corrupt. I never looked in Synaptic before.

The only issue is that it doesn't align the print quite properly - chops off the top, but I can live with that.

Thankyou again!!!

---

### Post by perrjo on 2010-10-10
I was having the same trouble. This worked for me too. Thank you!

---

### Post by SDRED on 2011-07-06
My printer works but the scanning part of it doesn't work. It acts like it is scanning but then it doesn't copy it to any place on my computer. ANy suggestions?

---

### Post by plucky on 2011-07-06
> **SDRED said:**
> My printer works but the scanning part of it doesn't work. It acts like it is scanning but then it doesn't copy it to any place on my computer. ANy suggestions?

Have you installed the scanner driver?

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) and download your scanner driver .deb file and install.

Installations instructions are also provided on the website.

Good Luck

---

