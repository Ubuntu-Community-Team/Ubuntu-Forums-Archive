---
title: "E220 Modem"
date: 2010-04-26
forum: General Help
---

### Post by bigseb on 2010-04-26
I connect to the internet using a Hauwei E220 modem. Often (ie. most of the time) I have trouble connecting, or if a connection is established then it is most often a GPRS connection. Now you'll say it has something to do with the signal in my area but my wife uses the modem too and she never has problems connecting. She gets a HSDPA connection first time, every time. The difference between our two PC's is that she's running Windows 7 whereas I'm running Ubuntu 9.10. She obviously has the software that came with the modem installed on her system, which I can't do. I feel this may be the problem. Does anyone know how to fix this?

---

### Post by klemes on 2010-04-26
All you need probably is supply the correct modem initialization strings in the modem software you are using for the connection.
Use always the AT+CGDCONT=1,"IP","fill_your_apn_here" after the ATZ string.
:popcorn::guitar:

---

### Post by alexfish on 2010-04-26
Hi

can you explain in further detail what is happening

itemise the problems one by one something like

1. my mobile connects but can't browse
2. type of connection Network Manager {or other}
3. and so on
4 System Ubuntu Version

then a solution may be found from these 

regards 

alexfish

Also this thread should be moved =============> Networking and Wireless

---

### Post by bigseb on 2010-04-26
> **klemes said:**
> All you need probably is supply the correct modem initialization strings in the modem software you are using for the connection.
Use always the AT+CGDCONT=1,"IP","fill_your_apn_here" after the ATZ string.
:popcorn::guitar:

I am still new to Linux... don't know what you mean by this. :confused:



> **alexfish said:**
> Hi

can you explain in further detail what is happening

itemise the problems one by one something like

1. my mobile connects but can't browse
2. type of connection Network Manager {or other}
3. and so on
4 System Ubuntu Version

then a solution may be found from these 

regards 

alexfish

Also this thread should be moved =============> Networking and Wireless

1) It always syas that it is connected but nothing will load in my browser. I f something does load it is very very slow (GPRS)
2) System ---> Preferences ---> Network Connections ---> Vodacom Mobile Broadband ---> I used the default settings as I have no idea what they all mean.
3) see 2)
4) Ubuntu 9.10 x64 Ultimate Edition

Let me know if you need any more info.

PS: Sorry for putting this in the wrong discussion group. Feel free to move.

---

### Post by alexfish on 2010-04-26
Hi

welcome aboard

So lets get started. since your new we take it step by step as there are several methods to hopefully fix your problems.some can be done visually and some can be done by the terminal

lets try to resolve the connection problem first { Visually}

1. make the connection with the Network Manager
2. right click on the network icon and select Connection Information
3. note down the information it gives
4. post two sets of results, one when you can browse and one when you can't browse
5. where you can browse this will have possibly two addresses , the primary DNS and the secondary DNS
6. go to edit connections , select your connect and click on edit,select the IPv4 Settings tab and select Automatic (PPP) Address only, see screen shot
7.in the DNS servers box enter the addresses or the primary server and then address for the secondary server separated by a comma " , " without the quotes

this should fix the problem for most of the time

I also want you to monitor the connections while the IPv4 is set to  Automatic (PPP)
you may notice two or more different sets of addresses , make a note of these if it happens,


If the above works then I will take you to the next step

Added:
Also make a note of the interface , see if this changes also post these results

regards 

alexfish

---

### Post by bigseb on 2010-05-08
An update:

I entered the primary and secondary DNS addresses in the DNS server box in my connection settings, seems to have worked fine as I get a connection every time I log on since then. Don't know if its the best possible fine tuning but so far I can't complain. Thanks for your help!

---

