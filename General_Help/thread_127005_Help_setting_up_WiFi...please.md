---
title: "Help setting up WiFi...please?"
date: 2006-02-07
forum: General Help
---

### Post by Leiki on 2006-02-07
Of course, I searched other threads and none of them helped...

I have an internal Atheros AR5005G wireless card, and I don't know if Ubuntu detects it or not. I go to System > Administration > Networking and it shows me  a wireless, ethernet, and modem connection. Does that mean it detects my wireless card (plus all of my other connections)? If so, then I type in my network name and my WEP key and click OK. It then shows a pop up, loads for a minute, and then I click OK on the main window and that loads for a while...now what? It does nothing.

And what about these screens at the top of the screen (indicating a connection)? It says the connection name is "lo" or something, and fluxuates between "Idle" and "Sending/Receiving" status. What's that all about?

Your help is GREATLY appreciated. Thank you.

---

### Post by BlacKoffee on 2006-02-08
Yeah, I'm having problems with that too. I'm fairly new to linux, and this is my first time using Ubuntu. A friend of mine gave me the install disk and I am definately hooked. 

I'm using a Belkin USB wireless adapter for my WiFi. My network is actually based on the Windows computer. I can't get the rest of the guys I live with to see the Linux light heh. 

I need to know how to make sure its registering my USB adapter and how to connect it with my Windows network.

/Help

Koffee

---

### Post by adi-beg on 2006-02-08
To Leiki: Yes, your wireless card is detected. You need to know if you use dhcp or static ip adress, your essid and enc key.

Screens on the top right side indicate connections. When you click on them, you can switch between your active connections to see status. Connestions can be lo, wlan0, eht0...

---

### Post by nanotube on 2006-02-08
hi
just select another interface from the list. the 'lo' interface is your loopback connection (a fake interface that is used for computer to communicate with itself). find a real-looking interface in the list (something like eth0, or anything else besides lo), and check.
if you want to try the commandline, open up a terminal, and type "ifconfig"
that will show you all the info about all your interfaces. also, command "iwconfig" will tell you all the info about your wireless cards.

---

### Post by Leiki on 2006-02-08
Thank you so much for your help, everyone. I changed my connection to ath0 and it displays the connection strangth and says it's connected! But whatever URL I type in Firefox it says "Looking for www.google.com..." for a long time and then says it can't be found! Oh, what is going on? :(

---

### Post by adi-beg on 2006-02-08
What belkin adapter? Which chipset? I think you need to use ndiswrapper to configure your adapter and windows drivers (.inf and .sys files).

---

### Post by BlacKoffee on 2006-02-08
It's not an internal chip, its an external USB adapter. Meh, worse comes to worst, I can always get an internal PCI card :)

What is ndiswrapper?.

Koffee

---

### Post by gosh on 2006-02-08
I think you might find a lot of answers to your questions on the Official Wiki. Search for Wifi and Ndiswrapper.

---

### Post by BlacKoffee on 2006-02-08
Thanks :) I'm actually working on it right now. Now if I could just get the make install command to work heh

Koffee

---

### Post by Leiki on 2006-02-08
Ok, so I have ndiswrapper, so how do I install the driver? I coped the driver from Windows and put it on Ubuntu, but I guess it has to be an inf file?

---

### Post by Leiki on 2006-02-09
I don't want to give up! PLEASE HELP!

---

### Post by gosh on 2006-02-09
[QUOTE=BlacKoffee]Thanks :) I'm actually working on it right now. Now if I could just get the make install command to work heh

Koffee[/QUOTE]

try:
sudo make install

---

### Post by drakeoutlaw on 2006-02-09
[QUOTE=Leiki]I don't want to give up! PLEASE HELP![/QUOTE]

Relax. You're making progress! So far your wireless interface (ath0) has found the the wireless access point which is why it is showing you your connection strength. What's happenning is that your connection is not being configured because of WEP or WPA encryption has been activated on your access point.

The easiest way to get things going is to disable all encryption on your wireless router. Then type "sudo /etc/init.d/networking restart"

The above command will restart your networking subsystem. As your builtin wireless card connects it will recieve configuration parameters from the router and will be assigned an ip no. and given a default route. As currently configured your wireless connection is not getting this info now.

Your wireless connection should become active.

Once you get your wireless connection working you can search elsewhere in the Ubuntu forums for excellent instructions on how to get encryption working.

Remember: small steps

Learn and Enjoy

Regards, Drake

---

### Post by techflavor on 2006-02-09
Leiki, it seems Ubuntu is already seeing your Atheros card.  If you type iwconfig, you should see something about ath0.  

If you don't have WEP or WPA turned on your router, then try the following commands:

sudo iwconfig ath0 essid "linksys"
sudo ifconfig ath0 up
sudo ifup ath0


The first command tells the wireless card which wireless network to connect to (change linksys to your routers SSID).  The second command tells Ubuntu to activate the wireless connection.  The third command attempts to get an IP address from DHCP (that is if you have DHCP enabled on your router).

If you want to scan for available networks, make sure the wireless device is turned on (sudo ifconfig ath0 up), then do:

sudo iwlist ath0 scan


Let me know if this helped.  FYI, madwifi drivers come preinstalled in Ubuntu 5.10 (the drivers used by the Atheros cards).  

For the other person in the thread with problems, you will need to read about ndiswrapper and how to get it working with your wireless device.

---

