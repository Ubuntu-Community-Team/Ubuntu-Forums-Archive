---
title: "How to Install Printer filter Ubuntu Printer."
date: 2011-06-07
forum: General Help
---

### Post by lee.davis on 2011-06-07
I am new to Ubuntu and would very much appreciate someone's assistance in getting my printer to work in the Ubuntu O.S.:confused:

 I created the printer using CUPS after downloading the printer drivers from the URL:   [http://www.openprinting.org/driver/epson-workforce-840/](http://www.openprinting.org/driver/epson-workforce-840/)   extracting the .ppd file in my /home/ldavis/opt/ directory. When downloading the driver, OpenPrinting-Epson was inserted into the /opt/OpenPrinting-Epson/ppds/Epson directory and not in my /home/ldavis/opt/. Then I  enabled the printer to be published in the server settings in the  “Printing Manager” application located at  systems>administration>printing.
 

 The printer filter is located in my /home/ldavis/opt... directory and not in  the /opt/OpenPrinting-Epson/ppds/Epson directory where some of the .ppd.gz are located and  where the error message states it is looking for it. Do I need to  extract the .ppd.gz in the /opt/OpenPrinting-Epson/ppds/Epson directory and install  the filter in the same location? 

After trying several times in vain, I attempted to download and install the pinter drivers using the sudo -i apt-get install <> and apt-get upgrade < >. It installed some Epson printer drivers, but I still get an error message that the printer is looking for a printer filter to be installed. Can someone please tell me how to install a printer filter and which directory should it be installed in?
 
Please note that I do have three partitions: /, /home /swap


 Any assistance is truly appreciated! The assistance does not need to be complete even though it would very helpful. Therefore, any bits of information would be of great assistance to me, as I believe that I'm not too far away from resolving this issue especially with your assistance!!

:)
 

 Lee

---

### Post by IWantFroyo on 2011-06-07
Are you sure you needed the drivers? Ubuntu already has Epson support.

Good luck!

---

### Post by spesheled1 on 2011-06-07
First I think we need a little more information...

What kind of printer do you have? I'm assuming it is an Epson printer, but what model?

How are you connected to the printer? Parallel, USB, over your network, etc?

Ubuntu does come out of the box with plenty of printer drivers already installed, so you may or may not have needed to install a ppd.

---

### Post by lee.davis on 2011-06-08
Ubuntu has a tons of drivers available to them, but unfortunately, not for my Printer, or at least I did not locate it. My printer information is below...

Printer Type = Epson Workforce 840 connected to my network via wireless router where all other computers have access to and are able to connect and print from it. When using CUPS, I did not find the Epson Workforce 840. Many of the CUPS printer drivers were earlier models and one  was a latter model.

I appreciate everyone's quick response!

Thanks!

Lee

---

### Post by spesheled1 on 2011-06-13
I saw that the link you gave takes you to a page with links to download software packages. Since Ubuntu uses DEB packages you would download either the 32bit or 64bit depending on what kind of pc you have. You could then install the package using a package manager like Ubuntu Software Center or GDebi. Did you already download them and install the correct DEB package for your system?

---

### Post by elphaba on 2011-06-16
Wish someone would reply who has successfully installed.  I'm looking at this hardware - Epson Workforce 840 but don't want to buy unless I know it works with Ubuntu.  There is a review on Amazon where someone says this hardware is a difficult installation on a MAC - not good news for Ubuntu, IMO.

Here's an excerpt from that review (no guarantees this guy knows what he is talking about but certainly sounds interesting) -
"For Windows users, the Workforce 840 is a solid multifunction inkjet. The materials are too flimsy for sustained workgroup use, but it's definitely nice for a hone office user who likes the distinct look of Epson printing. For Mac users though, I can't really recommend this. The drivers aren't good at all, and you're going to lose functionality out of the box. "

---

