---
title: "libusb-1.0.so not in /usr/lib folder after upgrade"
date: 2012-05-07
forum: General Help
---

### Post by vezinadj on 2012-05-07
I have just upgraded to ubuntu 12.04, and am at a loss in where my libusb-1.0.so libraries are. I was trying to run my c++ application build and was getting crashes on a bulk_transfer library call saying it didnt exist...then I realized that the library wasn't located in the libs. The include files exist in the libusb-1.0/libusb.h folder, but no libs! 

I tried reinstalling the libraries but they still do not exist in the folder. What to do! What to do!

Edit: I have found the libusb-1.0 in /usr/include/i386-linux-gnu, yet when building, i keep getting the error "No source available for "libusb_submit_transfer() at 0xb7fbc7d2"" which is a segfault on the library call. I am using eclipse CDT8...

---

