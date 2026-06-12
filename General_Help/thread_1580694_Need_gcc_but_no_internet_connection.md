---
title: "Need gcc but no internet connection"
date: 2010-09-23
forum: General Help
---

### Post by dremelts on 2010-09-23
I have a sort of "chicken and egg" situation.  I am setting up Ubuntu Server on a new machine here at home and want to get it pretty much ready before I deliver it to the person who will be using it for their small business.  Well, I don't have an internet connection at home... all my internet connectivity is thru my tethered Droid.  It's a usb tether using Azilink and OpenVPN.  I thought I would just set up OpenVPN on the server and tether it to my Droid to update the system.  But OpenVPN is source and I need to compile it.  When I try to run ./configure it says "no acceptable C compiler found in $PATH".  When I run dpkg -l |grep gcc it shows:

ii  gcc-4.4-base                    4.4.3-4ubuntu5                    The GNU Compiler Collection (base package)
ii  libgcc1                         1:4.4.3-4ubuntu5                  GCC support library

It appears that there is no gcc package installed.

So, I need to get on the internet in order to get the compiler installed so I can compile OpenVPN, but I need OpenVPN before I can get on the internet (I think I'm getting dizzy).

Any suggestions?

---

### Post by spiky001 on 2010-09-23
found this [http://www.google.co.uk/#hl=en&q=need+to+update+no+internet+ubuntu&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=44fc429e19c3a006](http://www.google.co.uk/#hl=en&q=need+to+update+no+internet+ubuntu&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=44fc429e19c3a006)  see if it helps

---

