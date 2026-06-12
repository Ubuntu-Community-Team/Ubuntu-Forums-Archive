---
title: "Lexmark z55 installation"
date: 2009-08-02
forum: General Help
---

### Post by LinuxFanBoi on 2009-08-02
When manually installing the Lexmark z55 printer driver, I followed these instructions;

[INDENT]tar -xvzf CJLZ55LE-CUPS-1.0-1.TAR.GZ
tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
sudo alien -t lexmarkz55-CUPS-1.0-1.i386.rpm
sudo alien -t z55llpddk-2.0-2.i386.rpm
sudo tar xvzf z55llpddk-2.0.tgz -C /
sudo tar xvzf lexmarkz55-CUPS-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz
sudo /etc/rc2.d/S19cupsys restart
sudo /usr/lib/cups/backend/z55[/INDENT]

When I reach the very last command,  I get the following error;

> /usr/lib/cups/backend/z55: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

I can still add the printer by locating the ppd file and it looks as if it's installed, however the test page fails to print.

Any ideas?  Could this be a problem with running x86_64?

---

### Post by LinuxFanBoi on 2009-08-02
Bump

---

### Post by LinuxFanBoi on 2009-08-02
Bump again... 

If I can get some responses I'll stop bumping

---

### Post by HermanAB on 2009-08-02
Well, judging by the error message, libncurses.so.5 is missing.  You got to install it, or if you already installed a newer version of libncurses, make a soft link so that linbcurses.so.5 points to the version that is installed.

Otherwise, sell it on Ebay and buy a HP printer.

---

### Post by LinuxFanBoi on 2009-08-02
Actually,  the problem is that I had the 64 bit libraries installed,  but because the driver is 32 bit,  it needs the 32 bit libraries...

drum roll please.........
> sudo apt-get install ia32-libs
Done and... done!

Prints just fine, al though the printed page is a bit crooked on the paper :S

---

