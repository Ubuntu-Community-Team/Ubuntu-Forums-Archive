---
title: "libusb-1.0-0-dev on Ubuntu Hardy"
date: 2011-04-13
forum: General Help
---

### Post by arohde on 2011-04-13
Hi Ubuntu

This is my first post here. I'm trying to get the OpenKinect driver running on a development system that runs Ubuntu 8.04 (hardy). I have installed it on my 10.10 without any problem.

But on hardy, when I tried to install the packages mentioned in the description  I just can't find the libusb-1.0-0-dev for Hardy. Nor can I find it in the hardy backports.

I properly need to compile it from the source from libusb.org, but I have no idea how? And if I get the libusb compiled the how do I bind the newly compiled version with ubuntu instead of the "origional" libusb-0.1.

Hope some one can help.

Regards, Anders

---

### Post by ajgreeny on 2011-04-13
Hardy Heron (8.04) is about to loose all support, so I suggest you either do an online upgrade to the next LTS version 10.04, or even better in my opinion, do a clean install of 10.04, 10.10, or even wait a couple of weeks for 11.04.

---

### Post by arohde on 2011-04-14
Thanks for the reply, i got the source downloaded, compiled and installed, and it is fully working now. 

After download of the source I just executed, 
./configure; sudo make; sudo make install

And it worked as it should

---

