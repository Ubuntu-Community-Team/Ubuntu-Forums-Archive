---
title: "printing with Canon Pixma MP560"
date: 2009-09-12
forum: General Help
---

### Post by yaise on 2009-09-12
Hi, 
Has anyone gotten the canon pixma mp560 working on ubuntu. The printer supports wireless printing too but i'm tyring to get it to print over the wire first. the printer is detected on connecting through usb.However, the only printers available in the database are those for mp500 and mp520. I tried both but neither worked.

Any ideas?

TIA

---

### Post by mfloris on 2009-09-23
I also have the same problem... Is there any news on this?

---

### Post by mor-bus on 2009-09-27
MP560 is a new version of MP620. Instructions on how to get MP620 working: [http://technicaltony.blogspot.com/2008/12/installing-canon-mp620-on-ubuntu.html](http://technicaltony.blogspot.com/2008/12/installing-canon-mp620-on-ubuntu.html)
I'm looking for a new printer and if the MP560 works under Linux it might be that. Please, let us hear if you get the printer working

---

### Post by mor-bus on 2009-09-30
I have found another guide for the MP620: [http://www.michael-krueger.org/2009/01/how-to-use-canon-pixma-mp620-with.html](http://www.michael-krueger.org/2009/01/how-to-use-canon-pixma-mp620-with.html)
Please report back how it goes with getting the MP560 working

---

### Post by Giblet5 on 2009-09-30
I had to purchase the TurboPrint drivers to REALLY get my Pixma MP830 working.

I can even print on printable DVDs reliably.

Sometimes, not often really, but SOMEtimes, ya gotta pay for results.

---

### Post by panosp on 2009-10-03
hi
i'm about to buy the same printer. Do you think i can make it work in hardy?

---

### Post by mfloris on 2009-10-11
Hi, I tried to follow the instructions and install it as if it was an mp620, but it didn't work...
turboprint does not support mp560, according to their website.

According to this page, canon will provide support in autumn 2009, maybe we just have to wait a bit... [http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp](http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp)

---

### Post by RifRaf1961 on 2009-10-28
Hi... I am using Ubuntu 8.04 (Hardy) and having the same problems using the MP560 with it.  I'm currently using a dual boot system with XP (I only use XP for a few programs there are no Linux equivalents) and all I can say is the MP560 is a very good printer/scanner for only $96!  It works fantastic in *cough* XP.  When I bought it I didn't notice it can be used in stand alone WiFi mode, which is how I set it up.  It's really nice to not have it as a shared printer where my PC must be on for my daughter or my laptop to use it.  Now if there were only Linux drivers because we both prefer Ubuntu!

---

### Post by mfloris on 2009-11-03
Hi,

the canon driver is not (yet?) out, but I noticed that a new version of turboprint was released and it supports the MP560 ([http://www.turboprint.info/](http://www.turboprint.info/)). I downloaded the trial version and it worked wonders! I have my printer configured for wifi: it was detected and configured immediately. The only drawback is that turboprint is not GPLed...

---

### Post by jmcvey on 2009-11-13
If you check the Canon Asian site, they have drivers available (although the MP560 is the MP568 on the site; once you get to the driver page it states "MP560").

Actually, here:

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

Look for:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...

and download the file.

Use Archive manager to extract the file and then look inside the directory it created. There should be a "packages" directory with 2 .deb files.

You can use dpkg to install the files (install the common file first) and if you're on a 64-bit system use the force option to make it work (that's why I had to use dpkg in the first place).

So you issue:

sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb

Then use the Printer configuration tool to add the new printer.

I use the Pixma over it's wireless connection and the printer tool found it and installed it without a problem once the steps above were done. Printed a test page and then a couple of documents. So far it handles the basic printing tasks without a problem.

Haven't tried the other software available on that site (that's for this weekend) but looks like there's a scanner package as well that I'll see if I can get working.

Jer

---

### Post by wbee on 2009-11-13
Hello,

This is pure conjecture on my part.

I have a Canon Pixma printer and before I got the hang of how CUPS and XSane work,I sent an e mail to Canon. They replied that they did not support Linux architecture.

*Here is the conjecture. I suspect they had a change of heart for these two reasons:

1.HP does support Linux and informed customers might select HP over Canon because the former supports Linux.

2.When the world economy does start to recover,lots of of Atom 1.6 processors in those new netbook computers are going to be sold. While many of those will be loaded with XP,others will be loaded with bare bones Linux systems.

My guess is that many companies,including Canon,want to compete for accessory business and that will only help the availability of Linux support.

The next time I upgrade a video card,it will be nVidia,because they now support Linux on their site's driver's page.

-------

---

### Post by RifRaf1961 on 2009-11-15
Thank you jmcvey!  I followed your link to the Asian Canon driver site.  These are the two links I followed to the EULA's with the driver download links at the very end of each page:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...
MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian Packagearchive).
support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html - 43

MP560 series ScanGear MP Ver. 1.40 for Linux (debian ...
MP560 series ScanGear MP Ver. 1.40 for Linux (debian Packagearchive).
support-asia.canon-asia.com/contents/ASIA/EN/0100237802.html -41

I just double clicked the tar.gz files to extract the packages into folders. Then I installed the printer first by going into the folder that was created for it and double clicked the common .deb package first. It launched the package manager for me and I just followed the screens to the install button. I repeated the above on the other .deb package. After that it was simple to add the printer as normal (note: it will show up as a mp560 printer, not a pixma mp560 in the list).  I was all smiles when the test page fired up the printer!

I did the same for the scanner and in no time I used Gimp to scan in a photo of my daughter.  XSane still sees my TV capture card as the input device which is no problem because I'd rather scan right into Gimp anyway. I'll get around to fixing that later... maybe.

By the way, I am using it in WiFi mode with Ubuntu on a 32bit system so I didn't need to use force commands you pointed out.  That is why I didn't even bother using terminal to install it.  Just a few mouse clicks!

Thanks again!
Rif

---

### Post by yaise on 2009-11-15
@jmcvey

Thanks.

I was able to wirelessly print. I'll take @RifRaf1961's word for the scanning :)

Thanks for trying it out and Thanks to Canon.

---

### Post by macleodjd on 2009-11-16
Has anyone been able to set this up that isn't using an i386 architecture?

---

### Post by macleodjd on 2009-11-16
Never mind, I read the instructions. Amazing how things work out better when you follow the instructions! :oops:

---

### Post by fcaldera on 2009-11-17
Hi guys, this is my first post here so thank you in advance

I've installed the drivers for the MP560 from canon-asia site but I cannot print in wireless (and at the moment i can't verify via usb connection)

I extracted cnijfilter-mp560series-3.20-1-i386-deb.tar.gz, then the printer was correctly detected at local ip. My network has dinamic IP assignment (dhcp) so the IP of the printer is not always the same) and is referred with 'cnijnet:/00-1E-8F-3D-A5-52' uri.

The printer detects the local network and she's ready for print in wireless mode. I have an ACL for my network so I allowed in advance the mac address of my printer.

When I print the test page, printer is going to process the job (for a while) but suddenly it goes to 'idle' and cups reports a generic error (*"error occurred while printing"*)

what could I verify yet? thank you

---

### Post by jmcvey on 2009-11-18
Couple of thoughts and a few suggestions..

1) You mention the one package for the printer but not the 'common' package. Did you install both? If not, try installing both and see if that fixes the problem.

2) Regardless of the package installations, if the printer is on the network, can you ping the printer via it's IP address? If not, there may be issues with the network.

2a) If you can't ping, can you try disabling all the ACL stuff and see if it works that way.
2b) If you can ping, is there any way to fix the IP address so the printer is not changing. Generally it's a good idea to not have things like printers and servers get a random address each time they attach to the network.

For 2b I can't say if this is the problem but if I look at the printer setup on my system the device URI doesn't reference a MAC address or IP. I tend to think that there is some association made initially when first setting it up but if the IP of the printer is changing it may be the linux system can no longer find it where it thinks it should be. That leads to..

2c) Can you create another instance of the printer and see if it starts working. If it does, then fixing the random IP issue may be what's causing the problem.

I've a few other ideas but it's late (really late actually) and before I keep guessing at it I'd like to get a bit of feedback.

Best of luck.

Jer

---

### Post by fcaldera on 2009-11-18
Hi jer, thank you for you reply
I've installed all drivers (common and mp560 specific in this exact order) both double-clicking and later using the script shell to install them. 

I ping correctly the printer and I assigned a static IP address 192.168.1.35
while laptop has always 192.168.1.33  Both are correctly detected by the router (192.168.1.1). (Maybe I should first assign a static IP and then install driver?)

I also disabled the ACL but the result doesn't change. :( 

So now I'm in your "2c" case. 

By the way, when I submit a job, the printer is detected for just a moment. in fact the printer display seems to have accepted the job, but after 5 seconds an error occured and printer returns to 'idle'.

---

