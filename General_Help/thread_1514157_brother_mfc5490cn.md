---
title: "brother mfc5490cn"
date: 2010-06-20
forum: General Help
---

### Post by rubot on 2010-06-20
i would like to install the mfc5490 cn printer under ubuntu 10.04 i am a first time ubuntu user an would like some help

---

### Post by wojox on 2010-06-20
Have you downloaded the drivers from the 
Brother site?

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by CompyTheInsane on 2010-06-20
You can download the drivers for the Brother MFC5490CN on the Brother Linux website.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

The printer drivers for the MFC5490CN are here - [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-5490CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-5490CN)

Once you get to that page, click on LPR Driver link (under DEB format), and then click 'Accept' to download the LPR driver for the MFC 5490CN.

Click on your browser's back button, click on cupswrapper driver (under DEB format as well), and then click 'Accept' to download the cupswrapper driver.

Once the drivers are finished downloading, Open mfc5490cnlpr-1.1.2-2.i386.deb and click on Install Package.
Once that package is finished installing, open mfc5490cncupswrapper-1.1.2-2.i386.deb
and click on Install Package.

Verify that the printer is recognized by going to System > Administration > Printing.

And now, the scanner: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3)
Under the brscan3 section of that page, click on the brscan3 link (32-bit or 64-bit, depending on whichever version of Ubuntu you have instaled), and click 'Accept' to download brscan3.
Once the driver is downloading, click on brscan3-0.2.11-2.i386.deb (or brscan3-0.2.11-2.amd64.deb) and click Install Package.

After that, open the Terminal (Applications > Accessories > Terminal)
and run this command: 
```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
```
Once that file is open, go to the end of that file, and then go one line before this line:
```

# The following rule will disable USB autosuspend for the device

```
and add these lines: 
```

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```
Save the file and then restart Ubuntu (unless you mind waiting until you restart to use the scanner.

Also, I have left out instructions for installing the scan-key-tool as I have not tried that myself. Here are the original instructions for installing that if you wish to do so:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html)

---

### Post by Legendary_Bibo on 2010-06-20
You gotta love this community :D

---

### Post by rubot on 2010-06-21
thanks for helping me out with my printerproblem 
rubot

---

### Post by SuperFreak on 2010-09-13
Is there a clear method for users new to Ubuntu to install the MFC-5490CN drivers for a 64 bit install of Ubuntu 10.04?  Thanks


Edit
For anyone looking for the solution to the issue of running a Brother printer on a 64 bit Ubuntu here is text taken from Brothers web site([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00081](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00081)) that seems to work:

# For dpkg users:
1. Install the standard c library for 32bit applications (e.g. lib32stdc++6(Debian) or ia32-libs(Ubuntu))
2. Create some folders if it is required
2-1. Create /usr/lib/cups/filter if it does not exist.
Command1: mkdir /usr/lib/cups
Command2: mkdir /usr/lib/cups/filter

2-2. Create /usr/share/cups/model if it does not exist
Command: mkdir /usr/share/cups/model

3. Install the drivers using "--force-architecture" or "--force-all"option.

4. Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to /usr/lib64/cups/filter/
Command: cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter

5. Copy libbrXXXX files under /usr/lib/ to /usr/lib32/ if /usr/lib32 exists.
Command : cp /usr/lib/libbr* /usr/lib32/

---

### Post by Rasputin69 on 2011-01-24
I did everything you said. The printer works.

It still does recognize the scanner.

---

### Post by SuperFreak on 2012-05-05
I can't get the MFC 5490CN to work in 12.04. There is no choice for it in the directory of Brother printers when installing automatically and if I try to install the drivers from the Brother web site Ubuntu software center says they are not approved or safe and refuses to install them. Help would be appreciated

Solved. Had to create lpd Folder in Var/Spool

---

