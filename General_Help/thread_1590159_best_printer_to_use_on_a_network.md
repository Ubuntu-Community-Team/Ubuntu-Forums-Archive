---
title: "best printer to use on a network"
date: 2010-10-07
forum: General Help
---

### Post by happypig on 2010-10-07
My home network has 2 Kubuntu machines (mine), a Windows 7 laptop, a vista laptop and a Freecom FSG network storage device which acts as a file and printer server.
I bought a Kodak multifunction device as a friend has one and I liked the idea of cheaper printing. It's a good bit of kit, if printing directly from a windows machine via a USB connection but from linux boxes and networked from the win 7 box, it's crap, often needing rebooting before it will print (if it prints at all).
Can anyone recommend me a (cheap) printer that will be more suited to linux ? not bothered about photo quality, I'll keep the kodak for that and just connect via usb or plug in SD card directly.

---

### Post by efflandt on 2010-10-07
Since the dawn of time *nix computers originally used postscript, so any network printer that does postscript should be able to work.  HP PCL is also fairly widely supported and is backwards compatible (a driver for older similar printer will usually work).  Many years ago when I wanted to print something at Kinkos (now FedEx Office) on a parallel port I had no idea what Linux driver to use for a Xerox printer that was not listed.  So I simply used a generic level 2 postscript driver, and it worked.

But it would be best to check the website of any printer you are considering and see if they have Linux ppd files available.

Some people have trouble setting up Lexmark inkjet printers, but their Laser printers usually do Postscript and HP PCL.  When I got a Lexmark C543dn (color duplex network laser printer) which was just introduced, it worked from a bootable live Ubuntu USB iso using older Lexmark C534 driver.  Lexmark had ppd files for it C54x series.  The installer script for those did not seem to work in Ubuntu (maybe I forgot to use sudo), but all I had to do to install it from Printing config was to point to the extracted ppd directory.  Now my printer is in the repos, so Ubuntu can find a driver automatically.

At work when our HP Laserjet X3005n failed, I picked up a Lexmark X204n for $150 on sale, and all I had to do was set it to the IP that the HP had been using, and it simply worked without changing Windows HP driver (and remote printing via VPN from our factory).  It did not have duplex, but it is same 1200 dpi and understands Postscript and HP PCL, so it worked.  I have not tried printing or scanning with it in Linux, but know that printing would not be an issue.  Now the warranty replacement HP printer is failing, so the Lexmark may get some additional use until we replace the HP.

Basically see if the manufacturer has Linux support or ppd files, and/or if it uses a common printing protocol that may work with another driver.  The more it has in common with other network printers, the easier it should be to use.

---

### Post by pricetech on 2010-10-07
Overall HP seems to be your best bet.

I support several Color Laserjets, all of which just plain work under Linux and I personally have an HP Photosmart multifunction that works great too.  I know you said you didn't care about photo quality, but I know that one works.

---

### Post by Locke_99GS on 2010-10-07
HP works wonderfully. They provide opensource, *fully functional* drivers.

[http://www.hplipopensource.com](http://www.hplipopensource.com)

Ubuntu ships with the hplip drivers, but newer printers will require a newer stack. Easy though, if you require it.

I'm using a HP d110. It's connected via WiFi, and scanning, beautiful colour printing, even ink level detection all works great. I think I paid like $60 for my HP at the local WalMart.

---

### Post by happypig on 2010-10-12
Thanks chaps, the delivery man has just brought me a cheapo HP jobbie so we'll see how it goes :)

---