### Post by jmcvey on 2009-11-23
fcaldera.. well, I'm a bit stumped by this. This may be a silly question, but do you have anything else that can print to this printer? (For me, my son has a Windows desktop so that made it easy to test if I had an OS related issue versus a printer issue if something didn't work). It would be good to know the printer is working over the wireless link before we possibly start down a dead-end path. (Which I tend to do quite a bit before I realize it so I don't want to send you down one if I can avoid that.)

Any chance you can test with another OS and see if the printer works. That way we could eliminate any issues on the printer side before delving deeper into the Linux side of this.

Jer

---

### Post by fcaldera on 2009-11-23
thank you jer,

the printer works for sure: i have already print some documents using the scanner function (like a photocopier) and I printed also the network information. 

It could be that printer (bought here in Europe/italy) has some issues with asian drivers? Perhaps it could be a matter of wireless frequency?

---

### Post by jmcvey on 2009-11-23
fcaldera.. I'm not worried about the printer not scanning and printing locally. What I'm wondering is whether the wireless part of the printer is actually working completely (rather than just syncing to an access point). If there's another machine that uses Canon's released drivers, over the wireless link, and can successfully print, then it rules out the wireless hardware in the printer. If that system also has problems printing, then it could be something internal to the printer.

jer

---

### Post by RifRaf1961 on 2009-11-23
fcaldera, I agree with jmcvey.  You need to rule out the wireless issue.  You mentioned you also have a laptop.  Is it Windows or do you have any dual boot systems that you can install the printer drivers on just to test connectivity?

My network uses DHCP for all the devices including the printer and I've never had any problems connecting to it.  It doesn't display IP address anywhere in the setup.  It just shows the MAC address.  The same is true for the scangear software.

By the way, if you set the MP560 up as WiFi you can't plug a USB cable into it.  That will stop it dead in its tracks.  It will work only one way or the other (WiFi or Wired).  Also, if you are using any WiFi protection schemes (WEP, WPA or WPA2) you may want to verify you keyed them into the printer network wizard correctly.  If the printer is setup correctly for WiFi use, it will identify itself as "MP560_Ver.3.20" where you add printers.  If it thinks it is USB it identifies itself as "MP560_Series".  I made the mistake of plugging in the USB cable trying to get the scanner to work with XSane and a bubble opened in the upper right saying "New MP560 Series printer detected".  If you did this and try to print, the same thing you described will happen.  It acts like it is going to print and then a few seconds later it will fail with an error message.  You need to go into System/Administration/Printing and remove the "MP560_Series" driver that was installed by inserting the USB cable.

Rif

---

### Post by RifRaf1961 on 2009-11-23
I see everyone is avoiding the Scanning function of the MP560.  It will not detect with XSane for me at all.  XSane keeps defaulting to my TV capture card and won't detect the MP560.  Since I'm seldom happy with a raw scan anyway, I prefer scanning into an image editing program, such as Gimp.  It is a simple matter of using the MP560 with Gimp. 

First you must install the Scangearmp drivers like you did for the printer part.  

Then load Gimp and File/Acquire/ScanGear MP... The first time you do it (or if you turn the printer off) you will get a "No Scanners Detected" message.  Okay that and you should be prompted with a Select Scanner dialog box.  Just press "Update Scanner List" and "Canon MP560 Series (MAC Address)" will be detected.  Press Okay and you get the ScanGear tool.  From there it is pretty obvious what to do.  Select the source type (ie; color photo), set the destination and output size if you want and just Press Preview, use the left mouse button to make a crop window around the image and then press the scan button.

Your image will open in Gimp where you can improve the image to your liking and then save it (or copy and paste to another application).  If you have multiple images to scan you can minimize the ScanGear tool between images so you don't have to keep acquiring it each time.

Give it a try... it works great!

Rif

---

### Post by fcaldera on 2009-11-25
Rifraf, i never used USB to connect to mp560. I only tried wireless. My laptop has only Ubuntu 9.10 and no other OS.

My wireless has no WiFi encryption/protection, no dhcp, but static IP for each device
Firewall has no rule, and by default it forwards all received packet

this is what i see when I enter the printer IP :



Printer Name: Canon MP560 series
Firmware Version: 1.030
Network Printer Name: MP560LAN
Bonjour Service Name: Canon MP560 series _3DA552000000

LAN Connection Type: Wireless LAN / IPv4
MAC Address: 00-1E-8F-3D-A5-52
IP Address: 192.168.1.35
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1

Network Type: Infrastructure
SSID: ZyXEL
Encryption Method: Do not use

Signal Strength: 56%
Link Quality: 70%
Transmission Rate: 54 Mbps


printer is identified as "Canon MP560 series Ver.3.20"

---

### Post by trixman on 2009-11-25
a freind of mine has a cannon printer 520, does ubuntu play with this printer nicely?


thanks to all

---

### Post by jmcvey on 2009-11-26
Trixman..

That same site (the Canon Asian site) has drivers for Pixma 520. Looks similar to what's available for the 560 so I'd think if you downloaded the 'common' and then the particular file, do the install for both of those, you should be able to get it working. Can't help more since I don't have one to play with, but see if that gets you moving.

Jer

---

### Post by jmcvey on 2009-11-26
fcaldera.. okay, from what you posted that's the web interface of the printer. To that end, it would seem you have network connectivity to the printer itself. I'm also assuming this is from a browser on your laptop so that means Ubuntu can "see" the box.

Now, that leads to what is going on when you try to configure this using the Printing tool? I didn't realize that connecting an USB cable tends to mess up the configuration (thanks Rifraf for that bit of info; also for the scanner info, never got around to that but hopefully there's time this weekend). To be safe, I'd delete all Canon printers if any exist. Then add a new printer, it should go looking for it. With any luck if you look under the 'Network Printer' section in the Devices list there should now be an entry for 'Canon MP560 (Canon...'. Now if you click on this selection, if I recall correctly, it took about 10-15 seconds before anything seems to happen (the Wifi light on my laptop was flashing during this time but the Printer diaglogs looked like nothing was going on). Once it did come back, the right side of the dialog changed to a "Description: LPD network printer via DNS-SD". You can click the 'Forward' button at this point and then you'll go throw the configuration ending with a point to print a test page.

So, is this what you experience when you try to add this printer to Ubuntu after install the two files from .debs you downloaded from the Asian site?

jer

---

### Post by dam718 on 2009-11-27
I'm pretty new to Linux, and this has been the first post I've made here (have read many)

I have been able to get the MP560 to work great for printing using the steps provided by jmcvey. I also loaded up the ScanGear MP drivers and I can't get it to scan anything. I tried to use GIMP and XSANE, neither of which worked. I don't know if I am using a different version of GIMP than RifRaf, but it appears that the version I have uses the SANE backend for scanning. When I go to file, there is no option to "Acquire" so it doesn't appear I can scan directly into GIMP without using the SANE backend. The only device SANE picks up is a built in USB webcam. :/

I am using Ubuntu 9.10 64-Bit, GIMP  2.6.7

I guess I shouldn't be a baby... I have several other machines in the house that the scanner is working just fine on, but I would really like this machine to work as well...

---

### Post by superlex on 2009-11-28
> **dam718 said:**
> I'm pretty new to Linux, and this has been the first post I've made here (have read many)

I have been able to get the MP560 to work great for printing using the steps provided by jmcvey. I also loaded up the ScanGear MP drivers and I can't get it to scan anything. I tried to use GIMP and XSANE, neither of which worked. I don't know if I am using a different version of GIMP than RifRaf, but it appears that the version I have uses the SANE backend for scanning. When I go to file, there is no option to "Acquire" so it doesn't appear I can scan directly into GIMP without using the SANE backend. The only device SANE picks up is a built in USB webcam. :/

I am using Ubuntu 9.10 64-Bit, GIMP  2.6.7

I guess I shouldn't be a baby... I have several other machines in the house that the scanner is working just fine on, but I would really like this machine to work as well...

Hi!
I have your same problem. That I think the blame is the use of drivers in our system 64 bit.
In fact, here is the response of the terminal:

> scangearmp
scangearmp: error while loading shared libraries: libgimp-2.0.so.0: cannot open shared object file: No such file or directory

but this library is present in the system:

>  locate libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0.600.7

Now I try to download the same library (but compiled to 32-bit) and to copy it in /lib/32

---

### Post by superlex on 2009-11-28
It Works!!
You can download it here:

[http://mirrors.kernel.org/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.7-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.7-1ubuntu1_i386.deb)

Then, you must extract it so:

```
dpkg -x libgimp2.0_2.6.7-1ubuntu1_i386.deb .
```

and you must transfer the libraries in /usr/lib32 .

---

### Post by rmgak on 2009-12-05
I followed the instruction on post #12.  I am running 8.4 and I installed the following using package installer.

cnijfilter-common_3.20-1_i386.deb

and then tried

cnijfilter-mp560series_3.20-1_i386.deb

but I get the following error

Error: Dependency is not satisfiable: cnijfilter-common

Is anyone had this problem?

---

### Post by fcaldera on 2009-12-07
> **jmcvey said:**
> fcaldera.. okay, from what you posted that's the web interface of the printer. To that end, it would seem you have network connectivity to the printer itself. I'm also assuming this is from a browser on your laptop so that means Ubuntu can "see" the box.

Now, that leads to what is going on when you try to configure this using the Printing tool? I didn't realize that connecting an USB cable tends to mess up the configuration (thanks Rifraf for that bit of info; also for the scanner info, never got around to that but hopefully there's time this weekend). To be safe, I'd delete all Canon printers if any exist. Then add a new printer, it should go looking for it. With any luck if you look under the 'Network Printer' section in the Devices list there should now be an entry for 'Canon MP560 (Canon...'. Now if you click on this selection, if I recall correctly, it took about 10-15 seconds before anything seems to happen (the Wifi light on my laptop was flashing during this time but the Printer diaglogs looked like nothing was going on). Once it did come back, the right side of the dialog changed to a "Description: LPD network printer via DNS-SD". You can click the 'Forward' button at this point and then you'll go throw the configuration ending with a point to print a test page.

So, is this what you experience when you try to add this printer to Ubuntu after install the two files from .debs you downloaded from the Asian site?

jer


I did exactly these steps as you suggested and the printer is now configured as dnssd://Canon%20MP560%20series%20_3DA552000000._printer._tcp.local/

When I try to print the test page the printer dialog says 
idle: /usr/lib/cups/backend/dnssd failed

---

### Post by chicky on 2009-12-09
> **superlex said:**
> It Works!!
You can download it here:

[http://mirrors.kernel.org/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.7-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.7-1ubuntu1_i386.deb)

Then, you must extract it so:

```
dpkg -x libgimp2.0_2.6.7-1ubuntu1_i386.deb
```and you must transfer the libraries in /usr/lib32 .


Hi!
As a newbie I'm trying to understand us much as possible.
I'm running 9.10 64 bits on a desktop. I've installed the  MP560 printer according to the directions given by [jmcvey]("http://ubuntuforums.org/member.php?u=14641") in post #10. All went well.

I've also installed scangear using the same principle, and as [superlex]("http://ubuntuforums.org/member.php?u=966676") in post #30, I ran into the same problems.
Now I understand that [superlex]("http://ubuntuforums.org/member.php?u=966676") has found a solution; step 1 download libgimp2.0 and step 2 unpack it.

But when I use the example from [superlex]("http://ubuntuforums.org/member.php?u=966676") I get an error:
--extract needs as target map.
Maybe you need 'dpkg --install'?
(maybe the translation is a bit of, but I'm not using an English version of Ubuntu)
How do I fix this?

Further [superlex]("http://ubuntuforums.org/member.php?u=966676") says "you must transfer the libraries in /usr/lib32". What does that mean?

---

### Post by superlex on 2009-12-11
> **chicky said:**
> Hi!
As a newbie I'm trying to understand us much as possible.
I'm running 9.10 64 bits on a desktop. I've installed the  MP560 printer according to the directions given by [jmcvey]("http://ubuntuforums.org/member.php?u=14641") in post #10. All went well.

I've also installed scangear using the same principle, and as [superlex]("http://ubuntuforums.org/member.php?u=966676") in post #30, I ran into the same problems.
Now I understand that [superlex]("http://ubuntuforums.org/member.php?u=966676") has found a solution; step 1 download libgimp2.0 and step 2 unpack it.

But when I use the example from [superlex]("http://ubuntuforums.org/member.php?u=966676") I get an error:
--extract needs as target map.
Maybe you need 'dpkg --install'?
(maybe the translation is a bit of, but I'm not using an English version of Ubuntu)
How do I fix this?

Further [superlex]("http://ubuntuforums.org/member.php?u=966676") says "you must transfer the libraries in /usr/lib32". What does that mean?

Hi!
Sorry, my fault, the command is wrong. The correct one is

```
dpkg -x libgimp2.0_2.6.7-1ubuntu1_i386.deb .
```

.
Basically, the problem is that if you install the package, the 32-bit library replaces the 64-bit one. So you have to copy it by hand so as to have both 32-bit library that 64bit.

---

### Post by chicky on 2009-12-11
[LEFT]Thx Superflex for the reply

But still not working?!?

When I type "scangearmp" in a terminal I still get the following:

scangearmp: error while loading shared libraries: libgimp-2.0.so.0: cannot open shared object file: No such file or directory

But when I type locate libgimp-2.0.so.0
I get the following:

/usr/lib/libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0.600.7
/usr/lib/debug/usr/lib/libgimp-2.0.so.0.600.7
/usr/lib32/usr/lib/libgimp-2.0.so.0
/usr/lib32/usr/lib/libgimp-2.0.so.0.600.7

I seems that the library (libgimp-2.0.so.0 as wanted by scangear) is in the /usr/lib32 folder.

So why can't scangear open the file?




[/LEFT]

---

### Post by superlex on 2009-12-11
> **chicky said:**
> [LEFT]Thx Superflex for the reply

But still not working?!?

When I type "scangearmp" in a terminal I still get the following:

scangearmp: error while loading shared libraries: libgimp-2.0.so.0: cannot open shared object file: No such file or directory

But when I type locate libgimp-2.0.so.0
I get the following:

/usr/lib/libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0.600.7
/usr/lib/debug/usr/lib/libgimp-2.0.so.0.600.7
/usr/lib32/usr/lib/libgimp-2.0.so.0
/usr/lib32/usr/lib/libgimp-2.0.so.0.600.7

I seems that the library (libgimp-2.0.so.0 as wanted by scangear) is in the /usr/lib32 folder.

So why can't scangear open the file?




[/LEFT]

You have made a mistake and you have copied the whole package to /usr/lib32 and so the result is this:

```
/usr/lib32/usr/lib/libgimp-2.0.so.0
/usr/lib32/usr/lib/libgimp-2.0.so.0.600.7

```

.

Now you give these commands:

```
sudo mv /usr/lib32/usr/lib/libgimp-2.0.so.0 /usr/lib32/
sudo mv /usr/lib32/usr/lib/libgimp-2.0.so.0.600.7 /usr/lib32/
sudo rm -rf /usr/lib32/usr
```

:D

---

### Post by chicky on 2009-12-11
Hai Superflex,

Thanks for the swift reply. This is gonna look more and more like a chat session (I don't mind)

I've copied and pasted your code into a terminal.
but when i locate libgimp now the result is:

locate libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0.600.7
/usr/lib/debug/usr/lib/libgimp-2.0.so.0.600.7

So we're back to square one. No libgimp-2.0.so.0 in the usr/lib32 folder.

Next I've reinstalled the libraries with :

dpkg -x libgimp2.0_2.6.7-1ubuntu1_i386.deb .

But for one reason or an other when I type 
locate libgimp-2.0.so.0

I still get:

/usr/lib/libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0.600.7
/usr/lib/debug/usr/lib/libgimp-2.0.so.0.600.7

When I look in the folder /usr/lib32 with Nautlus, I do find the files libgimp-2.0.so.0 and libgimp-2.0.so.0.600.7. Why don't then showup in the terminal?

It looks like I didn't install anything at all? what am I doing wrong?

(I must say that it is a complete culture shock going from Windows XP to Ubuntu, when it comes to things like this. Aldo I do realize that I didn't learn Windows in a week either)

---

### Post by superlex on 2009-12-11
> **chicky said:**
> Hai Superflex,

Thanks for the swift reply. This is gonna look more and more like a chat session (I don't mind)

I've copied and pasted your code into a terminal.
but when i locate libgimp now the result is:

locate libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0
/usr/lib/libgimp-2.0.so.0.600.7

So we're back to square one. no libgimp in the usr/lib32 folder

I do not understand why. :(

Now you give:

```
gksu nautilus
```

and you browser into /usr/lib32/ and checks for libgimp-2.0.so.0.600 and libgimp-2.0.so.0.

---

### Post by chicky on 2009-12-11
I've done 

gksu nautilus

browsed into /usr/lib32/ and checked for

libgimp-2.0.so.0.600 (not present, but libgimp-2.0.so.0.600.7 is)
libgimp-2.0.so.0 (present)

but with locate libgimp...... they don't show. how come?




I've restarted the computer.
When I type scangearmp in the terminal I get a new error message:

scangearmp: error while loading shared libraries: libgimp-2.0.so.0: wrong ELF class: ELFCLASS64

Any idea?

---

### Post by superlex on 2009-12-11
> **chicky said:**
> I've done 
scangearmp: error while loading shared libraries: libgimp-2.0.so.0: wrong ELF class: ELFCLASS64


probably the aforementioned library is 64-bit. So replace it with 32 bits one that were previously extracted.

 This time we use gksu nautilus instead of the mv command :)

---

### Post by chicky on 2009-12-12
Finally, after long hours fiddling it works.

Superflex really thanks a lot. =D>

---

### Post by superlex on 2009-12-12
If I had said beforehand using nautilus you would not come all this effort :P

but all well that ends well :KS

---

### Post by faintscrawl on 2009-12-19
Thanks to Jmcvey.

I installed printer drivers and was printing beautiful papersaving duplex wirelessly within 5 minutes.

Now download and test the scanner ...

---

### Post by faintscrawl on 2009-12-19
Scanning was trickier. Thanks to posts above I figured it out.

After installing the 2 scanner drivers from the site, xsane can't find scanner, so I go to Gimp. Then FILE-->Create-->ScanGearMP.  Yep, it was right there in Gimp. At first it won't find it but then it'll let you pick it and it works nicely. I tried a scan and it worked.

I went back to try directly from xsane, but it still couldn't find a scanner. Oh, well. I'll just use Gimp for scanning.

Thanks, everyone.

---

### Post by jmcvey on 2009-12-20
faintscrawl.. you're right about using GIMP (and following the various posts on this for scanning). However, if you want to just use the scanning app that Canon provides (which is what GIMP actually calls) you can create a menu entry for just that app.

To do so, goto System -> Preferences -> Main Menu. It will present with the utility to add/delete/modify your menu entries. I ended up clicking on the "Graphics" in the left panel and then the "New Entry" button. You'll get a 'Launcher Properties" window and fill in the following:

Type: Application
Name: ScanGear
Command: scangearmp
Comment: (I left this blank)

The install puts the scangearmp in the /usr/bin directory which is already in the path so you shouldn't need to explicitly type the full path.

Save the entry and then you should have a "ScanGear" entry under the Graphics menu under your main Applications menu. 

Either method works (GIMP or making the entry), just if you only need to scan this saves you from having to open GIMP.

Jer

---

### Post by faintscrawl on 2009-12-20
> **jmcvey said:**
> faintscrawl.. you're right about using GIMP (and following the various posts on this for scanning). However, if you want to just use the scanning app that Canon provides (which is what GIMP actually calls) you can create a menu entry for just that app.

To do so, goto System -> Preferences -> Main Menu. It will present with the utility to add/delete/modify your menu entries. I ended up clicking on the "Graphics" in the left panel and then the "New Entry" button. You'll get a 'Launcher Properties" window and fill in the following:

Type: Application
Name: ScanGear
Command: scangearmp
Comment: (I left this blank)

The install puts the scangearmp in the /usr/bin directory which is already in the path so you shouldn't need to explicitly type the full path.

Save the entry and then you should have a "ScanGear" entry under the Graphics menu under your main Applications menu. 

Either method works (GIMP or making the entry), just if you only need to scan this saves you from having to open GIMP.

Jer

Thanks. It worked. :)

---

### Post by faintscrawl on 2009-12-20
Actually, I am having an issue with this printer on my Ubuntu machine. It only looks for paper in the bottom tray. I'm trying to print on a sheet of 4x6 photo paper loaded at the back of the machine and it keeps saying no paper. I don't have this problem when I print a photo from my Mac, but on the Mac, when I print a photo, a window pops up and asks me exactly what type of paper I'm using. Anyone had this issue?

---

### Post by faintscrawl on 2009-12-20
> **faintscrawl said:**
> Actually, I am having an issue with this printer on my Ubuntu machine. It only looks for paper in the bottom tray. I'm trying to print on a sheet of 4x6 photo paper loaded at the back of the machine and it keeps saying no paper. I don't have this problem when I print a photo from my Mac, but on the Mac, when I print a photo, a window pops up and asks me exactly what type of paper I'm using. Anyone had this issue?

I think I got it.  You have to go to Configure Printer-->Printer options and then change the tray, paper type, paper size. For tray, I put it on 'automatically select'.

---

### Post by Zenos on 2009-12-21
I have been following the superlex/chicky posts about getting scanning to work on the mp560 (the printing works). I have the suggested libraries in /usr/lib32/.

I can get scangearmp to load up, and it doesn't detect my printer. I said ok and tried to "Update Scanner List" and nothing comes up. I've unplugging/replugging the usb and searching, turning the printer on while plugged in/not plugged in, etc. and it still cannot detect the scanner. Any thoughts here on next steps?

(My first post, woo!)

---

### Post by Zenos on 2009-12-21
> **Zenos said:**
> I have been following the superlex/chicky posts about getting scanning to work on the mp560 (the printing works). I have the suggested libraries in /usr/lib32/.

I can get scangearmp to load up, and it doesn't detect my printer. I said ok and tried to "Update Scanner List" and nothing comes up. I've unplugging/replugging the usb and searching, turning the printer on while plugged in/not plugged in, etc. and it still cannot detect the scanner. Any thoughts here on next steps?

(My first post, woo!)


Update if anyone is interested, after doing lots of stuff, i eventually (re)installed libsane-dev and then ran 

```

sudo sane-find-scanner

```

which DID detect my scanner but would not without the root privilege. Naturally it made me run  scangearmp as root and lo and behold my scanner was available and makes beautiful whirring noises when I start scanning. I will continue to see if there's an issue/fix for starting this as root but for now, at least it is functional at this point.

---

### Post by camdecoster on 2009-12-23
I just picked up an MP560 yesterday and was printing wirelessly as soon as I set up the printer with my network key. I'm running Linux Mint 8 and haven't had any problems yet. Though, like most other people, I can't get it to work with XSane. Gimp works and so does the ScanGear MP start menu tip from jmcvey. Has anyone gotten XSane to work with this printer?

---

### Post by madsc89 on 2009-12-25
I haven't red the talst posts in this thread, but I have now testet the MP560 on Linux mint 8 (Karmic) with the drivers from the asian site linked to in one of the first posts. Both printing and scanning over WiFi works perfect. Scanningtried through Gimp, worked perfect. Printing duplex from OOo also worked like a charm.

---

### Post by jono_1001 on 2009-12-31
@jmcvey
Thanks worked for me on Xubuntu 9.10, printing via wi-fi and scanning via gimp.

FWIW: I was lazy and used the cmd line install.sh script (for print) which worked and identified the printer for me.
Anyone having issues with scanning it's worth running from cmd line as you'll clearly see any issues reported back.

---

### Post by konohamarusan on 2010-01-04
jmcvey

Thank you very much!!!

---

### Post by jembo on 2010-01-07
Hi
 
Has anyone got a solution to this error message, since I have got stuck with it now,
I don't know if it's an issue with my ubuntu version (8.04) or an unpacking/installing problem.
 
Thanks
 
> **rmgak said:**
> I followed the instruction on post #12. I am running 8.4 and I installed the following using package installer.
 
cnijfilter-common_3.20-1_i386.deb
 
and then tried
 
cnijfilter-mp560series_3.20-1_i386.deb
 
but I get the following error
 
Error: Dependency is not satisfiable: cnijfilter-common
 
Is anyone had this problem?

---

### Post by madsc89 on 2010-01-07
Try reinstalling cnijfilter-common_3.20-1_i386.deb.

Looks like your problem is with that package.
Are you running 32 or 64 bit?

---

### Post by jembo on 2010-01-08
I've tried reinstalling the common file package several times, that installs fine.
 
When I try to open the extracted main package the error message shows before I can install it.
 
I'm running 32bit.

---

### Post by jwvraets on 2010-01-22
I am hoping someone can steer me in the right direction because I am trying to install the MP560 onto a 64bit Ubuntu 9.10 (fully updated) and having no luck even using the process from jmcvey (msg#10 in this thread, dated 13 Nov 2009), a process that others seem to find works.
 

 Here is what I did...
 

 I initially installed the printer using a Windows Vista laptop using a USB cable. Systems was fully operational.
 

 I installed the printer on an AMD Athalon II quad core (i.e. 64-bit architecture) using a  USB cable and it did work for printing (but not for scanning) after installing the drivers as per the process described by jmcvey #10.  
 

 I decided to change over to a wireless link rather than USB and in preparation for that I gave the printer a fixed IP address using the printers internal web page tools.  I set it to a fixed IP address (192.168.15.203) and it is fully operational from Vista.
 

 I reran the driver installation on the Ubuntu machine as per jmcvey #10 in hopes that the re-installation would clobber/replace the previous USB based installation (just in case).  
 

 The output of the forced re-installation as per jmcvey #10 was:  
 = = = = = =
 jwvraets@atilla:~$ cd /data/sys_updates/temp_mp560/print
jwvraets@atilla:/data/sys_updates/temp_mp560/print$ ls -la
total 1824
drwxr-xr-x 2 jwvraets jwvraets    4096 2010-01-20 16:42 .
drwxr-xr-x 4 jwvraets jwvraets    4096 2010-01-20 16:41 ..
-rw-r--r-- 1 jwvraets jwvraets  103882 2009-09-27 21:53 cnijfilter-common_3.20-1_i386.deb
-rw-r--r-- 1 jwvraets jwvraets 1742604 2009-09-27 21:53 cnijfilter-mp560series_3.20-1_i386.deb
jwvraets@atilla:/data/sys_updates/temp_mp560/print$ sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
[sudo] password for jwvraets: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 214093 files and directories currently installed.)
Preparing to replace cnijfilter-common 3.20-1 (using cnijfilter-common_3.20-1_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (3.20-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jwvraets@atilla:/data/sys_updates/temp_mp560/print$ sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 214093 files and directories currently installed.)
Preparing to replace cnijfilter-mp560series 3.20-1 (using cnijfilter-mp560series_3.20-1_i386.deb) ...
Unpacking replacement cnijfilter-mp560series ...
Setting up cnijfilter-mp560series (3.20-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jwvraets@atilla:/data/sys_updates/temp_mp560/print$


= = = = = = 
I can ping the printer using a terminal window on the Ubuntu machine.  I then accessed the printer's buit-in web page at its URL (i.e. the fixed IP of 192.168.15.203) and it displays properly in Firefox on both the Vista and the Ubuntu systems.
 

 When I then try to find the printer using:
     System > Administration > Printing
 I get &#8220;Printing configuration localhost&#8221; window as expected. No printers are listed (I deleted the printer before I started this whole re-installation process). Then I clicked on the &#8220;New&#8221;  button  and it begins to search for printers. After a short time a window is brought up with the title &#8220;New Printer&#8221; a a window on the left which labeled &#8220;Select Device&#8221;, below which a window lists the options. These are grouped under a label &#8220;Devices&#8221; as LPT #1, Serial Port #1, and other in the first group and an expandable entry labeled &#8220;Network Printer&#8221;. Clicking on the &#8220;Network Printer&#8221; it expands to the following options: Find Network Printer,  AppSocket/HP JetDirect, Internet Printing Protocol (ipp), LPD/LPR Host or Printer, and Windows Printer via Samba.  
 From that list I selected &#8220;Find Network Printer&#8221; and a Network Printer Host data entry area is provided into which I entered the fixed IP address of the printer (i.e. 192.168.15.203) and then I click on the adjacent Find button. A &#8220;Queue&#8221; selection list window is presented with the only option being &#8220;PASSTHRU&#8221; and a small &#8220;Connection&#8221; expansion button is provided at the bottom of the window      (options are a variety of LPD?LPR , queue types, covering LPT and Com options) the default of which is the first entry LPD/LPR queue 'PASSTHRU'. I left that alone and hit the &#8220;Forward&#8221; button.
 A new window appears with the title &#8220;New Printer&#8221; and it asks me to choose a driver. Its options are:
 
[LIST=1]
[*]Select printer from database
[*]Provide PPD File
[*]Search for printer driver to     download.
[/LIST]
 The default is &#8220;Select printer from database which I kept. The text below the options refers to &#8220;The foomatic printer database...&#8221; and then lists manufacturers. I selected Canon and the clicked on forward to view a list of models which do not included the MP560 (no surprise there).
 

 And there I sit.
 

 I apologize for the lengthy description but I hope it is helpful in tracking down where/how I went off the rails in this exercise. Can anyone who has successfully installed the drivers on a 64-bit system identify what I am doing wrong and (if possible) suggest how I can get this on track? Help would be very much appreciated.
 

 (and I have not even started on the scanner section yet...)
 

 JW

---

### Post by PeregrinGo on 2010-01-22
Mine worked perfectly out of the box. I'm so pleased. However, I'd like to know if there is a way to print in grayscale / b&w only. The one color option that shows up is RGB.

---

### Post by PeregrinGo on 2010-01-22
I found the answer [HERE]("http://translate.google.com/translate?prev=hp&hl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FCanon-Drucker&sl=de&tl=en") via [The Canon PIXMA Linux Blog.]("http://mp610.blogspot.com/"). It worked like a charm. This is one of the reasons I love Ubuntu (and Linux in general): The support community & mechanisms are unparalleled.

To make a long story short, you alter your .ppd file as found in usr/share/cups/model/canonmp560.ppd (this assumes that you had already downloaded and installed the .deb file from Canon Asia that corresponds to the MP560). You can do this by opening up nautilus in root (or opening the file in gedit as root), navigating to the file in the folder outlined, right-clicking it and opening in text editor. Then, you'll want to modify the file.

Insert the following:
```

*OpenUI *CNGrayscale / Grayscale: PickOne
*DefaultCNGrayscale: false
*CNGrayscale false/Off: "false"
*CNGrayscale true/On: "true"
*CloseUI: *CNGrayscale

```

I chose to put mine after the entry referring to color scale:
```
*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel
```

Additionally, you can add the following lines in order to increase the resolution with which you can print (The default includes only an option for 600dpi):
```

[B]From:
[/B]*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution[B]

To:
[/B] *OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200dpi/1200 dpi: "<</HWResolution [1200 1200]>>setpagedevice"
*Resolution 2400dpi/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution

```

---

### Post by maxounette on 2010-01-29
Hi 

I've just bought a mp560 (because someone from a shop told me mp640 didn't work on linux)
I've installed the links 

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...
MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian Packagearchive).
support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html - 43

MP560 series ScanGear MP Ver. 1.40 for Linux (debian ...
MP560 series ScanGear MP Ver. 1.40 for Linux (debian Packagearchive).
support-asia.canon-asia.com/contents/ASIA/EN/0100237802.html -41

both common and mp560

but I'm no computer expert and I don't know _what to do next_ you don't seem to explain after that you just say it works

I've plugged my printer in by usb switched it on and nothing happened I tried playing the canon cd install doesn t work and I've tried printing something with openoffice it detect s the printer but doesn t print

do I have to type in something in the terminal ?

I'm sure I ve missed domething really simple

Thanks allot

---

### Post by tornado42 on 2010-01-30
i downloaded the file via the same site...
support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html - 43


extract the folders to /tmp

user@ubuntulaptop:~$ cd /tmp
user@ubuntulaptop:/tmp$ ls
cnijfilter-mp560series-3.20-1-i386-deb  
user@ubuntulaptop:/tmp$ cd cnijfilter-mp560series-3.20-1-i386-deb/
user@ubuntulaptop:/tmp/cnijfilter-mp560series-3.20-1-i386-deb$ ls
install.sh  packages
user@ubuntulaptop:/tmp/cnijfilter-mp560series-3.20-1-i386-deb$ sudo ./install.sh

there will be some entries in the terminal window but once it says searching for printer....  i went to system >> administration >> printing and it was there.

just a few clicks and ready to go.

---

### Post by maxounette on 2010-02-01
Thank you so much for your help

I followed your instructions and it works great!

Do I have to do the same things with the scanner drivers??


As I haven't installed the canon cd is there a program to manage the scans from the printer or do I have to make it work using only the printer buttons ?

Thanks again

---

### Post by andreasbuykx on 2010-02-16
I've spent several hours now trying fruitlessly to get my laptop running Ubuntu 9.10 to print wirelessly to my MP560. My PC running WinXP does print wirelessly.

Here's what happened:

[LIST]
[*]installed the driver packages mentioned by earlier posters
[*]can connect to the printer's internet page
[*]Router security settings all switched off except for the WPA-PSK.
[*]Printer setup dialog finds the printer (as bjnp://Pilae-PRINT01.local:8611)
[*]Printing test page:
[LIST]
[*]Processing - Printing page 1, 8%
[*]Processing - failed to read backchannel data: Success
[/LIST]
[*]The queue will show the job status as 'processing' indefinitely.
[/LIST]
I tried to select different printer models: the MP560 entry has one 'recommended' which is the default, and another one which I tried as well, and there is also a PIXMA MP560 entry which I tried, but all gave the same message about the backchannel data. 

I tried googling for the message about the backchannel data, but I didn't find any information that led me to a solution.

Please help me understand what the problem is and how to fix it. 

Thanks!

---

### Post by -jay- on 2010-03-09
wow this even worked on a older canon thank you very much

---

### Post by GGG121 on 2010-03-25
Worked for me, thanks! Community support like this is why Ubuntu (...and linux in general) rocks!

---

### Post by dendari on 2010-03-30
I try to follow the instructions (post #10) and I get this:

dendari@ubuntuX86-64:~$ sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
[sudo] password for dendari: 
dpkg: error processing cnijfilter-common_3.20-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-common_3.20-1_i386.deb

I downloaded the file and extracted it into my downloads folder. Should I extract into a different directory? I can follow instructions, but best to assume I know nothing. 
Thanks

Ubuntu 9.10 on amd64

---

### Post by madsc89 on 2010-04-10
Canon Europe has now released linux drivers.
[http://software.canon-europe.com/products/0010756.asp](http://software.canon-europe.com/products/0010756.asp)

EDIT:
I have installed those on Ubuntu 10.04 beta 2 64 bit, and they are confirmed working over WiFi.
Notes: There are only 32 bit drivers included from Canon. Therefore, you need to use the option --force-architecture when installing on 64 bit systems.

What I did:
I used GUI for extracting the appropriate packages.
For printer function: 
I got the folder: cnijfilter-mp560series-3.20-1-i386-deb
I did not use install.sh, rather I opened the packages folder.
In terminal I wrote: "sudo dpkg -i --force-architecture " then I dragged the deb-package called "cnijfilter-common_3.20-1_i386.deb" into terminal, making the executed command "sudo dpkg -i --force-architecture '/home/**myusername**/Downloads/MP560_debian_driver_pack/cnijfilter-mp560series-3.20-1-i386-deb/packages/cnijfilter-common_3.20-1_i386.deb'"

I did the same to the other package, cnijfilter-mp560series_3.20-1_i386.deb.

I then turned on the printer, and added it through system -> administration -> printing.

I used the same approach for scangear, however, I needed to install one additional package (due to my 64 bit system) for this I used getlibs-all.deb ( [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) ). Install this, then write in terminal: "getlibs /usr/bin/scangearmp".
Confirmed working in gimp. (It says it couldn't find scanner... Say ok, then search and it should be detected.)

---

### Post by tardisrider on 2010-04-15
This works perfectly. Many thanks to all who contributed with instructions and development.

---

### Post by bgreenaway on 2010-04-19
I love the Ubuntu forums. Downloaded the .debs from Canon's Asian support site, followed the instructions on this thread and my brand-new MP560 worked like a charm. 

Despite starting out not even knowing whether Canon actually had a Linux driver, I actually got my printer config sorted before the missus did on her V*$ta laptop!

---

### Post by cdillard-hsp on 2010-04-27
Ubuntu ROCKS!  Not only because it is a robust, complete and powerful operating system but also because of the wonderful community that helps each other out.

My new PIXMA MP560 is up and running on Ubuntu 10.04 x86_64 and working great with duplex printing and scanning to GIMP over Wi-Fi.  Now to configure my wife's Windows 7 computer to print to it!

Love this community....

 - Clay

---

### Post by grege on 2010-05-05
CD printing on my MP640 turned out to be an issue. The Canon drivers simply refuse to offer CD tray as an option so the whole "print CD" falls apart. I use a network connection for the printer.

I tried Turboprint (demo), it went through the motions but nothing printed.

However, if you do not print many CDs there is a workaround.

1. Print you label to normal paper.

2. Put printed label in scanner and blank CD in tray and insert in printer.

3. From the printer itself select DVD/CD label copy and follow prompts.

It works fine for me, you just need a discernible circle of the correct size that the printer will see as a CD to be copied. I use OpenOffice Draw and created a simple light gray template of a CD disk.

Hopefully this will help someone.

---

### Post by pdfisk on 2010-05-08
Thanks to everyone who contributed help on this topic.  A few clicks and my old Acer TM244 is printing wirelessly on the MP560 thanks to the helpful folk here.

---

### Post by madsc89 on 2010-05-08
You've gotta' love the Ubuntu community! \\:D/

---

### Post by sheehanje on 2010-05-08
I just bought my wife this printer for mothers day, and haven't even opened the printer yet but followed this thread to see what I'm getting in to.

Anyways, just to add to the discussion, I found a handful of downloads for this printer on the European site, including source code for the print drivers.  If you follow this link, scroll down to find the drivers instead of making any selections for the OS or Language (if you do, the results come back empty)

[http://software.canon-europe.com/products/0010756.asp](http://software.canon-europe.com/products/0010756.asp)

In addition to the source files they also have a few different packages including a debian package that was tested with Ubuntu 9.04 ...  I am not sure if these are the same as the Asian site I've seen posted here...

I hope this helps someone, but it raises a few questions for me...

1)  If the software is on the Asian site and the European site, why is it not on the USA site?

2)  If the source code is freely available for download, why hasn't the distribution picked it up?  Maybe the license is incompatible?  This is a very common printer (I bought mine at Wal-Mart for $99)

3)  Just curious as to why it feels like it's buried?  It's not on the USA site, and you can't select it from the drop downs but have to scroll through over a  hundred other drivers for windows and os x

I won't complain too much though, I threw out a Lexmark printer a while back that will never work with any distribution, so it's nice to see that Canon has drivers at all, and the source code is available.  I just find it silly in this day and age that there are still printers with proprietary drivers...

---

### Post by t2000kw on 2010-05-15
Thanks to the information here, I was also able to get my 560 working over the wireless network. However, unlike most changes in Ubuntu, I had to reboot for the printer to be seen by Linux. 

I thought I'd mention this since someone else might have the same experience and give up before trying a reboot. 

Has any one been able to get some sort of monitoring of the ink levels on this MP560 printer?

Thanks

Donald

---

### Post by DannoXYZ on 2010-05-23
Printing to MP560 works fine for me under 10.04. I downloaded the v3.20 driver mentioned above from the Asian site and expanded the TAR.GZ archive. This save me a folder with two items: INSTALL.SH and PACKAGES folder.

I then opened up a terminal and ran: SUDO INSTALL.SH and answered a couple of questions and that was it. The default values for the printer was perfect (name, IP, etc.).

Going to test the ScanGear driver next...

---

### Post by dmagett on 2010-05-29
This forum is wonderful! I just purchased an MP560 to replace an old HP OfficeJet. My setup is
1. Wireless router on XP Desktop...MP560 installed as wireless.
2. Ubuntu 9.04 desktop with wireless card...connect to MP560 wireless 
3. Windows 7 laptop running Sun Virtual Box with Ubuntu 9.04 guest...again connect to MP560 wireless.
After this forum showed me where to find the drivers on the Asian site, I was able to install and connect sucessfully. Previously I had to have My XP Desktop powered on to use the attached printers remotely....now only the printer.
Thanks, Dave

---

### Post by N8N on 2010-05-29
so Canon DOES actually have Linux drivers, despite what their tech support people say?  Dayam.  I'm gonna have to check out their non-US sites to see if they have drivers for my scanner.  I thought I had to boot into Windoze to use it, maybe not...

edit: no such luck.  It's a CanoScan 5600F, and neither european nor asian sites had anything.  Oh well, back to your regularly scheduled discussion.  Glad you got your printer working, anyway, but on principle now that I'm aware of Canon's stance on support for Linux, I won't be buying any more Canon products unless I actually have to.

nate

---

### Post by t2000kw on 2010-05-29
The Canon printer being discussed ALSO has a built-in scanner. My guess is that Canon is changing their approach to making drivers available for Linux. They even made them available in deb package format instead of requiring us to compile the driver program ourselves. 

I don't know about you, but that impresses me. I don't think they'll go back and make drivers for previous printers but I look for them to make them for their most popular new printers. This particular ones is probably popular because it is also a wireless multifunction printer.

---

### Post by redcharlie on 2010-05-31
[http://software.canon-europe.com/products/0010756.asp](http://software.canon-europe.com/products/0010756.asp)

Worked for me!

I have two desktops running 32bit Jaunty, and both printing and scanning works w/o any issue.

Thanx!

---

### Post by rmgak on 2010-06-01
I installed the Canon Pixma MP560 drivers from Canon's Asian site on a Dell Mini 10 running  Ubuntu 10.4 Lucid Lynx and had no problems.  I just restarted the Dell and the printer and I found the printer on the network.  I could not get the printer to work under Ubuntu 8.4 that came with the Dell Mini.

---

### Post by mazato on 2010-06-15
I downloaded the drivers from Asian site, and just run dpkg on both files inside the packages folder, then added the printer through System/Administration/Printing and it worked, I almost cried :)
Then opened Gimp and went through New/Create/Scangear MP560 and saw my Dilbert  strip on my screen :)
I'm using my MP560 wifily :)

one more time, I'm amazed at the power of this Ubuntu  community. Thanks a lot to those that made it happened!


Ubuntu 9.04-32 bit with just 768 MD of RAM.

---

### Post by t2000kw on 2010-06-19
> **camdecoster said:**
> I just picked up an MP560 yesterday and was printing wirelessly as soon as I set up the printer with my network key. I'm running Linux Mint 8 and haven't had any problems yet. Though, like most other people, I can't get it to work with XSane. Gimp works and so does the ScanGear MP start menu tip from jmcvey. Has anyone gotten XSane to work with this printer?

I have Linux Mint 9 installed and also can't get Xsane or Simple Scan to recognize that I have a scanner. GIMP uses the Canon Scangear driver and works with the scanner properly. Using Xsane from within GIMP also does not work. 

I don't remember if it works on my Ubuntu Lucid installation with Xsane, but it does work with GIMP.

The printer works with both. 

Is there a way to get Xsane to recognize the MP printer?

Don

---

### Post by madsc89 on 2010-06-20
As far as I know, Xsane and other scanning solutions are not able to use MP560. Only GIMP or scangear are able to detect the scanner. The printerpart is deeply implemented in the system and is working good anywere there is a print option.

---

### Post by t2000kw on 2010-06-20
> **madsc89 said:**
> As far as I know, Xsane and other scanning solutions are not able to use MP560. Only GIMP or scangear are able to detect the scanner. The printerpart is deeply implemented in the system and is working good anywere there is a print option.

Is there a way to get to Scangear by itself?

---

### Post by madsc89 on 2010-06-20
Yes. It is crippeled, though. It can't compare to the windows verision.

The terminal comand is scangearmp.

---

### Post by t2000kw on 2010-06-20
> **madsc89 said:**
> Yes. It is crippeled, though. It can't compare to the windows verision.

The terminal comand is scangearmp.

Thanks! I can always use GIMP to do the basic scanning, which uses ScanGear. I don't really use all the features of ScanGear in Windows anyway. 

But I might make an icon tied to that command if I like ScanGear by itself in Ubuntu (or Linux Mint). 

I guess this is one of those things about using something that is fairly new, wireless printing and scanning. Someone mentioned that Xsane works if the 560 is plugged into the USB port. I would think that as wireless connectivity with peripherals becomes more widespread, we'll see improvements in this area that needs support. 

Don

---

### Post by joshua84 on 2010-07-04
this works perfect i have been trying to set up my mp560 for a week now and finally got it to work, thanks

---

### Post by delgotit99 on 2010-08-06
for 64bit folks.....works great so faron 10.4

[http://moritz89.wordpress.com/2010/05/23/canon-pixma-mp560-under-kubuntu-10-04-in-64-bits/](http://moritz89.wordpress.com/2010/05/23/canon-pixma-mp560-under-kubuntu-10-04-in-64-bits/)

---

### Post by computerwiz908 on 2010-08-19
> **madsc89 said:**
> Canon Europe has now released linux drivers.
[http://software.canon-europe.com/products/0010756.asp](http://software.canon-europe.com/products/0010756.asp)

EDIT:
I have installed those on Ubuntu 10.04 beta 2 64 bit, and they are confirmed working over WiFi.
Notes: There are only 32 bit drivers included from Canon. Therefore, you need to use the option --force-architecture when installing on 64 bit systems.

What I did:
I used GUI for extracting the appropriate packages.
For printer function: 
I got the folder: cnijfilter-mp560series-3.20-1-i386-deb
I did not use install.sh, rather I opened the packages folder.
In terminal I wrote: "sudo dpkg -i --force-architecture " then I dragged the deb-package called "cnijfilter-common_3.20-1_i386.deb" into terminal, making the executed command "sudo dpkg -i --force-architecture '/home/**myusername**/Downloads/MP560_debian_driver_pack/cnijfilter-mp560series-3.20-1-i386-deb/packages/cnijfilter-common_3.20-1_i386.deb'"

I did the same to the other package, cnijfilter-mp560series_3.20-1_i386.deb.

I then turned on the printer, and added it through system -> administration -> printing.

I used the same approach for scangear, however, I needed to install one additional package (due to my 64 bit system) for this I used getlibs-all.deb ( [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) ). Install this, then write in terminal: "getlibs /usr/bin/scangearmp".
Confirmed working in gimp. (It says it couldn't find scanner... Say ok, then search and it should be detected.)

This worked amazingly on my i686 Ubuntu 10.04 LTS installation!  Thank you so much!

---

### Post by jarnett on 2010-08-29
Any one have luck getting the card reader to work with 10.04?
All other functions work great thanks to all!

---

### Post by asookazian on 2010-09-22
> **jmcvey said:**
> If you check the Canon Asian site, they have drivers available (although the MP560 is the MP568 on the site; once you get to the driver page it states "MP560").

Actually, here:

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

Look for:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...

and download the file.

Use Archive manager to extract the file and then look inside the directory it created. There should be a "packages" directory with 2 .deb files.

You can use dpkg to install the files (install the common file first) and if you're on a 64-bit system use the force option to make it work (that's why I had to use dpkg in the first place).

So you issue:

sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb

Then use the Printer configuration tool to add the new printer.

I use the Pixma over it's wireless connection and the printer tool found it and installed it without a problem once the steps above were done. Printed a test page and then a couple of documents. So far it handles the basic printing tasks without a problem.

Haven't tried the other software available on that site (that's for this weekend) but looks like there's a scanner package as well that I'll see if I can get working.

Jer

This worked great for me via wireless as well.  thx!

---

### Post by i386pointer on 2010-10-14
I am using kubuntu, and installed the driver, but there is something wrong with printer, when I open file with xpdf, it will print, but it wont work when I using okular or type in shell $ lpr file, and somehow I cannot reinstall the driver, it gave me the 

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

I don't know where I was doing wrong, any suggestions would be helpful, thanks!

---

### Post by ocarlson on 2010-10-15
> **computerwiz908 said:**
> This worked amazingly on my i686 Ubuntu 10.04 LTS installation!  Thank you so much!

Also on an ancient Dell C640 laptop (32-bit, of course, Pentium M).

---

### Post by rmgak on 2010-10-23
Has anyone tried to install the MP560 drivers in Ubuntu 10.10 (64-bit)?  I have not been been able to install yet.

---

### Post by jv2112 on 2010-10-23
rmgak,

I forced the 32 (running 64 Bit OS) bit & I was all set (sudo dpkg --force-architecture -i Packagename) withe the printer. Still working on the scanner.

---

### Post by rmgak on 2010-10-25
> **madsc89 said:**
> Canon Europe has now released linux drivers.
[http://software.canon-europe.com/products/0010756.asp](http://software.canon-europe.com/products/0010756.asp)

EDIT:
I have installed those on Ubuntu 10.04 beta 2 64 bit, and they are confirmed working over WiFi.
Notes: There are only 32 bit drivers included from Canon. Therefore, you  need to use the option --force-architecture when installing on 64 bit  systems.

What I did:
I used GUI for extracting the appropriate packages.
For printer function: 
I got the folder: cnijfilter-mp560series-3.20-1-i386-deb
I did not use install.sh, rather I opened the packages folder.
In terminal I wrote: "sudo dpkg -i --force-architecture " then I dragged  the deb-package called "cnijfilter-common_3.20-1_i386.deb" into  terminal, making the executed command "sudo dpkg -i --force-architecture  '/home/**myusername**/Downloads/MP560_debian_driver_pack/cnijfilter-mp560series-3.20-1-i386-deb/packages/cnijfilter-common_3.20-1_i386.deb'"

I did the same to the other package, cnijfilter-mp560series_3.20-1_i386.deb.

I then turned on the printer, and added it through system -> administration -> printing.

I used the same approach for scangear, however, I needed to install one  additional package (due to my 64 bit system) for this I used  getlibs-all.deb ( [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) ). Install this, then write in terminal: "getlibs /usr/bin/scangearmp".
Confirmed working in gimp. (It says it couldn't find scanner... Say ok, then search and it should be detected.)

I  have tried to use these instructions because I am on a 64-bit machine  but I do not understand " then I dragged the deb-package called  "cnijfilter-common_3.20-1_i386.deb" into terminal."  I down loaded the  drivers but when I type in the commands I get an error file not found.   Any ideas of what I might be doing wrong?

---

### Post by rmgak on 2010-10-26
> **rmgak said:**
> I  have tried to use these instructions because I am on a 64-bit machine  but I do not understand " then I dragged the deb-package called  "cnijfilter-common_3.20-1_i386.deb" into terminal."  I down loaded the  drivers but when I type in the commands I get an error file not found.   Any ideas of what I might be doing wrong?

I got the printer working under Ubuntu 10.10.  I forgot to exact the files and had a typing error somewhere.  It works great!  Thanks for the instructions!  :P

---

### Post by slinky_41 on 2010-10-29
When I extract the file I only get a rpm file.  I dont see any .deb file.  And that doesnt seem to do anything

---

### Post by StratosL on 2010-11-11
I had real trouble setting up this printer with 64bit Mint 10rc. Eventually it worked, however. [I have posted the process in my blog.]("http://laspas.gr/2010/11/10/getting-canon-pixma-mp560-to-work-in-mint-10rc-64bit-and-ubuntu-10-10/")

---

### Post by TehThird on 2010-12-10
> **jmcvey said:**
> If you check the Canon Asian site, they have drivers available (although the MP560 is the MP568 on the site; once you get to the driver page it states "MP560").

Actually, here:

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

Look for:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...

and download the file.

Use Archive manager to extract the file and then look inside the directory it created. There should be a "packages" directory with 2 .deb files.

You can use dpkg to install the files (install the common file first) and if you're on a 64-bit system use the force option to make it work (that's why I had to use dpkg in the first place).

So you issue:

sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb

Then use the Printer configuration tool to add the new printer.

I use the Pixma over it's wireless connection and the printer tool found it and installed it without a problem once the steps above were done. Printed a test page and then a couple of documents. So far it handles the basic printing tasks without a problem.

Haven't tried the other software available on that site (that's for this weekend) but looks like there's a scanner package as well that I'll see if I can get working.

Jer

Thanks alot for this post. This worked as a charm on my asus eee 1000h with ubuntu 10.10 :)

---

### Post by Benster900 on 2010-12-10
I havr the MP560 drivers and is working wireless. On my computer in Ubuntu 10.4. I forgot where I got them. I will send a link of just make a mediafire link real quick for you guys. But I have the actaul driver for it and works perfectly. I do not know however if it works under Ubuntu 10.4.

---

### Post by Benster900 on 2010-12-11
This website has the .deb packages straight from the website. [http://software.canon-europe.com/products/0010756.asp](http://software.canon-europe.com/products/0010756.asp) I can't make it anymore easier than this. It works with wireless to.

---

### Post by Ghostnik11 on 2011-01-12
> **RifRaf1961 said:**
> Thank you jmcvey!  I followed your link to the Asian Canon driver site.  These are the two links I followed to the EULA's with the driver download links at the very end of each page:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...
MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian Packagearchive).
support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html - 43

MP560 series ScanGear MP Ver. 1.40 for Linux (debian ...
MP560 series ScanGear MP Ver. 1.40 for Linux (debian Packagearchive).
support-asia.canon-asia.com/contents/ASIA/EN/0100237802.html -41

I just double clicked the tar.gz files to extract the packages into folders. Then I installed the printer first by going into the folder that was created for it and double clicked the common .deb package first. It launched the package manager for me and I just followed the screens to the install button. I repeated the above on the other .deb package. After that it was simple to add the printer as normal (note: it will show up as a mp560 printer, not a pixma mp560 in the list).  I was all smiles when the test page fired up the printer!

I did the same for the scanner and in no time I used Gimp to scan in a photo of my daughter.  XSane still sees my TV capture card as the input device which is no problem because I'd rather scan right into Gimp anyway. I'll get around to fixing that later... maybe.

By the way, I am using it in WiFi mode with Ubuntu on a 32bit system so I didn't need to use force commands you pointed out.  That is why I didn't even bother using terminal to install it.  Just a few mouse clicks!

Thanks again!
Rif

Just wanted to say thanks for the solution worked great as i can now print wireless from my laptop to printer and it was thanks to your instructions

---

### Post by JohnMead on 2011-01-29
> **jmcvey said:**
> If you check the Canon Asian site, they have drivers available (although the MP560 is the MP568 on the site; once you get to the driver page it states "MP560").

Actually, here:

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

Look for:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...

and download the file.

Use Archive manager to extract the file and then look inside the directory it created. There should be a "packages" directory with 2 .deb files.

You can use dpkg to install the files (install the common file first) and if you're on a 64-bit system use the force option to make it work (that's why I had to use dpkg in the first place).

So you issue:

sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb

Then use the Printer configuration tool to add the new printer.

I use the Pixma over it's wireless connection and the printer tool found it and installed it without a problem once the steps above were done. Printed a test page and then a couple of documents. So far it handles the basic printing tasks without a problem.

Haven't tried the other software available on that site (that's for this weekend) but looks like there's a scanner package as well that I'll see if I can get working.

Jer

Used your post to install my MP560 on Ubuntu 10.10 and it worked a dream. Everything needed to do the install is in this post. Thank you Jer.

---

### Post by Spyderkid on 2011-01-29
could you mark this thread as solved and say what you did to fix this problem thanks :)

---

### Post by t2000kw on 2011-01-29
I appreciate the links and information. It worked for me when I was using Ubuntu 10. Flawlessly. 

These instructions also work on Linux Mint Debian Edition. The driver files linked to are actually for the Debian disto, but since Ubuntu is based on Debian, they work. Most *.deb packages will work on both. There is some compatibility between Mint and Ubuntu, but they aren't fully compatible. 

So far, though, I haven't found any issues. I switched to Mint because of the direction Ubuntu was taking with the desktop, and also because of a serious bug (serious to me) in Ubuntu ver. 10 where GRUB2 couldn't be installed in the Linux root partition instead of the MBR. It's supposed to be able to do that, so you can use a boot manager in Windows to start Linux. If you don't do it that way with Vista/7, you're asking for problems if you ever make changes to your partition table in Windows and then try to boot. I did, and I don't want that to ever happen again. 

Donald

> **jmcvey said:**
> If you check the Canon Asian site, they have drivers available (although the MP560 is the MP568 on the site; once you get to the driver page it states "MP560").

Actually, here:

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

Look for:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...

and download the file.

Use Archive manager to extract the file and then look inside the directory it created. There should be a "packages" directory with 2 .deb files.

You can use dpkg to install the files (install the common file first) and if you're on a 64-bit system use the force option to make it work (that's why I had to use dpkg in the first place).

So you issue:

sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb

Then use the Printer configuration tool to add the new printer.

I use the Pixma over it's wireless connection and the printer tool found it and installed it without a problem once the steps above were done. Printed a test page and then a couple of documents. So far it handles the basic printing tasks without a problem.

Haven't tried the other software available on that site (that's for this weekend) but looks like there's a scanner package as well that I'll see if I can get working.

Jer

---

### Post by t2000kw on 2011-01-29
> **i386pointer said:**
> I am using kubuntu, and installed the driver, but there is something wrong with printer, when I open file with xpdf, it will print, but it wont work when I using okular or type in shell $ lpr file, and somehow I cannot reinstall the driver, it gave me the 

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

I don't know where I was doing wrong, any suggestions would be helpful, thanks!

I'm not sure how you do this, but there must be a way to uninstall the deb package files and then go and reinstall them.

---

### Post by t2000kw on 2011-01-29
> **slinky_41 said:**
> When I extract the file I only get a rpm file.  I dont see any .deb file.  And that doesnt seem to do anything

Sounds like you picked up the wrong file. Try here. I refined the search using the term DEBIAN and found this one. 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html")

This is the one for ScanGear(see below for the link). My Linux Mint installation didn't need this driver as it scanned wirelessly even before I installed the Canon printer drivers! But it didn't find or install the printer, so I had to use the file above. I put the extracted files on my desktop, then opened a root terminal, typed

CD desktop

then ran the commands provided by member jcvey:


sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb

You would do similarly with the Scangear drivers if you needed those. 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100237802.html]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100237802.html")

---

### Post by dl5neg on 2011-01-30
Hi all,

thanks to this forum and others, I managed to install the MP560 on Linux Mint 10, 64bit, which seems to be the most tricky Ubuntu based platform for this printer. (For whatever reason, it was much less troublesome on Mint 9, 64bit, when I did it some months ago.) It works like a charm now on Mint 10 as well, nothing to complain (also the scanner works fine, and all of that over the WiFi network).

I did follow in principle this really nicely prepared instructions, and used the modified files, from this blog entry: 
[http://moritz89.wordpress.com/2010/05/23/canon-pixma-mp560-under-kubuntu-10-04-in-64-bits/](http://moritz89.wordpress.com/2010/05/23/canon-pixma-mp560-under-kubuntu-10-04-in-64-bits/)
It is written for Kubuntu 10.04 but works (almost) perfectly for Mint 10 as well. 

Now, there is one flaw in this description, which in my view, may be the root cause for all the extra trouble that is seen on Mint 10 64bit with these 32bit drivers from Canon. It took me a while to trace it down to this, but now it has made the problems go away.

There is a binary executable file called cnijnetprn, located in /usr/bin, which is apparently installed as part of the Canon driver installation. Now the installation must be enforced with --force-architecture as outlined in this forum before. BUT: this binary file does not work, since it is missing 32bit libraries. The obscure effect is, that during the setup, a "printer not found" is reported. That is a lie. What is should say is: the executable cnijnetprn, which has the task to find the printer, could not be started.

To try out if that is your problem as well, simply try to start it from a terminal:
cnijnetprn --search auto
If that command does run for a while and then comes back without a result, then your printer is really not found in your network. But if it returns immediately with an bash error, like: no such file or directory, despite the fact that the file is there and has the executable bit set, then you have exactly this problem. If the command should come back after some seconds with your printers name, well, then you have no problems at all, but then you are probably not browsing this forum anyway. 

Once that problem is identified, the solution is actually not that tricky any more. Install getlibs, see here:
[http://ubuntuforums.org/showthread.php?p=2849759#post2849759](http://ubuntuforums.org/showthread.php?p=2849759#post2849759)

Then you simply do a 
getlibs cnijnetprn
this downloads all needed 32libs and from now on, all the setup and also the command described above, work perfectly.

I hope that helps some of you to avoid spending endless nights to get this really nice printer working.

Have fun everyone! ):P

---

### Post by jimbudler on 2011-02-04
The site for downloading getlibs is suspended.

Here is what I did:

> On 64bit Ubuntu 10.10.

Downloaded MP560_debian_driver_pack.tar and MP560_Linux_Scangear.tar
from [http://software.canon-europe.com/products/0010756.asp](http://software.canon-europe.com/products/0010756.asp)

Unpacked MP560_debian_driver_pack.tar and MP560_Linux_Scangear.tar
and obtained 
[INDENT]cnijfilter-common_3.20-1_i386.deb 
cnijfilter-mp560series_3.20-1_i386.deb 
scangearmp-common_1.40-1_i386.deb 
scangearmp-mp560series_1.40-1_i386.deb
[/INDENT]
from them.

Executed the following:
sudo dpkg --force-architecture -i cnijfilter-common_3.20-1_i386.deb
sudo dpkg --force-architecture -i cnijfilter-mp560series_3.20-1_i386.deb
sudo dpkg --force-architecture -i scangearmp-common_1.40-1_i386.deb
sudo dpkg --force-architecture -i scangearmp-mp560series_1.40-1_i386.deb

Determined the printer utilities needed 32bit libgtk2.0-0 and scangear 
needed 32bit libgimp2.0, downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com).

You cannot install these, they would overwrite the 64bit equivalent, 
so instead extract them into a temporary location:

sudo dpkg -x libgtk2.0-0_2.22.0-0ubuntu1_i386.deb /tmp
sudo dpkg -x libgimp2.0_2.6.10-1ubuntu3_i386.deb /tmp

sudo cp -a /tmp/usr/lib/* /usr/lib32
cd /usr/lib/gtk-2.0/2.10.0
sudo cp gtk.immodules gtk.immodules.32

sudo EDIT gtk.immodules.32, change every occurance of lib to lib32 and remove 
the im-ibus.so line.

sudo EDIT /etc/udev/rules.d/40-libsane.rules and change: 
# Canon PIXMA MP530
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1712",ENV{libsane_matched}="yes"

to:
# Canon PIXMA MP530
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1712", ENV{libsane_matched}="yes"
# Canon PIXMA MP560
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="173e", ENV{libsane_matched}="yes"

This fixes the permissions so you don't have to run scangearmp as root.

[COLOR="Red"]Everything from here down to the reboot is optional.[/COLOR]

sudo EDIT /usr/share/ppd/canonmp560.ppd
and add
*Resolution 1200dpi/1200 dpi: "<</HWResolution [1200 1200]>>setpagedevice"
*Resolution 2400dpi/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 2400dpi/4800 dpi: "<</HWResolution [2400 4800]>>setpagedevice"
*Resolution 2400dpi/9600 dpi: "<</HWResolution[2400 9600]>>setpagedevice"d 

immediately below
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"

also add

*OpenUI *CNGrayscale / Grayscale: PickOne
*DefaultCNGrayscale: false
*CNGrayscale false/Off: "false"
*CNGrayscale true/On: "true"
*CloseUI: *CNGrayscale

immediately below
*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

[COLOR="Red"]Reboot[/COLOR]

After rebooting create the printer entry in the Gnome Printer Config
or at [http://localhost:631](http://localhost:631). When asked to select a printer model/driver select the checkbox for "Provide PPD File" and browse to /usr/share/ppd/canonmp560.ppd.

As pointed out by swdinesh the URL to use for the printer is lpd://<ip>/queue

The first time you use it, it takes a long time to connect. After that it is quick, perhaps until reboot or restart of print server.



Seems to be a very nice printer/scanner.
Jim Budler

---

### Post by cowdogmoocat on 2011-02-07
ahem... [http://software.canon-europe.com/software/0037271.asp]("http://software.canon-europe.com/software/0037271.asp")

---

### Post by jimbudler on 2011-02-08
> **cowdogmoocat said:**
> ahem... [http://software.canon-europe.com/software/0037271.asp]("http://software.canon-europe.com/software/0037271.asp")

Same print driver you get through the URL I provided, but of course through the URL I provided you can also get the scanner driver and the source code.:p

---

### Post by amagi on 2011-02-15
I have been able to print with this device for some time now. But, for some reason, I can not manually specify the printer resolution.

The UI shows the printer option, but the contents mentions:

<Unknown IPP tag>

I only found out that this really had to do with the PPD file when I changed it according to the info from @jimbudler

Does anybody else have this problem too?

I am using Ubuntu 10.10 64bit

---

### Post by tchen on 2011-04-09
Thanks! I did this and it detected my printer automaticly. Very simple to do and solves the problem.

Tyler

---

### Post by mytimps on 2011-05-02
After reading almost all of this thread I have still not been able to understand or even start to understand how I am supposed to install this printer.

I actually found on the ubuntu forum somewhere a while back a very straight simple step by step install but some how trying to update computer to the 11.4 version it f'ed up my system and I had to reinstall Ubuntu- I lost everything! "Tks). All this talk about dpkg, deb and code and scripting, extracting and what not- wth is it all? I mean, I am really new and some where on this d.am. os I am able to use some thing like the ms dos? Can some one point me in the direction of "easy install" for this printer?"  

Thanks, disgruntled, stressed and really PO'd.

---

### Post by jimmy-j on 2011-05-08
I just installed this for my printer using Ubuntu 11.04, and it worked great. It even prints 2 sided. As a new Ubuntu user I thought I was out of luck when I didn't see a driver in the initial install. Using a 32-bit system, I just had to click on the files that were downloaded from the site you referenced, and the installer came up and installed them.  How slick.  Thanks  jim

---

### Post by ontwowheels on 2011-05-22
> **jimmy-j said:**
> I just installed this for my printer using Ubuntu 11.04, and it worked great. It even prints 2 sided. As a new Ubuntu user I thought I was out of luck when I didn't see a driver in the initial install. Using a 32-bit system, I just had to click on the files that were downloaded from the site you referenced, and the installer came up and installed them.  How slick.  Thanks  jim

Anyone have this printer working on 64bit 11.04???

---

### Post by Patak on 2011-05-23
> **ontwowheels said:**
> Anyone have this printer working on 64bit 11.04???

no luck here, and I've tried every guide out there... it worked fine on 10.10 64bit for me...

---

### Post by selcho on 2011-05-24
Hi,
Have a look at this post.
[http://ubuntuforums.org/showthread.php?t=1475336&page=8](http://ubuntuforums.org/showthread.php?t=1475336&page=8)
HTH

---

### Post by ontwowheels on 2011-05-24
> **selcho said:**
> Hi,
Have a look at this post.
[http://ubuntuforums.org/showthread.php?t=1475336&page=8](http://ubuntuforums.org/showthread.php?t=1475336&page=8)
HTH

Thanks, I will try this soon.

---

### Post by ontwowheels on 2011-05-24
> **Patak said:**
> no luck here, and I've tried every guide out there... it worked fine on 10.10 64bit for me...

Works for me now

[http://ubuntuforums.org/showthread.php?p=10858618#post10858618](http://ubuntuforums.org/showthread.php?p=10858618#post10858618)

I used the MP560 printer and scanner set.

---

### Post by Patak on 2011-05-25
thanx,

I get these errors following the first guide you provided... 

dpkg: error processing cnijfilter-common_3.20-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing cnijfilter-mp560series_3.20-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg-deb: error: file `X.deb' is not a debian binary archive (try dpkg-split?)
dpkg: error processing X.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 cnijfilter-common_3.20-1_i386.deb
 cnijfilter-mp560series_3.20-1_i386.deb
 X.deb

I haven't tried the one where I'm supposed to unpack the .deb file and remove the dependencies...

Update 2:

After using force architecture I get those depend on errors... so I would need to remove the dependencies like you did except I have no idea how to get that step done...

---

### Post by ontwowheels on 2011-05-25
> **Patak said:**
> thanx,

I get these errors following the first guide you provided... 

dpkg: error processing cnijfilter-common_3.20-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg: error processing cnijfilter-mp560series_3.20-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
dpkg-deb: error: file `X.deb' is not a debian binary archive (try dpkg-split?)
dpkg: error processing X.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 cnijfilter-common_3.20-1_i386.deb
 cnijfilter-mp560series_3.20-1_i386.deb
 X.deb

I haven't tried the one where I'm supposed to unpack the .deb file and remove the dependencies...

Update 2:

After using force architecture I get those depend on errors... so I would need to remove the dependencies like you did except I have no idea how to get that step done...

This is corrected by applying the --force-architecture change to the install.sh files

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

If you look through the various posts you will see this mentioned a lot.

---

### Post by Patak on 2011-05-25
> **ontwowheels said:**
> This is corrected by applying the --force-architecture change to the install.sh files

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

If you look through the various posts you will see this mentioned a lot.

Even after I add force architecture to the install.sh file I get errors... I give up

---

### Post by Patak on 2011-05-25
hey ontwowheels,

how did you  remove the entire Depend line from all .deb files... this is where I get stuck?

The link you provided I can't really follow?

Thanx

---

### Post by selcho on 2011-05-25
Hi Patak,
Ref: [http://ubuntuforums.org/showthread.php?t=1427098](http://ubuntuforums.org/showthread.php?t=1427098)
Use a modified version of Barna's great step by step instructions to edit the control script in the expanded control.tar.gz file. Instead of using sed to modify "/libcupsys2/libcups2" in the Depends line, delete the entire Depends line then recompile the control.tar.gz and subsequently the new modified deb. Repeat this procedure for all four canon install debs.
cnijfilter-common_3.20-1_i386.deb
cnijfilter-mp560series_3.20-1_i386.deb
scangearmp-common_1.40-1_i386.deb
scangearmp-mp560series_1.40-1_i386.deb
Then install using the dpkg -i --force-architecture *.deb to satisfy the amd64 architechture. 
HTH

---

### Post by Patak on 2011-05-25
> **selcho said:**
> Hi Patak,
Ref: [http://ubuntuforums.org/showthread.php?t=1427098](http://ubuntuforums.org/showthread.php?t=1427098)
Use a modified version of Barna's great step by step instructions to edit the control script in the expanded control.tar.gz file. Instead of using sed to modify "/libcupsys2/libcups2" in the Depends line, delete the entire Depends line then recompile the control.tar.gz and subsequently the new modified deb. Repeat this procedure for all four canon install debs.
cnijfilter-common_3.20-1_i386.deb
cnijfilter-mp560series_3.20-1_i386.deb
scangearmp-common_1.40-1_i386.deb
scangearmp-mp560series_1.40-1_i386.deb
Then install using the dpkg -i --force-architecture *.deb to satisfy the amd64 architechture. 
HTH


Ok I'll try it right now...

---

### Post by Patak on 2011-05-25
it worked perfect... deleting the entire depends line was the key... thanx a lot

---

### Post by ontwowheels on 2011-05-26
> **Patak said:**
> it worked perfect... deleting the entire depends line was the key... thanx a lot

Yes, I also had to delete the entire depends line.  Only changing the libcupsys2 line did not work for me.

---

### Post by luchtzak on 2011-09-23
There seems to be a problem with this printer with ubuntu 11.04

how do I reconfigure my printer pixma mp560 so it works again ? 

thanks

---

### Post by ontwowheels on 2011-09-23
> **luchtzak said:**
> There seems to be a problem with this printer with ubuntu 11.04

how do I reconfigure my printer pixma mp560 so it works again ? 

thanks

I had to do this:

[http://ubuntuforums.org/showthread.php?p=10858618#post10858618]("http://ubuntuforums.org/showthread.php?p=10858618#post10858618")

---

### Post by Sm0ke42o on 2011-09-24
I followed the instructions provided earlier in this thread to install the MP560 on Linux Mint 11 x64 with the --force-depends switch added. 

Basically went like this:

-downloaded the Linux drivers from canons website. 

-extracted contents to a folder

-ran the following commands:

    sudo dpkg -i --force-architecture --force-depends cnijfilter common_3.20-1_i386.deb
    sudo dpkg -i --force-architecture --force-depends cnijfilter-mp560series_3.20-1_i386.deb

-Used the add printer tool (Find network printer > LPD\LPR > (point toward host))

-provided the PPD file created in /usr/share/cups/model/canonmp560.ppd

-Done!

Hope this helps.

---

### Post by luchtzak on 2011-09-25
in which folder do I have to extract as when I run the command in terminal it doesn't find the files.

---

### Post by heybobitsme on 2011-10-11
> **ontwowheels said:**
> I had to do this:

[http://ubuntuforums.org/showthread.php?p=10858618#post10858618]("http://ubuntuforums.org/showthread.php?p=10858618#post10858618")

I tried this with 11.10 and as soon as I get everything installed synaptic complains that I have broken packages and update manager wants to do a partial upgrade and remove the packages. It won't let me do any other updates until I do so.  Thoughts?

Edit: I found this: [http://kan.gd/1790](http://kan.gd/1790) and it worked. I can print again!

---

### Post by Sm0ke42o on 2011-10-13
> **luchtzak said:**
> in which folder do I have to extract as when I run the command in terminal it doesn't find the files.
You can extract the contents to any folder that you please. Just make sure you are either executing the commands from within that folder or enter the full path of the files when executing the dpkg command. 

Like so, 
 
```
sudo dpkg -i --force-architecture --force-depends ~/driver/cnijfilter common_3.20-1_i386.deb

```

That being said, the path of least resistance would go something like this:

- Open a command terminal
- Enter the following commands from your home folder:
  (The folder name is arbitrary, choose whatever you like.) 
```
mkdir driver
cd driver

``` 
- Download drivers and extract to the directory you just created.
- In your terminal window make sure you are still in the driver folder and proceed to execute the steps specified in my previous post.

---

### Post by qaissi on 2011-10-13
No more fooling around with making any files.

This site shows you how to do the ppa route and install what you need no matter x86 or x64.

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")

---

### Post by Gelupah on 2011-10-16
Will this work on WiFi printing too ?


> **qaissi said:**
> No more fooling around with making any files.

This site shows you how to do the ppa route and install what you need no matter x86 or x64.

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")

---

### Post by Gelupah on 2011-10-16
> **Gelupah said:**
> Will this work on WiFi printing too ?

Just found out it does... Splendid. The only thing I did wrong (could be useful for others) is I installed the drivers, but forgot to add the printer in the Printer / Administration Panel. It found it on the WiFi, and off I go

Made my day :popcorn:

---

### Post by Gelupah on 2011-10-17
One problem I did find though, is that I can't seem to print double-sided.

Is that just me or have others encountered this too ?

---

### Post by jmcvey on 2011-10-17
Just did a fresh install of 11.10. Decided to use the PPA to set up the printer. Everything installed fine and tested fine. However, I also notice that trying to print duplex just results in single sided sheets coming out of the printer. Don't know if this is something with the PPA drivers, the Canon base drivers, or the manner in which it is installed. I'll have to use the manual method later this week and pull the drivers from Canon's website to see if that makes a difference.

---

### Post by Gelupah on 2011-10-18
When I had 11.04 32 bits installed, printing both sides worked fine; those were the official Canon drivers. Not sure what is causing this, don't think it's the switch to 11.10...

Anyone with 11.10 32bits printing double sided ?


> **jmcvey said:**
> Just did a fresh install of 11.10. Decided to use the PPA to set up the printer. Everything installed fine and tested fine. However, I also notice that trying to print duplex just results in single sided sheets coming out of the printer. Don't know if this is something with the PPA drivers, the Canon base drivers, or the manner in which it is installed. I'll have to use the manual method later this week and pull the drivers from Canon's website to see if that makes a difference.

---

### Post by alfefried on 2012-02-01
> 
No more fooling around with making any files.

This site shows you how to do the ppa route and install what you need no matter x86 or x64.

[http://www.ubuntubuzz.com/2011/06/do...er-driver.html]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")


This worked fine for me, after hours, but yet !

The 228 Mo took a bit of time to download, but no more  worries after that.

Ubuntu 11.10 64
works in wifi

THAAAAANKS !

---

### Post by mowriter on 2012-02-18
THANK YOU for this.  Had the printer working under Linux mint, but had no luck in Ubuntu till you provided this.

FYI, the scanning feature?  On Ubuntu 11.10, the "Simple Scan" app innate within Ubuntu did the job just fine, no need to add anything else from Canon!!!!!

:KS:popcorn:

> **jmcvey said:**
> If you check the Canon Asian site, they have drivers available (although the MP560 is the MP568 on the site; once you get to the driver page it states "MP560").

Actually, here:

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP568&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

Look for:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...

and download the file.

Use Archive manager to extract the file and then look inside the directory it created. There should be a "packages" directory with 2 .deb files.

You can use dpkg to install the files (install the common file first) and if you're on a 64-bit system use the force option to make it work (that's why I had to use dpkg in the first place).

So you issue:

sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb

Then use the Printer configuration tool to add the new printer.

I use the Pixma over it's wireless connection and the printer tool found it and installed it without a problem once the steps above were done. Printed a test page and then a couple of documents. So far it handles the basic printing tasks without a problem.

Haven't tried the other software available on that site (that's for this weekend) but looks like there's a scanner package as well that I'll see if I can get working.

Jer

---

### Post by meyhus2 on 2012-05-25
The model number **Canon Pixma MP560**.

**Method 1:**
You may refer to the below links and use the troubleshooters. Check if it lists and helps resolve any issues: Open the Printer troubleshooter:
[http://www.usa.canon.com/cusa/support](http://www.usa.canon.com/cusa/support)

**Method 2:**
You may check if you have the latest drivers installed for the device. You may refer to the below link for getting the latest drivers and check –
[Canon Pixma MP560 Driver]("http://www.driverscanon.com/printer-drivers/canon-pixma-mp560-driver.html")

Good Luck.

---

### Post by shawnrgr on 2012-06-18
Yes after hours for trying to figure this out, simply installing the 2 deb packages with --force-architecture worked perfectly.

```
sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb
```

---

### Post by mikeric on 2012-12-13
Thanks for the info, I just installed in 12.10. Downloaded the files from canon asia and just clicked on and installed them. Then it auto detected the printer on the network and printed test page no problem. Took under 5 minutes.

---

### Post by KieranFitzgerald on 2012-12-14
I have been attempting to get my MP560 going on Ubuntu 12.04 on and off all day.  Synaptic reports that the packages above are installed.  I have set up the IP address in printers settings.

If I try to print a test page then printer state box has
  "Processing - The printer is not responding."

Printer works fine from XP and from this machine XP boot.

Any ideas?

How do I do a ping of 192.168.255.006 the IP for the printer?

Thanks

---

### Post by KieranFitzgerald on 2012-12-15
Update
partial print from USB using the rear paper feed rather than the main feed tray, status says idle but printer has not ejected sheet and still reports "printing from PC".
Hey ho!

I am upgrading my other PC soon and I was thinking of installing Ubuntu on it but I need to be able to print and Scan.

---

### Post by KieranFitzgerald on 2012-12-15
Update 2
Had two instances of the USB printer, deleted first one.  Now prints OK (still the wrong tray).  Drivers working??
So it's the wireless bit that's a problem.

---

### Post by KieranFitzgerald on 2012-12-16
Don't know how but wireless printing started to work after a test print via USB.

---

### Post by bijah on 2013-01-14
Hey,

I have a new problem. Since I used CUPS 1.5.3 the printer only prints the black component of colors. I tried every color model but nothing changed. The testpage looks perfect! I also removed the printer and added it after reboot again. nothing changed.

I run a lenovo x200s with Mint 13 on it.

thanks in advance...

edit:
SOLVED!!! It was only a switch in the advanced options choosing in the:

Common Printer Features:

Ink Type: CMYKk and not black

thanks anyway!!

---

### Post by pdc on 2013-01-16
Hi Bijah

Canon supply a utility cngpij that allows you to change various settings on your Canon printer

paste this into a terminal

> [COLOR="Red"]cngpij P MP560[/COLOR]

---

