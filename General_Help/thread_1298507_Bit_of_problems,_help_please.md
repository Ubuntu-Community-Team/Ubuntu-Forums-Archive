---
title: "Bit of problems, help please?"
date: 2009-10-22
forum: General Help
---

### Post by tranzue on 2009-10-22
Hello all,

I stuck this in General Help because I got two problems.
 
One is that I'm dual booting Windows 7 with Ubuntu, the newest one out.  Well, on my windows 7 i had to download an ATI Catalyst Control Center, to properly get my graphics card installed.

Well, Before i did this, my graphics were fine on my Ubuntu desktop, but since I downloaded this, it messed it up.

My second problem is my internet connection.  I properly downloaded my correct wireless driver for Ubuntu, but sometimes it wont connect me, even if it does show my network connection.  

Any help please?

Some more information, I have a Dell Inspiron 1501, Dual booting Windows 7 with Ubuntu, the newest.  

Thanks

---

### Post by cilynx on 2009-10-23
In my experience, ATI video cards are a bit finicky, especially when dual booting.  I don't understand why a piece of hardware would maintain settings over a rebbot, but I've had a few ATI cards exhibit this behavior.

The best solution I've found is installing the ATI Catalyst Control Center on the Ubuntu side as well and letting it do it's thing.  There's some black magic in there, but if you let it work, it generally fixes it.

As for the networking issue, I don't think I can be much help.  So far as I can tell, Network Manager is comprised almost entirely of black magic, with a little bit of voodoo thrown in for good measure.  Give me good old /etc/network/interfaces and iwconfig any day.

---

