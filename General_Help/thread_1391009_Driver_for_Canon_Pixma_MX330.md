---
title: "Driver for Canon Pixma MX330"
date: 2010-01-26
forum: General Help
---

### Post by DukeBoxer on 2010-01-26
Does anyone have an idea of where i can find a driver for this printer? The system does not have one and if I try a driver for say the PIXMA MP220 which is CUPS + Gutenprint v5.2.4 [en] (actually, all the PIXMA drivers are that one) and I print the printer seems like it receives some command but nothing else happens. The printer says 'Printing from PC' and then goes back to the main screen. Thaks

-Josh

---

### Post by hhlp on 2010-01-26
here you are 

[http://software.canon-europe.com/products/0010698.asp]("http://software.canon-europe.com/products/0010698.asp")

---

### Post by DukeBoxer on 2010-01-26
Thank you sir.  I probably should have looked there before right...I didn't even think of it.

---

### Post by DukeBoxer on 2010-01-27
Ok, I got it working.  For anyone else that runs into this problem, make sure the printer is uninstalled from the computer then install the driver, restart the computer and plug the printer back in.  I was having a problem at first because the printer was still installed on the computer.

---

### Post by texla on 2010-06-07
> **hhlp said:**
> here you are 

[http://software.canon-europe.com/products/0010698.asp](http://software.canon-europe.com/products/0010698.asp)
Thanks for the link - These worked great.  Downloaded the debian files for linux.  There were two tar.gz files to download that extracted into four deb packages.  You have to install each of them.  The ones marked common go first but ubuntu won't let you do it any other way.  Then you plug in the printer at the end and all is working.  Of course the Windows version has a bit more software and stuff with it but I believe you can at least install the manual on ubuntu if you want (it's an .exe file not a pdf).  You would have to download the windows version and install it with Wine.  

 But I just put all that stuff on my windows install - only needed the drivers for my linux to run smoothly.  Glad they made it easy to use and doubly glad that the forum offered up the link with an easy search!  They neglected to tell Linux users where to go in their included instructions or even offer any drivers on their American website.... oh well - at least they had them there to use.

---

### Post by texla on 2011-04-24
MORE INFO FOR 64 bit install of Canon Pixma 330 or settings/grayscale additions for 32 and 64 bit:

64 bit 330 installs like this:
(adapted from [http://theseekersquill.wordpress.com/2010/05/03/canon_mp610_ubuntu_1004_64bit/](http://theseekersquill.wordpress.com/2010/05/03/canon_mp610_ubuntu_1004_64bit/))

sudo apt-get install ia32-libs cups libcups2 libcups2-dev build-essential

then:

sudo dpkg -i --force-architecture --ignore-depends=libcupsys2 cnijfilter-common_3.10-1_i386.deb

then:

sudo dpkg -i --force-architecture --ignore-depends=libcupsys2 cnijfilter-mx330series_3.10-1_i386.deb

then:

sudo /etc/init.d/cups restart

all of the above is done with printer unplugged, afterwards printer needs to be plugged in to be added to printer list.

then you can add new settings with this: (All of below info WORKS ON 32 or 64 bit btw)

(Originally Posted by **fauzie**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7868706#post7868706")              )   
                 [I]To get more options, (gksudo nautilus) and edit the appropriate file at /etc/cups/ppd

And add or edit the following lines. (They might be already available, but incomplete)

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 100/100 dpi: "<</HWResolution[100 100]>>setpagedevice"
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
 
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 5
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality[/I]
                                 
*OpenUI *CNGrayscale/Grayscale: PickOne 
*DefaultCNGrayscale: false 
*CNGrayscale false/Off: "false" 
*CNGrayscale true/On: "true" 
*CloseUI: *CNGrayscale 

Then make two extra copies of printer in the printing  settings and then go to  printing options and set one to GRAYSCALE 100dpi - Standard quality,  then one to Color 300dpi - Normal quality and one to hires color 600dpi -  high quality [I]     

Lastly, to have the Grayscale option : (copied from: [http://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/](http://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/))

[/I]To enable the Grayscale printing just follow the following steps .
 1. Click System &#8211;> Administration &#8211;> Printing .
 2. Now right click on your Grayscale printer and select properties .
 3. Now select Job Options
 4 . Now scroll down to the bottom .
 5. At the bottom you will see a text box . In that text box add &#8220;CNGrayscale&#8221; (without qoutes) and click on Add button .
 6. Once you click add there will appear another text box right above  the first text box . So in the second text box add &#8220;TRUE&#8221; and click on  apply .
 That's all , now your printer will print in Grayscale mode .



And for Scanner in 64bit:

Place the packages in your home folder for scangearmp 
(assuming you downloaded them or can find them - they are currently missing from the Canon site - June 8, 2011)

then in a terminal type:
sudo dpkg -i --force-architecture --ignore-depends=libcupsys2 scangearmp-common_1.30-1_i386.deb

and then:
sudo dpkg -i --force-architecture --ignore-depends=libcupsys2 scangearmp-mx330series_1.30-1_i386.deb

afterwards make a launcher with the command scangearmp (or type it in a terminal whever you want to run it)

---

