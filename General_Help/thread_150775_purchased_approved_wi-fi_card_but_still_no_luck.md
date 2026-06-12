---
title: "purchased approved wi-fi card but still no luck"
date: 2006-03-26
forum: General Help
---

### Post by rhomsy on 2006-03-26
I purchased the Belkin wi-fi model number F5D7010. On the ubuntu list ([HTML]https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards[/HTML]) it says that it just works without any configuration.  Well, it doesn't just work.  I have breezy installed and it sees the wi-fi networks but when I select the network, and tell it to use dhcp, and put in the WEP, it doesn't work.  WHY IS USING WI-FI SO HORRIFIC IN UBUNTU.  I just returned my last wi-fi card at the store today to get this one because the last one didn't work.  What do I do now?

Something so simple as wi-fi shouldn't be so difficult to get working in a desktop os.  This really needs to be improved in Dapper.

---

### Post by towsonu2003 on 2006-03-26
Check out the following pages in order:

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)
[https://wiki.ubuntu.com/WifiDocs/Device/F5D7010](https://wiki.ubuntu.com/WifiDocs/Device/F5D7010)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

you will want to read these in full before doing anything. The third page will help you make sense of the second page. The first page uses rt2500 module while the others use ndiswrapper. The first one should make it work. If it doesn't, use ndiswrapper to make the thing to work. Also, file a bug to Malone - Ubuntu for your card.

Also, change that wiki page you posted so that others know your card doesn't work out of the box.

---

### Post by rhomsy on 2006-03-26
[QUOTE=towsonu2003]Check out the following pages in order:

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)
[https://wiki.ubuntu.com/WifiDocs/Device/F5D7010](https://wiki.ubuntu.com/WifiDocs/Device/F5D7010)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

you will want to read these in full before doing anything. The third page will help you make sense of the second page. The first page uses rt2500 module while the others use ndiswrapper. The first one should make it work. If it doesn't, use ndiswrapper to make the thing to work. Also, file a bug to Malone - Ubuntu for your card.

Also, change that wiki page you posted so that others know your card doesn't work out of the box.[/QUOTE]


Well, I was in the middle of performing the steps outlined in your second url, and it continues to say "hardware present: no".  I'm stuck, and I have no wi-fi.  Someone please help.

---

### Post by rhomsy on 2006-03-26
Well, I went to Belkin's website.  Their "drivers" and their website are about as useless as a screen-door on a submarine.  The drivers are all windows exe files, so I can't even use the inf file.  Do I have to return this wi-fi card now too?  Should I even try a third one?  The ubuntu wi-fi compatability list said that this works "out of the box", so my confidence is dropping.

---

### Post by stabface on 2006-03-26
i have the same card popped it in after i installed the system and it loaded and worked right away no problems at all

---

### Post by towsonu2003 on 2006-03-26
[QUOTE=rhomsy]Well, I went to Belkin's website.  Their "drivers" and their website are about as useless as a screen-door on a submarine.  The drivers are all windows exe files, so I can't even use the inf file.  Do I have to return this wi-fi card now too?  Should I even try a third one?  The ubuntu wi-fi compatability list said that this works "out of the box", so my confidence is dropping.[/QUOTE]
did you file a bug report? the compatibility list is put together with Ubuntu users as far as I know, not by the developers. 

See this list for a list of drivers, and find your own driver: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Use this to uninstall the driver that's not working for you (hardware present: no): sudo ndiswrapper -e <driver>

As you try out different drivers using ndiswrapper, uninstall one before installing the next. 

as per stabface's comment, before tarting to try out drivers: try removing dniswrapper (see ubuntu wiki page), reboot computer, make sure  ndiswrapper is not loaded (the command lsmod | grep ndiswrapper will give no output if ndiswrapper is not loaded), and pop in the card and check if it starts working. After 8-10 seconds popping in the card, type these two commands: ```

dmesg | tail
tail /var/log/messages
``` to see if it gives errors (post here and to your bug report) or info. check Networking Settings (System>Administration) to see if the thing is in there (either as wlan0 or ra0).

PS. The drivers are a mess bc manufacturers do not write drivers for linux. Unfortunately, Ubuntu has nothing to do with that. If Ubuntu was at fault, it might be easier to fix...

---

### Post by rhomsy on 2006-03-26
I couldn't find how to get rid of ndiswrapper in the wiki.  

When I look in Networking Settings, I seek the card as ath0.  When I configure it, I can see my wi-fi network.  I tell it to use dhcp and I have no password, and it activates (takes awhile), but it doesn't work.  So, I guess I don't know where my problem is.  The card *is* seen, however it just doesn't work.  I've tried it on other wi-fi networks too, so there is no problem with mine.

BTW, I'm sorry if my prior posts were a little rude.  I've just been so frustrated by this problem.  I certainly don't blame ubuntu's developers.

---

### Post by towsonu2003 on 2006-03-26
[QUOTE=rhomsy]The card *is* seen, however it just doesn't work.  I've tried it on other wi-fi networks too, so there is no problem with mine.
[/QUOTE]
Let's try the command line. But first, remove ndiswrapper so we know there is no conflict with it. I am assuming that, as your ndiswrapper install didn't work (hardware present:no), it is not the driver used for your wifi. 
```

sudo modprobe -r ndiswrapper 
sudo apt-get --purge remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
```

Now, make sure your access point is broadcasting its ESSID and it has no passwords or anything for access (wep, wap etc). 

1. open a terminal and type tail -f /var/log/messages Do not close that window and monitor the output. Error messages: please post here. 

2. Let's connect
```
sudo -i #this will give you root priveleges until you "exit", so be extremely careful!)
iwlist ath0 scan #this will give you a list of accessible access points. Choose yours and use below
iwconfig ath0 ESSID essidhere
iwconfig #Check out the output to see that ath0 has your ESSID correct. If it has not, there is a problem. go back to "iwlist ath0 scan" and try again)
killall dhclient #Disconnect from any networks
ifconfig eth0 down #Take down ethernet card so there is no conflict there either. You'll loose network connection at this point. You can get it back from Networking Settings (System>Administration>)
ifconfig ath0 up #Activate ath0 network interface
dhclient ath0 #this will connect you and inform you your IP address assigned
exit #don't forget to exit from root "mode"
```

3. Do you have a firewall installed? Firestarter? Guarddog? Make sure the firewall knows that you are now using ath0 as your network interface. 

4. You are supposed to be connected now. Did it work? Any error messages, please post here. Also, if you get error messages, post output of ```

lsmod | grep ndiswrapper
lsmod | grep 2.00
sudo iwconfig
sudo ifconfig
```

Good luck ;)

---

### Post by ectospasm on 2006-04-05
I'm having a similar problem with my F5D7010.  Ubuntu recognizes the card, and I can activate ath0, except I get a bogus IP address;  I get 192.168.1.x, when the access point should be returning a 192.168.0.x address.  It's weird, because the internal wifi nic (Prism2, I believe) gets the correct IP address, and both nics are configured with the same ESSID.  I haven't tried a scan with iwlist yet, maybe I'll try that.

---

### Post by towsonu2003 on 2006-04-05
[QUOTE=ectospasm]I'm having a similar problem with my F5D7010.  Ubuntu recognizes the card, and I can activate ath0, except I get a bogus IP address;  I get 192.168.1.x, when the access point should be returning a 192.168.0.x address.  It's weird, because the internal wifi nic (Prism2, I believe) gets the correct IP address, and both nics are configured with the same ESSID.  I haven't tried a scan with iwlist yet, maybe I'll try that.[/QUOTE]
it may well be possible that you are connecting to an access point with the same name. scanning would tell you about that. 

can you connect to the internet (browse pages) with the bogus ip? which driver are you using? did you try the advice given in this post? did you try other drivers for this device, if you are using ndiswrapper? 

also, try a setup in which access point gives you one and only one ip address (not "dhcp" -which gives random ip addresses upon connection, but I'm not sure if you can do that with wireless access points?? -I never had one :) ) Than you can pass that information to the card and try to connect (again, not sure if this can be done).

---

### Post by Lisa_T on 2006-04-05
I have the Belkin card referred to in the first post- Ubuntu doesn't even recognise the card as being present! However, i didn't even bother installing the card under windows- just plugged it in and booted up linux. Might that have anything to do with it? *grasping at straws*

---

### Post by towsonu2003 on 2006-04-05
[QUOTE=Lisa_T]I have the Belkin card referred to in the first post- Ubuntu doesn't even recognise the card as being present! However, i didn't even bother installing the card under windows- just plugged it in and booted up linux. Might that have anything to do with it? *grasping at straws*[/QUOTE]
not that it really matters but, try installing it in windows. that way, you can be sure that it's not a hardware failure... which driver are you using for that thing? 

I guess someone has to change the wiki accordingly and file a bug report. but that someone has to be the one who have the actual problem ( ;) )

---

### Post by shamrock_uk on 2006-04-05
It's best not to rely on the wireless wiki too much - I've bought three cards based on its advice and only one has worked as described, the rest have all required ndiswrapper. I can never seem to log on successfully to the wiki to edit the page though :(

---

### Post by towsonu2003 on 2006-04-05
[QUOTE=shamrock_uk]I can never seem to log on successfully to the wiki to edit the page though :([/QUOTE]
tell me which part to edit exactly and what to write (exactly) and I'll do that for you in a bit.

PS. tell me = post here ;)

Note: For any non-working hardware, I prefer filing a bug as well.

---

### Post by ectospasm on 2006-04-05
[QUOTE=towsonu2003]it may well be possible that you are connecting to an access point with the same name. scanning would tell you about that. 

can you connect to the internet (browse pages) with the bogus ip? which driver are you using? did you try the advice given in this post? did you try other drivers for this device, if you are using ndiswrapper? 

also, try a setup in which access point gives you one and only one ip address (not "dhcp" -which gives random ip addresses upon connection, but I'm not sure if you can do that with wireless access points?? -I never had one :) ) Than you can pass that information to the card and try to connect (again, not sure if this can be done).[/QUOTE]

I can plug in a correct IP, but I would rather use DHCP.  iwlist ath0 scan only shows one access point.  I think the problem is coming with DHCP, it just get's a completely wrong network address.  If I use DHCP to get the address, I have to manually add the "bogus" gateway to the DNS list, and then it seems to work.  

I don't use ndiswrapper (nor do I want to, I hear it's horrible if you want to do low level stuff like netstumbler).  The wireless access point provides the correct IP to the builtin wlan nic.  I'm just at a loss as to why I get a bogus address with the Belkin nic...

---

### Post by towsonu2003 on 2006-04-05
[QUOTE=ectospasm]The wireless access point provides the correct IP to the builtin wlan nic.  I'm just at a loss as to why I get a bogus address with the Belkin nic...[/QUOTE]
At this point, seeing that there are 15 (now 16) posts in here, I doubt there will be anyone *new* lookin here to offer help. You might wanna follow the following steps:
1. Wait for new posts offering help with this for 3-4 days
2. Open a new thread with a very specific title (problem + hardware)
3. If that's no help, file a bug report to ubuntu malone. 

Unfortunately, I have no idea what the problem is.

---

### Post by dpower on 2006-04-24
Looks like it depends *which* belkin F5D7010 card you bought. Version 3000 and above use a different chipset. Unfortunately I'm still trying myself... this is all a bit silly. This is a basic function of any OS. 

Dave

---

