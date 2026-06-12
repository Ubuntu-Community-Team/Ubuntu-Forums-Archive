---
title: "Ah No Internet!!!"
date: 2006-05-18
forum: General Help
---

### Post by That Guy X on 2006-05-18
Hi , I installed ubuntu and everything went fine accept i cant go on the internet. When I went to network connections it said eth0 active and everything looked fine. Whenever I try loading a page like google it said server not found. Is there some sort of firewall im supposed to turn off or something. :confused:

---

### Post by dirwood on 2006-05-18
open a terminal and run **ifconfig**
check to make sure it's showing what it should for your network/connection.

---

### Post by dg_w on 2006-05-18
Nope 

how are you connecting   
From the terminal can you ping 158.152.1.43 ? if so it is a DNS isue
check your /etc/resolv.conf  
Usualy
nameserver "your router"
nameserver "your isp dns server"

Also is the default gatway set to your router IP ?

---

### Post by That Guy X on 2006-05-18
When i tried /etc/resolve.conf it said command not found  (total noob)

Everything else looked ok  ](*,)

---

### Post by dirwood on 2006-05-18
resolv.conf isnt an executable, its a plain text file.
try:
nano /etc/resolv.conf

note, there is no "e" on the end of resolv

---

### Post by Slim Odds on 2006-05-18
[QUOTE=dirwood]resolv.conf isnt an executable, its a plain text file.
try:
nano /etc/resolv.conf

note, there is no "e" on the end of resolv[/QUOTE]

"cat /etc/resolv.conf" would be even easier

Output from "ifconfig", "cat /etc/resolv.conf" and "route -n" would be very helpful.

---

### Post by StubornAH on 2006-05-18
I think I am having a similar problem, here is my post: [http://www.ubuntuforums.org/showthread.php?p=1030892#post1030892](http://www.ubuntuforums.org/showthread.php?p=1030892#post1030892)

Someone just suggested it might be a problem with Firefox and IPv6.

---

### Post by That Guy X on 2006-05-18
Ug , for some reason /etc/resolv.conf keeps coming up blank.

I got the copy/paste on here becouse i put it on my flash drive. I cant access this forum from ubuntu so i have to keep coming back to windows.
](*,) 


steve@SUPER-COMPUTER:~$ cat /etc/resolv.conf
steve@SUPER-COMPUTER:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
steve@SUPER-COMPUTER:~$




steve@SUPER-COMPUTER:~$ cat /etc/resolv.conf
steve@SUPER-COMPUTER:~$
steve@SUPER-COMPUTER:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:C6:63:28
          inet6 addr: fe80::213:d3ff:fec6:6328/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)

steve@SUPER-COMPUTER:~$ /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied
steve@SUPER-COMPUTER:~$

---

### Post by dirwood on 2006-05-18
do you connect directly to your cable/dsl modem or through a router?
eth0 is not pulling an IP.

---

### Post by That Guy X on 2006-05-18
I connect directly to a modem/router

---

### Post by dirwood on 2006-05-18
is it a modem, or a router, or a combo device?

---

### Post by That Guy X on 2006-05-18
Its a combo device               westel Adsl modem/router   model 327w

---

### Post by dirwood on 2006-05-18
ok, is this a different network card than you usually use with the modem?

---

### Post by That Guy X on 2006-05-18
What do you mean

---

### Post by That Guy X on 2006-05-18
Its not a card its a modem with a router built into it

---

### Post by dirwood on 2006-05-18
Some internet providers will not give an ip address to a new network card.  If you have multiple computers, and the router is not set up to pull and IP and allow multiple computers to connect to it it would show the symptoms your computer is having.

Try unplugging all computers from the modem, pull the power on the modem for ~1 minute.  Plug your ubuntu computer into the modem, then plug the power back in.  Then check to see if you have internet access.

---

### Post by That Guy X on 2006-05-18
I only have one comp with bolth windows and ubuntu so im useing the same network card and hardware.

---

### Post by dirwood on 2006-05-18
does windows configure your network by DHCP or is it static?

---

### Post by That Guy X on 2006-05-18
Dhcp

---

### Post by dirwood on 2006-05-18
Could you take a screenshot of the configuration screen of your network?

You can get to it by right clicking on the network monitor icon in a panel (if it doesnt show just add it) and choosing configure, choose eth0 and click on properties.

---

### Post by That Guy X on 2006-05-18
[attach]9683[/attach]

[attach]9684[/attach]

[attach]9685[/attach]

[attach]9686[/attach]

---

### Post by dirwood on 2006-05-18
one more screenshot please.

Click on the highlighted entry and choose properties.

---

### Post by dirwood on 2006-05-18
I'm sure this is a PITA, but I'm just trying to help the best I can.

