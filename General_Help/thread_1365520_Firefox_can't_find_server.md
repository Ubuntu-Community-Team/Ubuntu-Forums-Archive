---
title: "Firefox can't find server"
date: 2009-12-27
forum: General Help
---

### Post by gap101 on 2009-12-27
After an update a week or so ago, Firefox (Version 3.5.5 / for Ubunto canonical - 1.0) cannot resolve web addresses. I can ping other computers by IP address on the network and can access my local router using it's IP address. My homepage is set to [http://www.al.com/](http://www.al.com/) I cannot get it that way but can get to it by typing in the IP address; [http://69.2.101.51/](http://69.2.101.51/) This is likely a Firefox / DNS issue but I have no clue about troubleshooting.

---

### Post by jonest1 on 2009-12-27
Can you resolve hosts outside of firefox?  In other words, is the problem firefox or more widespread?

Type the following command to test.
```
host www.yahoo.com
```
You can try some other hosts as well.  If they resolve, then the problem is specific to firefox.  If not, then it's a resolve issue with the OS.

Check your /etc/resolv.conf file as it should have your DNS servers populated.  You can check the settings in network manager as well.  

I had a problem where I was getting the IP address of my router as a DNS server, but the router was extremely slow in translating the queries.  I manually configured my PC to use the ISP DNS addresses and all has been well.

If your problem is firefox specific, I'm not sure on how to properly assist.

You may want to try to rename ~/.mozilla to ~/.mozilla_old or something similar and try again.  There could be something wrong in your firefox profile, but you'd need better expert advice for any detailed troubleshooting.

---

### Post by Nicolas.Perrault on 2009-12-27
You may like firefox, but you may want to try out Google Chrome. Works out perfect for me :D

[http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha](http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha)

Hope I helped!: :)

---

### Post by gap101 on 2009-12-27
Installed Google Chrome (no small feat, with the network issue) but it had the same problem. Found the problem. System has switched to Ethernet: Auto Eth0. Switched it back to Wired Connection 1 and bingo - my Ubuntu machine is back on the Internet. Thanks for the help. I will explore Google Chrome.

---

### Post by lovinglinux on 2009-12-27
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

