---
title: "Please help me I'm desperate"
date: 2009-12-17
forum: General Help
---

### Post by mommamac72 on 2009-12-17
Hello,
I have Ubuntu/Linux newly installed on my laptop. My fiance had to go out of town and I am trying to help him remotely get connected to the wireless internet at his hotel. We have tried the ifconfig and it comes up no connection. I know about a week ago i was goofing with the internet options on this computer and it came up with a list of wireless connections in my area but all were locked so I left it. Now it will show the list of previous wireless networks but will not refresh to show available networks where he is. How do I get the wireless to connect???
We have tried....

Open a terminal so you have the command line and run this command:

sudo dhclient

You will need to enter the root user password which is the same as the first user on the laptop.									
and...

dhclient will try to pick up an IP address from the server. If this does not work in a motel, you may have to talk to them to see if you need to add a name for ssid.

Also you can list what your system picks up with:

sudo iwconfig									

searched several forums and also tried 
  ifdown eth1

nothing seems to be working....... Please can someone help so our 6 children can see their dad. Been trying for 2 days now with no success only frustration!!
Thank you

---

### Post by CharlesA on 2009-12-17
Nothing listed in network manager?

---

### Post by paradigm2 on 2009-12-17
I've ran into something weird like this on Karmic (9.10) where it would no longer show the available networks.  Have you tried:

1. Disable Wireless.
2. Wait five seconds.
3. Disable Networking.
4. Shutdown (Not hibernate or Standby)
5. Boot.
6. Enable Nwtworking (if not enabled)
7. Enable Wireless (If not enabled)

Does it show something now?

---

### Post by synapsys on 2009-12-17
You should be able to see a list of available wireless networks by clicking the network manager (upper right hand corner next to volume control)

Is that what's showing the "old" wireless networks?

If it is, try:

```
sudo /etc/init.d/networking restart
```

then try again.

---

### Post by Leppie on 2009-12-17
there's also a [WifiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo").

---

### Post by mommamac72 on 2009-12-17
we have tried to enable wireless and it came up with the original list that came up when I tried it at home and when he tried to input the network name for the hotel he is at with the password given it does not allow him to connect.

the dhclient says
DHC disc on 255.255.255.5.. port 67 interval.... then there are a bunch of different numbers then it says no dhc offers recieved. no persistant database-sleeping

then waiting for command

---

### Post by synapsys on 2009-12-17
what is the output of 

```
iwconfig
```

---

### Post by mommamac72 on 2009-12-17
the iwconfig says there is no connection.

as for network manager it is showing network connections from by our home when I first tried to find out if wireless was working and will not load new list of networks for where the laptop is now

---

