---
title: "Install Brother MFC6490CW printer"
date: 2010-10-24
forum: General Help
---

### Post by rogerb1583 on 2010-10-24
I have tried everything I can think of to make this printer run with Ubuntu 10.10. I have downloaded and installed all of the software or at least I think I have but the printer does not show up on the list of printers in the dialog box to be selected. I have tried terminal install but hit a snag. (Yes I am a relative newbie to this.) :) I installed the printer definition software via Ubuntu Software Center. It will find the printer on the network but will not connect and print.

---

### Post by nevius on 2010-10-24
> **rogerb1583 said:**
> I have tried everything I can think of to make this printer run with Ubuntu 10.10. I have downloaded and installed all of the software or at least I think I have but the printer does not show up on the list of printers in the dialog box to be selected. I have tried terminal install but hit a snag. (Yes I am a relative newbie to this.) :) I installed the printer definition software via Ubuntu Software Center. It will find the printer on the network but will not connect and print.

Try installing the lpr and cups drivers here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6490CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6490CW)

Download the .deb files for your printer and double-click on them. I have a brother HL-2040. Part of the cups installation process tries to put a .ppd in /usr/share/cups/model. This folder does not exist in a normal Ubuntu install. You will probably have to ```
sudo mkdir /usr/share/cups/model
``` before running the cups driver installer.

Once this is done, you should be able to add the printer through System->Administration->Printing

---

### Post by rogerb1583 on 2010-10-24
Not having any luck yet. Tried Terminal install and I must be doing something wrong. :confused: Trying to connect via network. Is it absolutely necessary to be connected to the printer via cable? 

Thanks in advance for your help. Spent a lot of time on this with not results. Maybe I should dig out an old HP printer and use it.  ](*,)

---

### Post by rogerb1583 on 2010-10-24
Gave up! Plugged the laptop running Ubuntu 10.10 into my HP Photosmart c3180 and it just worked. Wish I could make it work via the network with my new Brother printer. I should have done a little more research before buying the new printer to make sure all of the drivers were available and installed without having to go through all of the stuff to install it. (Remember I am a newbie so I appreciate it when things just work. :)  )

---

### Post by lars-i on 2011-01-23
Hello,

I remember using Ubuntu 10.4 the installation of the Brother MFC-6490CW printer was no problem. But under 10.10 I also had problems. These are the steps that worked for me under 10.10:

- goto [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6490CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6490CW)

- download these drivers:
  LPR driver 	deb 	1.1.2-2 	1907 KB 	2008.Dec.09
  cupswrapper driver 	deb 	1.1.2-2 	14 KB 	2008.Dec.09

- install (double click) first the LPR driver
- install (double click) the the cupswrapper driver

- now goto the printer setting dialogue and install your printer

(I think in 10.4 I need not to install the cupswrapper driver. But under 10.10 this made the printer working for me.)

With kind regards,
Lars

---

