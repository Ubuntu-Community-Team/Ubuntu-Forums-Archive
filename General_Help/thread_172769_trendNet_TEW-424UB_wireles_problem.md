---
title: "trendNet TEW-424UB wireles problem"
date: 2006-05-09
forum: General Help
---

### Post by gauvain65 on 2006-05-09
Hi There,

Has any one ever tried to make a TrenNet TEW-424UB usb wirless key with ubuntu ?
I have tried to install the windows drivers via ndiswrapper, but it does not seem to work.

Any lead in the right direction would be welcome.

---

### Post by tristandeboer on 2006-07-05
*bump*.. indeed, any assistance here would be welcome because I have the same piece of harware

---

### Post by gauvain65 on 2006-07-12
I fixed the problem,

This is how:

1) I installed the Trend Wirless on my daughters computer (runs windows 98) so it is OK.

2) I bought a D-Link Air Plus Extreme G (DWL-G650) and it just works out of the box on Linux.

Kinda extreme solution..but hey...everybody is happy now..

---

### Post by joereid on 2006-12-11
very funny solution.  i really liked it.  i'm posting this in case people are looking for help making it work. i had to search and learn to make it work, and hope it helps someone.
i've gotten this driver to work in ubuntu 6.10 edgy eft.
i am sorry that i do not remember every exact step to do it, but hopefully this will get ya'll headed in the right direction.
i can confirm that it will work in ubuntu. i have done it. it worked.
the zd1211 or other drivers that i see people talking about isn't made for the particular chipset in the tew-424ub usb wireless thingy.
the zd1211 or whatever driver is made for the older model. the A series. we have the b series/model. mine is blue with a flippy cover for the usb thing.
here is how i did it.
i went to ndiswrapper home page, [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net) and got their latest release. this might not be entirely neccessary.
then i got all the build tools for ubuntu from synaptic. gcc g++ etc.
look for a howto if you need help with that part. i always refer to howtos.
next, i built and installed ndiswrapper.
now you may not need the latest version. it may be possible to skip those steps, and just install the ndiswrapper that is in synaptic.
after installing ndiswrapper, make sure you have the wireless tools, iwconfig and iwpriv and iwlist. its all in a wireless tools package or something in synaptic.
next, get your windows driver or the new driver for it off the [www.sis.com](www.sis.com) website. i used both, so either will work.
then give the command, ndiswrapper -i /path/to/driver.inf which is the windows driver. i think it is named 163u.inf or something.
that installed the driver.
next, run the command, depmod -a (this should only have to be run the first time, or only once.)
next run the command, modprobe ndiswrapper
you should have wlan0 now. its like eth0.
iwconfig will allow you to set essid and stuff.
and dhclient is already running on it.
your hardware is working now, all you have to do is configure it.
so to sum up, install ndiswrapper, get windows driver, run ndiswrapper -i driver.inf, the first time you use ndiswrapper after installing it you have to run depmod -a, then run modprobe ndiswrapper.
next, commands like iwconfig wlan0 essid s0me_id, iwlist scan, and man iwpriv should be helpful for setting it up. if i remember correctly, i just had to set essid, and used ifconfig to set the ip (no base station or dhcp here, i used ad-hoc mode and talked between two of them)
sorry this post is so sloppy, and fast.
i just wanted to give yall the info i know about this quickly and wanted to share. i hope it helps you. and if you get it working, please post instructions here and anywhere else you can find. like better directions than these. also, i expect that i would have had a lot easier time setting it up the first time if i had had dhcp and a base station.
you won't need the ifconfig command if you have dhcp.
after i got it set up here, i broke it somehow and then finals came in college and i'm waiting to finish before delving into it.
you can check back in a week or two from this post and i'll probably put up a much better howto. again, sorry its not exactly step by step.
this should get you headed into the right direction, and let you know its possible. i surfed from the couch for the first time in my life. it worked, for sure. hope this helps.

---

### Post by joereid on 2007-01-29
it works now.  it has been fixed. i tested it too.  it works. :)
the date is 1-28-2007 
currently, its in the svn revision 2186.
the current stable version is 1.35  but it doesn't work in this version.
it will in the next version, 1.36 or later
to get the svn version, run this command.
svn co [https://svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper](https://svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper) 
now you will have a folder called ndiswrapper.  
to install it, run these commands.  doesn't matter if the first two give errors or not.

sudo rmmod ndiswrapper
sudo ndiswrapper -e sis163u
cd ndiswrapper
sudo make uninstall     # might try running that twice
make
sudo make install

you have it installed now.  next plug in your trendnet thingy if it isn't already, and set it up. for example:
sudo ndiswrapper -i /path/to/sis163u.inf
sudo modprobe ndiswrapper

hardware is up and working now.
iwlist wlan0 scan  should give you results. get your essid and type:
sudo iwconfig wlan0 essid YourEssid
sudo dhclient3 wlan0  #to do dhcp   else, use ifconfig wlan0.
you should be set.  

with svn you can use svn up -r XXXX  to go back or forward through revision numbers. shouldn't need that.
2186 is the latest and the first to work with this card in ubuntu.
after ndiswrapper 1.36 comes out, it and every one after should work.  :)
i'll follow [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)  and make a package for it, but i don't know if it will make it to any repositories.   
enjoy !  and i'm using the card now. it works.
i'm using the [http://downloads.trendnet.com/TEW-424UB_v2%5CDriver_Utility%5CUtility_Driver_TEW-424UB(v2.x).zip](http://downloads.trendnet.com/TEW-424UB_v2%5CDriver_Utility%5CUtility_Driver_TEW-424UB(v2.x).zip)
driver for windows.  found it of the [www.trendnet.com](www.trendnet.com) site.  easy to find.

---

### Post by gauvain65 on 2007-01-29
Cool,

I'm sure this will help people using that device.

---

