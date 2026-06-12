---
title: "Using a USB external modem"
date: 2010-05-12
forum: General Help
---

### Post by tyler9 on 2010-05-12
I'm planning to install Ubuntu on a new PC and use an external dial-up modem for internet connection.

The modem I plan to use is the US Robotics USR5637 56K USB Faxmodem, which USR claims is compatible w/Linux kernel 2.4.20:
[http://www.usr.com/support/product-template.asp?prod=5637](http://www.usr.com/support/product-template.asp?prod=5637)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006)

In the modem's Installation Guide, it says:
"You need a USB modem driver (CDC ACM) compiled into a Linux kernel 2.4.20 or higher or as a loadable module for your kernel. Installation of the modem under these kernels is fully automatic provided your kernel has the Plug and Play module enabled (default)."

So...uh...does Ubuntu meet these specs? Are some version #s of Ubuntu, or its variants, different with regard to these specs? I have the CD of Ubuntu 9.10 Desktop Edition--is this one OK? Should I try a later or earlier version? I'm really looking for a version that will be the least hassle to set up and use; I'll probably have to use Wine, so I can use MS Word 2000. Is there a Ubuntu version best for this too?

I'm choosing Ubuntu because of its rep as friendly to the home, non-techie user. Hope it's OK that I don't know what CDC ACM mean.

Thanks for help!

---

### Post by frank cox on 2010-07-17
Did you ever buy the modem?
If you have learned anything please let me know . It should install easily but when I installed an old serial modem though a USB adapter I had to run the setserial program and remove Gnome-Network and install Gnome-PPP.

I am trying to help someone else install that same modem .

TIA

> **tyler9 said:**
> I'm planning to install Ubuntu on a new PC and use an external dial-up modem for internet connection.

The modem I plan to use is the US Robotics USR5637 56K USB Faxmodem, which USR claims is compatible w/Linux kernel 2.4.20:
[http://www.usr.com/support/product-template.asp?prod=5637](http://www.usr.com/support/product-template.asp?prod=5637)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006)

In the modem's Installation Guide, it says:
"You need a USB modem driver (CDC ACM) compiled into a Linux kernel 2.4.20 or higher or as a loadable module for your kernel. Installation of the modem under these kernels is fully automatic provided your kernel has the Plug and Play module enabled (default)."

So...uh...does Ubuntu meet these specs? Are some version #s of Ubuntu, or its variants, different with regard to these specs? I have the CD of Ubuntu 9.10 Desktop Edition--is this one OK? Should I try a later or earlier version? I'm really looking for a version that will be the least hassle to set up and use; I'll probably have to use Wine, so I can use MS Word 2000. Is there a Ubuntu version best for this too?

I'm choosing Ubuntu because of its rep as friendly to the home, non-techie user. Hope it's OK that I don't know what CDC ACM mean.

Thanks for help!

---

### Post by tyler9 on 2010-08-01
> **frank cox said:**
> Did you ever buy the modem?
If you have learned anything please let me know . It should install easily but when I installed an old serial modem though a USB adapter I had to run the setserial program and remove Gnome-Network and install Gnome-PPP.

I am trying to help someone else install that same modem .

TIA

Yep, bought the USR 5637; plugged+played in Ubuntu 10.04, no problems. Setting up dialup was a bit problematic--see many dialup threads--but no probs with this modem.

USR 5637 is outstanding--works perfectly, rock-solid connections, no disconnects, always a high connection speed--48-50K. Well worth the $$. And small size makes it excellent for travel w/laptop [not all hotels/motels have broadband].

---

