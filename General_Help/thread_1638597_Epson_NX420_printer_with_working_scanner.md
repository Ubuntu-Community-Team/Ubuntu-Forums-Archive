---
title: "Epson NX420 printer with working scanner"
date: 2010-12-05
forum: General Help
---

### Post by oldrocker99 on 2010-12-05
OK, I've been trying to get my Epson NX420 printer to scan for about three months now, and I finally got it working. Here's how:

1. Go to [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) and search for your printer. Select distribution and version and answer a couple of other questions.

2. Download pipslite_1.5.0-2_i386.deb, (or the 64-bit version), and all the iscan*.deb files (again, appropriate to your system).

3. [CRITICAL] Go to [http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3) and download this 8.04 package which worked just fine for me on 10.10.

4. Use the Software Center[-X or GDebi:lol: or sudo dpkg -i the .debs in this order:

1) libtdl3, which is a dependency for Step 2.
2) pipslite
3) iscan-data
4) iscan-network
5) iscan

(If you use a USB connection, you don't need the iscan-network file.)

This got my NX420 scanner up and running just fine. Installing libtdl3 was the key; in fact, I used the Debian Lenny package.

I hope this is useful to people. It's not a bad little all-in-one, and the price is right.

---

### Post by troy_at_trifftech.com on 2010-12-10
Awesome! Works great - Had been looking for this a few months back and glad I looked again - Maverick 10.10

---

### Post by cyberphrog on 2010-12-10
Thanks!  I'll give it a try this weekend.

---

### Post by oldrocker99 on 2010-12-13
Most glad I could help out; this is what I love about this community!:KS

---

### Post by tonderai on 2011-01-27
Thanks, that really worked well for me!

Note that there are some additional steps you'll need to take to get the network scanner working (as outlined on this page: [http://avasys.jp/eng/linux_driver/faq/id000652.php](http://avasys.jp/eng/linux_driver/faq/id000652.php))

1. Find your printer's IP address (you can use an NMap ping sweep to do this: eg. nmap -sP 192.168.1.*).

2. Edit /etc/sane.d/epkowa.conf and add your printer's IP address as a new line in the network section, as follows: ```
net <ip address>
```

3. Edit /etc/sane.d/dll.conf and comment out the "epson2" line, changing it to "#epson2"

Really amazing to have the scanner working over the network!

Thanks, David

---

### Post by gsparky2004 on 2011-03-05
Thanks for these instructions!  Worked perfectly on my brother-in-law's Ubuntu 10.10 system, both for the printer and the scanner.  He bought the Epson NX420 on a great discount ($60), and now the kids have a printer and scanner.

---

### Post by daev64 on 2011-03-06
> **oldrocker99 said:**
> 2. Download pipslite_1.5.0-2_i386.deb, (or the 64-bit version), and all the iscan*.deb files (again, appropriate to your system).

Where is this file? I can't locate it on Avasys' site, and a google turns up nothing... ](*,)

---

### Post by cyberfart on 2011-04-07
Also, it appears you must install iscan before iscan-network, as iscan is a dependency.

---

### Post by Avoozl on 2011-06-27
Everything here worked fine in Lucid.  Thank you so much!

---

### Post by oldrocker99 on 2011-06-29
OK, for the first time, I'm running 64-bit Ubuntu (love the extra RAM;)), and discovered that my above method had a fly in it: there is no pipslite.XXamd64.deb for 64-bit. No problem, said I, and downloaded the source code. Using ./configure, the results came up with a "'cups-config' missing, please install CUPS or fix your $PATH" error](*,).

Google is a wonderful thing=D>, and I found the solution by searching for the error string. To have the cups-config file, you need to install libcupsys2-dev, whcih is in the repositories\\:D/. Then it configured and made and installed just fine, after which I installed the iscan*amd64.deb files.

Just for anyone who has gotten that error.:-D

---

### Post by Stratosmacker on 2011-08-02
> **daev64 said:**
> Where is this file? I can't locate it on Avasys' site, and a google turns up nothing... ](*,)

I second this. I cant find the stuff I need. Any help would be greatly appreciated.

---

### Post by wyomingsour on 2011-08-06
Ok,
I have a 64-bit intel computer.  I am using lucid for the operating system.  I can't get it to recognize the scanner on my multi-function epson printer.  I have tried to load the various files at the avasys site, but get the incompatible architecture error message.

Any suggestions.
thanks.

---

### Post by wyomingsour on 2011-08-07
Problem resolved.  I reloaded all packages and my scanner works great.  In fact, I have three different scanner options to choose from:  simple scan; image scan for linux; and xsane image scanner.  Thanks for your prior posts that got me on the right path.:D

---

### Post by ReginaldPerrin3 on 2012-03-09
Ah... I see what people are concerned about. Trying to find the iscan and other packages? The website isn't well designed at all, making it very difficult to find them. However... if you go here: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) Go down to the bottom opf the page, select your distribution and version, then click the tiny &quot;next&quot; button. Again, it is badly designed, but on this page you can find the printer driver and the three scanner packages you will need.  It installs a prog called Image Scan! for Linux. You may have to restart the scanner and or the computer, but it does work.  Hope this helps Cheers

---

