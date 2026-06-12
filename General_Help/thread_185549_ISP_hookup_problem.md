---
title: "ISP hookup problem"
date: 2006-05-31
forum: General Help
---

### Post by crd6640 on 2006-05-31
I am having problems setting up my internet ISP connection.  I have read the howtosetupadialup (I think that's the name) but anyway while I can get modem to dial and apparently connect and then hangup by using the admin networking, I have been unable to get it to actually hook up to the ISP (netzero).  It acts as if it searches for an account, doesn't find it and then hangs up.  I know the netzero account works as I can loginto it on another machine.  Here is what I don't understand --- I have the access phone number, username and password, and have entered these into the Network settings using the properties tab.  However nowhere have I entered the name or URL for Netzero and since I'm sure ( believe) the access numbers are used by several ISPs then I don't see how it knows who my ISP is.  What do I need to do to make this thing work?  I have also tried setting up by using pppconfig and then tried connecting using pon but while this also physically gets to the modem it does not seem to dial but just goes thru the connect tries at different speeds.  Can one of of you Ubuntu gurus tell me what I'm doing wrong?  I also tried to install Kppp by sudo app-get install kppp but that didn't work.  Would appreciate any help I can get.  I'm sure this is a simple fix.  By the way my modem is an external modem (us robotics) on the /dev/tty0 port. Thanks

Well, since no one else answered I kept trying but still with no success.  I believe I have answered at least part of the problem.  First, I realized that the user name also should contain the ISP provider.  Unfortunately that hasn't helped -- I still have the same results under the admin/networking/ All info was entered into modem section and then activate the modem link -- it dials -- apparently hooks up (from lights on modem) and then hangs up the phone.  I thought for sure the putting the ISP name on end of my user name would work. I have not altered my DNS files - Should they be?  Second problem -- I have tried again to use the wvdial, and pon and also without success --- I never dial out until after it tries to hook up and I'm not sure even where it dials -- it just comes back with a voice msg that says "if you are having trouble dialing etc.  Maybe if someone is using wvdial, pppconfig and pon to hookup, you would share your wvdial config info and  your pppconfig info -- especially if you are using a U.S. Robotics modem.  Thanks

---

### Post by darthchaosofrspw on 2006-06-24
You need to try to get the Netzero debian file and install it like this :

sudo dpkg -i netzero.deb

The next step is VERY important. In order to get the NetZero dialer software to work with Ubuntu, you MUST use the Synaptic Package Manager or apt-get to download and install the Java 2 Runtime Environment (j2re). The NetZero software depends on j2re. Without j2re, the NetZero dialer will NOT work. To download j2re, you have to enable the Multiverse repositories which are listed at [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) and then once the apt sources are updated, you can download and install j2re...easiest way is to use Synaptic Package Manager and search for anything that has j2re.



Then you need to make a link on your desktop to the NetZero dialer. For this, you need to have the NetZero shortcut point to the following command :

sudo bash /opt/nzclient/runclient.sh

If that doesn't work, try running "sudo bash /opt/nzclient/runclient.sh" in a terminal window. It should work.

---

