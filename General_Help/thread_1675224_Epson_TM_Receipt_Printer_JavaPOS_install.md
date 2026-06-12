---
title: "Epson TM Receipt Printer JavaPOS install"
date: 2011-01-25
forum: General Help
---

### Post by J Doyle on 2011-01-25
Hi folks,
first post and new at linux so please be gentle.....

I'm trying to install a usb Epson TM-T88IV receipt printer on Ubuntu 10.04 using the JavaPOS driver.
There are instructions but they are for Red Hat and SUSE rather than Ubuntu. I'm making a (rather large) assumption that if it works for these distros then i should be able to get it working on Ubuntu?

This post appears to suggest that it should be possible:
[http://web.archiveorange.com/archive/v/qZjz3kRoCZXbf1Rfxy0B](http://web.archiveorange.com/archive/v/qZjz3kRoCZXbf1Rfxy0B)

I'm using the sun jre 1.6.0_22 and that all seems to be configured and working ok.

After install, a new kernel module USBTM should be running.
When the printer is plugged in, we should then see the printer picked up as \dev\usb\tm\usbtm0 

This issue is that after installing the ADK, the kernel module is not running so when we plug in the printer it is picked up as usblp0 instead.
There are no errors reported during the adk install so it is not obvious why it hasn't managed to install the usbtm kernel module.

*****

The steps described in the instructions for Red Hat are as follows:

1. Install gcc 
(have checked on Ubuntu software package manager and gcc is installed)

2. Install libusb using:
 rpm -i libusb-1_0-1-1.0.0-1.i586.rpm
(On Ubuntu both libusb-0.1-4 and libusb-1.0-0 are installed - is this right?)

3. Install kernel development package
Open a terminal window and type the following to install the kernel 
development package (against which we will build the TMUSB driver):
 
yum install kernel-devel 

(On Ubuntu I decided I needed to install the kernel development package and by googling discovered this:
sudo apt-get install linux-headers-$(uname -r)

Have no idea if what I did there is correct....)

4. Create a link in the /usr/src/ directory to the 
/usr/src/kernels/2.6.18-8.1.15.el5-i686/ folder and rename it as "linux" by typing: 
ln -s /usr/src/kernels/2.6.18-8.1.15.el5-i686/ /usr/src/linux

(the /usr/src/ folder exists but not the kernels/2.6.18-8.1.15.el5-i686/ - understandable as this relates to the red hat install.
It's not really obvious what I need to do to complete this step.
I think this /usr/src/linux link folder is required by the shell script that creates the usbtm kernel module.)

5. Run the Epson javapos ADK 

(This completes ok with no errors but the kernel module usbtm is not running.)

*******

There is a separate shell script which you can run to build/start usbtm and this fails with an error caused by the folder /usr/src/linux being absent.

So it seems the problem lies somewhere in step 3 or 4 above, however my knowledge and googling have both been exhausted so I am at a dead end.


Any help would be appreciated.

---

### Post by J Doyle on 2011-01-27
Nobody any ideas?

---

### Post by j-mi-jim on 2012-01-11
i have the same problem !

---

### Post by J Doyle on 2012-01-11
Hi,
I did eventually get this resolved through epson customer support. The linux driver doesn't work properly with ubuntu and you need a version of the driver specially compiled for it.

You need to drop an email to epson pos printer support (contact details are available through the epson pos website) you might have to subscribe. They should be able to provide you with the latest driver compiled for ubuntu.

Cheers,
Jeremy

---

### Post by j-mi-jim on 2012-01-11
Thank you very much.

---

### Post by j-mi-jim on 2012-01-12
Epson ne me répond pas par mail ;-(. 
Par téléphone, ils ne savent pas!
Pourriez-vous m'envoyer votre version s'il vous plait?

Merci d'avance

---

### Post by j-mi-jim on 2012-01-12
Epson does not reply by mail;-(.
 By phone, they do not know!
 Could you send me your version please?

 Thank you in advance

---

### Post by criatura on 2012-09-29
Same problem here, with Epson TM-T20. I tried using the cups driver tmt-cups-1.3.2.0. It prints just garbage. Now I'm breaking my head trying to install JavaPos.

---

