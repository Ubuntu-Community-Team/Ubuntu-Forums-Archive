---
title: "Printer drivers - Which, when, where, why, and how?"
date: 2011-05-11
forum: General Help
---

### Post by jmws219 on 2011-05-11
Hi everyone,

I am having a lot of trouble understanding how my printer (an Epson PX710) is set up and driven on ubuntu.

I am really concerned with photo quality printing mostly through Gimp, but also through programmes like digiKam.

I have been trying to work with the gutenprint plugin for Gimp. But although the printer looks to be installed correctly, it clearly isn't printing correctly.

In an attempt to solve this and with the help of the open printing website, I believe I have now at least 3 drivers installed for my printer (is this a problem in itself), very little idea which is being used when, and the same problem.

The 3 drivers are  the recommended epson-stylus-photo-px810fw-series, epson-escpr and gutenprint.

My questions are

1. Are these really different drivers (after all 2 are made by epson apparently)?

2. When I plugged my printer into a fresh install of ubuntu the printer was recognised and could print (not that well). Which driver was being used then?

3. In Gimp "print with gutenprint" obviously uses gutenprint, but what about the standard print option? The options that come up look like a sort of Gutenprint-lite, and I have the same print quality issues as in gutenprint, but is this using one of the other drivers, or can it be made to use one of the other drivers.

4 What if I print from, say, DigiKam? The print windows that come up look quite different to those brought up by Gimp/Gutenprint. Is this just cosmetic? The actual options listed seem to be the same.

I could go on but that is probably enough for now. As you have probably guessed by now I am a total linux/ubuntu novice, but I like using it and, apart fom this issue, have created a really good linux photo machine, so it would be great to get this sorted.

Any help would be very gratefully recieved.

James

---

### Post by frank cox on 2011-07-13
Apparently you were lost in the system.
I an by no means a printer guru but I have set up several Epson printers in Linux with outstanding results. I was skeptical when I read the Epson printer much better under Linux but I can say that has been my experience with the rx620 , nx400 and 2 I forget the name of. The only laxer I have installed is the hp 1200 and it was easy enough with hpl+igon PL 431. 

The printer drivers I used where either from the people who Epson recommends ,[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/) , or by downloading the driver directly from Gutenprint.

Depending on the model I either used the sane driver or the ImageScan driver for the scanner, no worries.

Mostly I installed these printers to Puppy Linux 431. The RX620 was installed to 431 and Ubuntu 10.4 and Linux Mint 9 . The 431 installs were manual , on Ubuntu and Mint I plugged the printer in , went to printers , it asked if I wanted to install, I hit yes and that was that, perfect install in 30 seconds! 

Like I said I am no printer expert but here is my 2 cents worth. Consider why you use Lubuntu, I love the program because it is very fast, very stable , and it just seems tailor made for my old Gateway M275 tablet . The pen functions beautifully!
However I am beginning to suspect that it has far less printer drivers than Ubuntu or Mint to save space. I can deal with that but when I set upz a customers machine I would rather sacrifice a little speed for not having to mess with manual printer installs and  have a bit more "user friendly" system . Linux Mint 11.04 seems much quicker than previous versions running on a Dell 530 duo-core with 2 gigs of ram. They claim it will run fine on 500 megs so I plan to test it on an old P4 4500 desktop and also my M275 laptop with a gig.

I love Puppy Linux because it is blinding fast and so easy to rebuild but to install it on a customers machine would be economic suicide unless they understood that if they needed any new software added I would have to do it and they would have to pay. If I could get better with the Wacom software on Puppy I would probably ditch Lubuntu on my laptop.

If that option does not appeal to you try the [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/) .

What version of cups are you using? Sometimes that is the problem, latests is not necessarily greatest.

This fellow compiled a driver from source and was kind enogh to share the instructions. [http://the-happy-hackers.planzone.com/5/Printing%20with%20an%20Epson%20Stylus%20PX700W%20on%20Ubuntu.html](http://the-happy-hackers.planzone.com/5/Printing%20with%20an%20Epson%20Stylus%20PX700W%20on%20Ubuntu.html)

This fellow had success with this driver:
 Epson Stylus Photo RX700 - CUPS+Gutenprint v5.0.2

Here is the page I got these from: 
[http://www.linuxquestions.org/questions/linux-networking-3/impossible-install-epson-stylus-photo-px700w-wireless-on-ubuntu-8-10-64bit-716315/](http://www.linuxquestions.org/questions/linux-networking-3/impossible-install-epson-stylus-photo-px700w-wireless-on-ubuntu-8-10-64bit-716315/)


Hope this helped somehow. Myself I will never buy another inkjet. The only advantage to them is photos and WalMart will print them cheaper tha you can. Lasers are dirt cheap to run and you can get a good one for a small office for unger 150.00. The HP and Brother are my favorites, Samsung is ok if it is a lot cheaper. 

Good Luck

---

### Post by frank cox on 2011-07-13
It could be you need to update the drivers in Lubuntu-Instructions are here"
[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx)

---

### Post by jmws219 on 2011-07-13
Hi Frank,

Thank you for your reply. I had forgotten I had posted this. In fact I did eventually work out how to install my printer and which drivers are driving it. It turned out to be remarkably easy as most things are when you know how. And I now have a very good photo editing linux system based on ubuntu (not lubuntu - my error).

And like you I find the epson drivers a huge improvement over Gutenprint - for this printer at least.

I was interested in your comments about lazer prtinters. Maybe I will try one instead of an ink jet in future. I have found though that a well colour-managed photo printing set up produces better prints than any commercial printing service that I have tried so far. But you are right, it ain't cheap.

Many thanks again,

James

---

### Post by skipx on 2011-10-06
but which drivers where the right ones? :) 
     (need them to..)

---

### Post by jmws219 on 2011-10-06
Epson's own driver. You can find them all here. [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

Good luck.

---

