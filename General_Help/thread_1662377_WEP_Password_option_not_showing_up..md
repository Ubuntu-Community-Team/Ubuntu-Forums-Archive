---
title: "WEP Password option not showing up."
date: 2011-01-08
forum: General Help
---

### Post by Ramirez! on 2011-01-08
In the wireless network icon on the menu bar, I try to log into my home network and it won't let me connect.

According to the website, it is a WEP Passcode.

All I see is WEP 128-Bit and WEP 128-bit Hex and ASCII

Help.

---

### Post by Bucky Ball on 2011-01-08
Right click the network icon, 'Edit Connections', go to wireless and check the details are correct there (including your WEP password and type).

What machine, Ubuntu release (10.10, 10.04 LTS) are you using? Do you know what wireless card you have?

When you say the website says it is WEP passcode, what website? The security key is set on your AP (Access point, router), NOT anywhere on the net. To get to the config, open Firefox and put in the IP address of your router (it would be in the manual, something like 192.168.0.1) and that will take you to the  configuration.

Set ESSID (network name), and security key (WEP, WPA, whatever you decide to use). Under 'IPv4' tag, make sure it is set to 'Automatic (DHCP)' or 'Manual if you are using a static IP address.

The make sure the info on your machine matches the info on your router by performing my first instruction; 'Right click the network icon, 'Edit Connections''

Try to include as much info as possible when posting a new thread. ;)

Welcome to the forums and Ubuntu!

---

### Post by Ramirez! on 2011-01-08
I'm using 10.10. And my card is an Apple Airport card.

---

### Post by Bucky Ball on 2011-01-08
Please try some of the things in my last post. I have edited it. ;)

---

### Post by Ramirez! on 2011-01-08
I apologize. My tiredness got the best of me. The "website" I was referring to was the Wireless Network Configuration website you mentioned earlier. I logged onto it using my Mac partition.

I'm running on a PowerPC PowerMac G4 Tower. With the Apple Airport card.

My problem is when I boot into Linux, my card can detect the wireless networks, I just can't connect with them because they are encrypted with a WEP Passcode. When I try to find it in the drop-down menu, it doesn't show. I will try to provide a screenshot.

---

### Post by Bucky Ball on 2011-01-08
What is the error message *exactly*?

---

### Post by Ramirez! on 2011-01-08
There is no error message. When I try to connect to the network, it asks me for an encryption type. WEP wasn't there, so I chose Dynamic WEP and WEP 128-bit. It tries to connect, but the dialogue box tells me that the password is invalid.

---

### Post by Bucky Ball on 2011-01-08
Does the one you're putting in match the password (security key) in your router???

> ... the dialogue box tells me that the password is invalid.That's what I'm after. ;)

As I said, set up the config on your router, or check how it is set. Change the security key there if you have to so then you will KNOW that you are putting in the right one.

---

### Post by mini260462 on 2011-01-08
Hi, I am having a similar problem but I cannot see where I can post my own thread although i am allowed!!!

I have an ASUS 4g with ubuntu netbook on and although it says connected it won't load any webpages. I can get on with mobile broadband but signal is very weak??

So for hijacking this post :confused: I'm new!

Thanks
Bec

---

### Post by Bucky Ball on 2011-01-08
Hi Bec. Go to the appropriate forum category and above the first post on the left is a big button saying 'New Thread'. ;) You can't miss it, and yes, please start a new thread dealing with your issue. :)

Welcome to the forums!

PS: Reread this thread and try some of the instructions I have already posted here.

---

