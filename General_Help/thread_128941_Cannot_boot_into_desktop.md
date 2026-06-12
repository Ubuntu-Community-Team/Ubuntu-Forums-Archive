---
title: "Cannot boot into desktop"
date: 2006-02-12
forum: General Help
---

### Post by Jackel003 on 2006-02-12
I just installed kubuntu and when I boot into it, I get a black console screen that tells me to login and enter my password. Once I do that I'm not sure on how to get into the desktop. I tried installing the "fglrx" drivers, but that did not work. I have an Ati card with a 64bit processor, but I am using the 32bit version of kubuntu. 

EDIT: When I am booting up I see "fglrx:firegl *Error* device not found [ok]"  Could this be the problem?

Ideas?

---

### Post by jonathan_c on 2006-02-12
What version of fglrx did you try to install? You don't need a 64-bit version if you are running 32-bit install of Kubuntu. Did you follow the installation guide on the wiki?

---

### Post by Jackel003 on 2006-02-12
I used the "BinaryDriverHowti/ATI" guide

I typed these commands in

sudo apt-get install xorg-driver-fglrx

then

echo fglrx | sudo tee -a /etc/modules

then

sudo dpkg-reconfigure xserver-xorg

and finally

sudo sed -e 's/"ati"/"fglrx"/' -i /etc/X11/xorg.conf
-----------------

when i try to "startx" I get a "No screens" error.

---

### Post by Prospero2006 on 2006-02-12
xorg.conf can be a total bitch.
I had to really do a lot of work to get my dual monitor support working well 
with ubuntu. My suggestion is that you download as many xorg.conf files as you can from the internet and plug them in. Once you make the replacements, type startx 
to see if X-server will fire up. Once you get to reading the xorg.conf file and comparing enough of them, it does start to make sense.

Prospero

---

### Post by jonathan_c on 2006-02-12
You could try the above and if you find an xorg.conf then you're all set. If you can't find one you might want to try "X -configure" It attempts to create an xorg.conf if the current directory. It might say things like could not find your mouse which should be easily fixable. and make sure to replace the "ati" driver with "fglrx" if it doesn't automaticall detect it.

---

### Post by alynx on 2006-02-15
i had the same problem with my GFORCE6600 GT

had to : sudo vi /etc/X11/xorg.conf 

and edit the driver section from nv to nvidia 

To make my X come up

---

