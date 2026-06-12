---
title: "Usb adsl modem"
date: 2010-12-31
forum: General Help
---

### Post by pssalman on 2010-12-31
i have a Conexant AccessRunner ADSL WAN USB Adapter and i want to switch from windows to ubuntu! i have installed along side windows and i don't know how can i get my ADSL adapter to work under ubuntu? any help please?

---

### Post by pssalman on 2011-01-01
59 views no solution... please help... 
when i use lsusb in the shell the system reads my modem 
Bus 004 Device 002: ID 0572:cb00 Conexant Systems (Rockwell), Inc. ADSL Modem

i have followed the steps in this tutorial [http://www.uluga.ubuntuforums.org/showthread.php?t=1597605](http://www.uluga.ubuntuforums.org/showthread.php?t=1597605)

and after finishing i installed gnome ppp to make a dial connection... but it doesn't detect my modem... please help

---

### Post by dcstar on 2011-01-01
> **pssalman said:**
> i have a Conexant AccessRunner ADSL WAN USB Adapter and i want to switch from windows to ubuntu! i have installed along side windows and i don't know how can i get my ADSL adapter to work under ubuntu? any help please?

What happened when you tried the Network Manager?

---

### Post by pssalman on 2011-01-01
gnome ppp doesn't detect my usb modem... how can i make a connection.. the red light on the modem is steady that's how i know that my modem is ready to make a connection... but if gnome ppp doesn't detect my modem... what alternative can i use to detect my modem to make a dial up

---

### Post by dandnsmith on 2011-01-01
I'm not too surprised that that thread didn't give the solution desired - it is written for a 56K dialup modem using POTS.

That said, I don't know enough about the connection methods for ADSL to help get it working, as I've always used a router connected to my PC via ethernet (or wireless) and that handles the setting up the connection.

I do have the passing acquaintance of a linux enthusiast who supplied his own router to a charity with which I am connected rather than face trying to get a Speedtouch modem to work.

---

### Post by pssalman on 2011-01-01
what shall i do? can u get me a solution?

---

### Post by dandnsmith on 2011-01-01
A quick Google search threw [this help](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-usb) up. There might be some leads there.

Good Luck

---

### Post by translator125 on 2011-01-09
Hello pssalman:

To connect to the Internet, follow these steps:

1. Go to Applications --> Ubuntu Software Center and type 'br2684ctl' in the search field. Install the utility.

2. Open a terminal by going to Applications --> Accessories --> Terminal and type (or copy-paste from here): 
sudo br2684ctl -c 0 -a 1.32
(For your information, 1 and 32 are the VPI and VCI values respectively.  You may need to use different values, depending on your WAN  configuration settings.)

3. Open another terminal and type:
sudo ifconfig nas0 192.168.1.1 netmask 255.255.255.0
(192.168.1.1 is the IP address and 255.255.255.0 is the (sub)netmask  under your LAN configuration settings. Please feel free to use different  values, depending on your LAN configuration settings.)

You will be prompted with several Yes/No options one after the other. Select 'Yes' each time.

In the same terminal, type:

sudo pppoeconf

Enter your user ID and password, when prompted.

4. Open your browser and voilà! You're connected to the Internet.

5. You may close both the terminals now, though a process may still be running in the first terminal.

Note: You will have to follow the same procedure each time you restart your system.

All the best!

- translator125

---

### Post by IcarusR on 2011-01-10
translator125


> sudo pppoeconf

This will not work as ppoe is 'point to point over ethernet' & the OP has a usb modem.

---

### Post by translator125 on 2011-01-10
I know that we're talking about a USB modem here. That's precisely why at the very outset I suggested to download and install the 'br2684ctl' utility. The utility will create a virtual ethernet interface (say, 'nas0') and use ATM bridging to connect it with eth0 or eth 1.

The method works great for me. Why not try it out yourself?

Good luck :)

- translator125

---

