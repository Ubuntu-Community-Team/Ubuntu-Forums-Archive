---
title: "epson perfection 2480 won't start with xsane"
date: 2010-01-18
forum: General Help
---

### Post by crchtiger on 2010-01-18
Hi!
i had this scanner working perfectly but now when i want to use it xsane returns this error:

failed to open device 'snapscan:libusb:001:007':error during device I/O

under ubuntu 9.04 

any idea??

i tried to change usb ports, disconnect and reconnect the scanner, reboot and nothing helped...

thanks

---

### Post by plizzba on 2010-04-29
I am having the same problem with my epson perfection 2480. Any suggestions?

---

### Post by plizzba on 2010-05-05
So, I've been wasting my time trying to get this scanner working. 

Does anyone have the "epson perfection 2480 photo" scanner working in a recent version of ubuntu? It didn't work in 9.10 for me, and I upgraded to 10.04 with no luck.

I noticed that on [sane's supported dsane's supported device list device list]("http://www.sane-project.org/sane-mfgs.html#Z-EPSON"), this model is said to be "unsupported." On the other hand the "epson perfection 2480" is supported by snapscan. I guess these models are different?

On the other hand, I have certainly had this scanner working in linux (on Gentoo arround 3 years ago.) And there are posts from people who seem to have gotten the photo scanner to work (e.g. [http://ubuntuforums.org/showthread.php?t=975051&highlight=epson+2480](http://ubuntuforums.org/showthread.php?t=975051&highlight=epson+2480)) But these posts all seem pretty dated. Maybe the scanner is no longer supported?

---

### Post by ellgor on 2010-05-05
Hi,

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.  

Regards, Ellgor.

---

### Post by megahertz on 2010-10-12
To set up the Epson 2480 or 2580 scanner to work with Xsane you need:
- Install p7zip-full (Synaptic Package Manager)
- Install Xsane (Synaptic Package Manager)
- Extract esfw41.bin from /ESCAN/ModUsd.cab from Epson scanner CD
- On terminal type sudo nautilus (to open file manager as root)
- make folder /usr/share/sane/snapscan
- move  extracted file esfw41.bin to /usr/share/sane/snapscan

- with Nautilus (as root) go to /etc/sane.d and edit /etc/sane.d/snapscan.conf so at the 4th line you should have:

firmware /usr/share/sane/snapscan/esfw41.bin

- with Nautilus (as root) go to /etc/sane.d and edit /etc/sane.d/dll.conf and put a # on the beginning off all lines EXEPT on snapscan

Be sure the Epson scanner appears with command lsusb on terminal
- Bus 001 Device 003: ID 04b8:0121 Seiko Epson Corp. Perfection 2480 Photo

Your Epson scanner should be working
Applications - Graphics - Xsane

---

### Post by rubecula on 2011-06-21
Epson Perfection 2480 Photo.   Newbie to Ubunto having recently switched from Windows with everything working fine except the flatbed scanner.   Have tried a number of 'Remedies', most recently  'Megahertz' advice of October 12th, last, but still unable to start the scanner.  Attempting 'Simple Scan' produces "Unable to communicate with Scanner".  Not certain about the final instruction re: lsusb on terminal - Bus 001 etc etc.
This produces a list of options that are not understood.   Scanimage -n advises 'unable to open firmware file 
esfw41.bin.  Can anyone help please.

---

### Post by iparorratza on 2011-12-31
Check the esfw41.bin is not Esfw41.bin as it goes in the driver CD. 
Megahertz's answer worked for me after rename.
Thank you

---