---

### Post by That Guy X on 2006-05-18
[attach]9689[/attach]

---

### Post by dirwood on 2006-05-18
I have to say that I am stumped.
The best advice i could give would be to run the commands:

[I]sudo ifconfig eth0 down
sudo ifconfig eth0 up[/I]

Hopefully someone else will know.  Sorry man I couldn't help you.

---

### Post by That Guy X on 2006-05-18
Thanks for tryin   hopefully someone else will know

---

### Post by That Guy X on 2006-05-18
Can anyone else help? With all those screen shots I know you can come up with something.             



(rezisting the evil temptation of going back to windows ](*,)   )

---

### Post by Slim Odds on 2006-05-19
[QUOTE=That Guy X]Can anyone else help? With all those screen shots I know you can come up with something.             

(rezisting the evil temptation of going back to windows)[/QUOTE]

Screen shots of your **loopback interface** don't really help.

I asked once, I'll ask once more:

[INDENT]Output from "ifconfig", "cat /etc/resolv.conf" and "route -n" would be very helpful.[/INDENT]

make sure that your ethernet port (eth0, eth1, whatever yours is) is checked as "activated", then give us the output of those commands.

I'm guessing that you are using DHCP, is there a DHCP client application installed?

---

### Post by redistributer on 2006-05-19
well maybe dhcp isn't working, go into windows and drop to a command box (start -- Run -- type cmd press enter) Once in a command box type 
ipconfig /all
Write down all the information
Reboot to ubuntu and go to your network properties, take off dhcp and choose static, enter the ip information you pooled from windows. Restart the network interface and try again.

Make sure you put your dns servers or you will never be able to surf the web, it could be you have an active connection (obviously you do you use it in windows) but your not resolving names due to dns, if this is true you will never surf the web without having to put the actual ip address of the server you wanna reach.

Try that hope it helps

-Red

---

### Post by majastic on 2006-05-19
Its not a DNS issue because he's not even pulling an IP address from his DHCP server. You need to do what dirwood said before. boot ubuntu, unplug the power from your modem/router for 1 minute, plug it back in, wait for all the lights to come back up, and go into terminal and type 

[I]sudo ifconfig eth0 down
sudo ifconfig eth0 up[/I]

then type ifconfig again and see if you get an IP address. If you do then :) , but if not then we can try something else.

---

### Post by Slim Odds on 2006-05-19
If DHCP is not working, it would be a much better idea to **fix DHCP**.

ISP's do sometimes change there DNS addresses and DHCP will get that automatically. Otherwise, someday your name resolution will just stop working  for no reason.

Ubuntu does install a DHCP client by default, because is it **very** commonly used. It should not be difficult to make it work.

---

### Post by dirwood on 2006-05-19
[QUOTE=Slim Odds]Screen shots of your **loopback interface** don't really help.

I asked once, I'll ask once more:

[INDENT]Output from "ifconfig", "cat /etc/resolv.conf" and "route -n" would be very helpful.[/INDENT]

make sure that your ethernet port (eth0, eth1, whatever yours is) is checked as "activated", then give us the output of those commands.

I'm guessing that you are using DHCP, is there a DHCP client application installed?[/QUOTE]
See post #8

---

### Post by redistributer on 2006-05-19
he siad the internet works in windows......
this means something is wrong with his dhcp-client in ubuntu.....
obviously he can't update it, so the best thing to do is to bypass DHCP
and assign a static ip this way he can surf and get the updates and then
try the dhcp again, rebooting the router wouldn't do anything if he can already
surf in the windows environment.
More than likley it's not the connection state.

---

### Post by Slim Odds on 2006-05-19
[QUOTE=dirwood]See post #8[/QUOTE]

Sorry, I missed that one.

eth0 has no IP address. Is it "activated"?

what type of card is it? (lspci)

---

### Post by tuga on 2006-05-19
Hello,
I also can not access the internet after boot.
To get internet I have to go to >System>Administration>Networking and then Deactivate/Activate eth0 (even if eth0 is active).
I do not know why this happens but it is the only way I know to get internet access...

---

### Post by That Guy X on 2006-05-19
Ug , I just cant figure this out. Im gonna have to wait untill the final version of dapper drake to come out. Hopefully it will have a better dhcp that works and hopefully it will come out soon.

---

### Post by Slim Odds on 2006-05-20
[QUOTE=That Guy X]Ug , I just cant figure this out. Im gonna have to wait untill the final version of dapper drake to come out. Hopefully it will have a better dhcp that works and hopefully it will come out soon.[/QUOTE]

DHCP on dapper works fine. I've used it on many different machines. I think the problem is probably with the network card/driver.

What type of card is it?

run lspci
run lsmod and see if there is a driver loaded

---

