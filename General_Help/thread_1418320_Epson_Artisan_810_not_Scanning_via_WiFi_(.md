---
title: "Epson Artisan 810 not Scanning via WiFi :("
date: 2010-02-28
forum: General Help
---

### Post by xavierp on 2010-02-28
Ok so this is my second post here.  Has anyone encountered problems scanning with an Epson Artisan 810 using xsane 0.996?  When I hit the SCAN button on the xsane window I immediately get an error message: Failed to start scanner: Error during device I/O. Please note that I was able to successfully print a test page while the printer is setup wirelessly.

Any fixes would be greatly appreciated.

Thanks,
Xavier

---

### Post by DenysT on 2010-02-28
As far as I can tell there is no network scan support for Xsane and Epson networked all-in-ones. I have the same problem with my Artisan 700. You can try connecting via the USB to see if Xsane will work with the 810.

---

### Post by sforces on 2010-03-01
I've tried a bunch of things as well to get it to work with Xsane and just couldn't do it under Ubuntu 9.10 x64.

In my searching I found an app called iscan which is made by avasys for Epson for Linux which you can get here: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

While I still can't scan over the network, at least I can now scan using this tool when the printer is connected via USB. And they have both 32bit and 64bit deb packages.

> **xavierp said:**
> Ok so this is my second post here.  Has anyone encountered problems scanning with an Epson Artisan 810 using xsane 0.996?  When I hit the SCAN button on the xsane window I immediately get an error message: Failed to start scanner: Error during device I/O. Please note that I was able to successfully print a test page while the printer is setup wirelessly.

Any fixes would be greatly appreciated.

Thanks,
Xavier

---

### Post by prtsmgr on 2010-05-11
I got the Epson Artisan 810 wireless scanning to work by following the directions on this page:

[http://avasys.jp/eng/linux_driver/faq/id000652.php](http://avasys.jp/eng/linux_driver/faq/id000652.php)

In step# 4 you edit /etc/sane.d/epkowa.conf by adding an entry for your printer. 
Add only net and the printer ip address

Example:
#
net 192.168.2.7

I forgot to add that I am using Ubuntu 10.04 64 bit
Cheers :):):):)

> How do I set up and use the network plugin to scan via the network?
To set up your device for scanning via its network interface, follow the steps outlined below:

   1. Download and install the latest version of Image Scan for Linux! from here.
   2. If your device has a supported network interface, the iscan-network-nt plugin will also be available for download. Download and install the version appropriate for your system.
   3. Now configure your device for network access. You need to set or obtain the IP address of the device. Please consult the product manual for details on how to do this.
   4. Finally, configure Image Scan for Linux! to connect to your device by editing /etc/sane.d/epkowa.conf. You need administrative privileges to do so. Read the instructions in the file about network configuration and add an entry for your device as indicated.

---

