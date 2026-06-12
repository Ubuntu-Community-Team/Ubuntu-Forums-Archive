---
title: "Internet sharing, 2 ubuntu 10.04 computers through 1 modem/router"
date: 2011-03-03
forum: General Help
---

### Post by igrac777 on 2011-03-03
Hello,
I'm a Ubuntu newbie, and I have a problem.
I have 2 computers, 2 compatible LAN cables and 1 modem (Kasda wired modem).
Both computers are connected to modem, every computer with one LAN cable. I've managed to make pppoe internet connection for my first computer and it works fine. The second computer is connected to the modem, via LAN cable. I would like to know how can I connect the other computer to internet? 

I had Windows Xp on the first computer and Ubuntu on the second before, and the internet worked fine with every computer connected to one modem.
Now when I have Ubuntu on each computer, the same thing doesn't work.

---

### Post by oliwek on 2011-03-03
you should connect to internet, giving your adsl user name and password (from your Internet Access Provider), through your router interface, then any computer can connect to internet ; there should be a user guide in pdf for your router, google its model (name + pdf). You connect to your router typing its IP (192.168.1.1 probably)

pppoe settings is not done in ubuntu, but in the router ;)
There is probably an "easy setup"/"wizard" to guide you, when connected with your browser to the router itself

---

### Post by oliwek on 2011-03-03
from this page [http://webcache.googleusercontent.com/search?q=cache:http://www.enemies.org/2008/01/10/kasda-modem-router-mode/](http://webcache.googleusercontent.com/search?q=cache:http://www.enemies.org/2008/01/10/kasda-modem-router-mode/), I conclude you have to :

Open a browser and type the following URL: [http://192.168.1.1](http://192.168.1.1)
Wait for a while and a Popup Dialog box will appear asking for username and password. Type in the following:
Username: user
Password: password


then try to find this "easy setup"

edit : when the router is set, you'll have to setup ubuntu back to default for internet connexion (through LAN, no pppoe settings in ubuntu), or you'll have no internet anymore on this PC...

edit 2 : [COLOR="Red"]I suppose you have a router-modem[/COLOR], and not a simple modem (PCs are connected to LAN 1 and LAN2 in the back of the device): check this please ; if you had a simple modem, then you would have to configure 1 PC to internet, and the second would connect to internet through the first PC (this first PC must be ON all  the time to keep internet access, and needs 2 LAN cards : 1st connected to the modem, 2nd to 2nd PC) -> better to get a router (any PC can accesss the net even if the 2nd PC is OFF)

---

### Post by igrac777 on 2011-03-03
Thank you for your answer. 
I remember that 192.168.1.1 is the way that I can connect to my router, but unfortunatelly it doesn't work :(.
When I type that in my browser (the connection to internet was shut down before that) nothing happened, my browser couldn't open my modem's settings!

I don't know what to do!

---

### Post by oliwek on 2011-03-03
try to reset your router (there is probably a button to do this in the back of the device), then retry 192.168.1.1

and tell us the result

you are positive that you have a modem-router (not a simple adsl modem), don't you?


by the way, if you have a modem-router, and you have access to internet having set up pppoe details in ubuntu, that means you use your router as a simple modem (in "bridge mode"), then the link I have given above explains how to put your router back to router mode : [http://webcache.googleusercontent.com/search?q=cache:http://www.enemies.org/2008/01/10/kasda-modem-router-mode/](http://webcache.googleusercontent.com/search?q=cache:http://www.enemies.org/2008/01/10/kasda-modem-router-mode/)
> [COLOR="RoyalBlue"][I]
KASDA

Here is a simple step by step instruction to turn your KASDA ADSL modem from Bridge mode to Router mode. How to turn KASDA ADSL Modem into Routing Mode.

Add a Root User

Open a browser and type the following URL: [http://192.168.1.1/hag/emweb/PopOutUserAdd.htm](http://192.168.1.1/hag/emweb/PopOutUserAdd.htm)
Wait for a while and a Popup Dialog box will appear asking for username and password. Type in the following:
Username: user
Password: password
Now add user page should appear. Add any username you like but make sure the user type is &#8216;ROOT&#8217;
Close your browser now. Please do not switch off the modem as doing so you would lose all steps done from 1 to 3
Open browser and type in [http://192.168.1.1](http://192.168.1.1)
Now Key in the username and password that you have created in step 3
Go the Admin Tab and select the Commit and Reboot, now click the button commit. This should save all the work done from steps 1 to 7
Turn KASDA into Routing Mode

Go to the Home Tab and click on the Quick Configuration
Make sure the following Options are filled in accordingly:
ATM Interface: 0
Operation Mode: Enabled
Encapsulation: PPPoE
LLC VPI: 0
VCI: 35
Default Route: Enable
PPP Username: yourname@streamyx
Password: your TMNet Streamyx password
Click the Submit button
Next, Select the System Mode. Make sure that all settings (radio button) are set to disable. Click the submit button
Go to the Services Tab
Click the NAT. NAT Options: NAT Global Info. Select the Enable radio button option and click the Submit button
NAT Options: NAT Rule Entry. Click on the Add button. Key in the following:
Rule Flavor: NAPT
Rule ID: 1
IF Name: ALL
Protocol: ANY
Local Address From: 192.168.1.0
Local Address To: 192.168.1.255
Click the Submit Button
Select the DNS
Click on the Enable radio button
Click on the Submit button
Go to Admin Tab
Select the Commit and Reboot
Click on the Commit button
Wait for the screen to refresh and Click on the Reboot Button. Now we are done. Now you can try to open a new browser and you should be able to browse the internet without using the PPPoE dialer from your PC.[/I][/COLOR]

---

### Post by igrac777 on 2011-03-03
I'm sorry but I restarted my Kasda like you said, and I've tried to go to [http://192.168.1.1/hag/emweb/PopOutUserAdd.htm](http://192.168.1.1/hag/emweb/PopOutUserAdd.htm) but it gave me an ERROR 109.

I tried also 192.168.1.1 and stil ERROR 109.

I did this after I've used poff dsl-provider, and then after pon dsl-provider and in both cases nothing :(! What now?

---

### Post by igrac777 on 2011-03-03
And i did the ifconfig and the result is this, maybe it helps:

eth0      Link encap:Ethernet  HWaddr 00:50:8d:a8:96:42  
          inet6 addr: fe80::250:8dff:fea8:9642/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:223290019 (223.2 MB)  TX bytes:19157238 (19.1 MB)
          Interrupt:22 Base address:0xb400 

eth1      Link encap:Ethernet  HWaddr 00:0e:f4:04:98:04  
          inet6 addr: fe80::20e:f4ff:fe04:9804/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2989 (2.9 KB)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51389 (51.3 KB)  TX bytes:51389 (51.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:93.138.3.220  P-t-P:172.29.252.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:553092 (553.0 KB)  TX bytes:157148 (157.1 KB)

---

### Post by igrac777 on 2011-03-03
Problem solved, Thank you all!

---

