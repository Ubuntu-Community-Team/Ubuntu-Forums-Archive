---
title: "karmic internet connection issues?"
date: 2009-11-12
forum: General Help
---

### Post by jon zendatta on 2009-11-12
hell0.
I have done fresh install of 9.10. Problem is I can not update or connect using mozilla. The curious thing is i have 100% connection when i highlight the network icon..Any enlightenment please:KS

---

### Post by Wim Sturkenboom on 2009-11-12
Your post is missing something. 100% connection means that your using wireless? WiFi to a router or HDSPA or ...
And what is the output of *ifconfig*

---

### Post by jon zendatta on 2009-11-12
0k. just bear with me. I'm dual booting with xp, so few minutes away

---

### Post by jon zendatta on 2009-11-12
ok. I can't post that. As I'm connecting fine this way using xp. Even trying the broadband cable said "wired connection active" but i still couldn't get internet. 
 ifconfig claimed no packets dropped. Sorry for the lack of information. Maybe my laptop is too old?:KS

---

### Post by bilol on 2009-11-12
Hi jon,
Have you followed the steps?
(1) Righ click on my network place in XP and from TCP/IP properties and note down your IP,Netmask,gateway and DNS .
(2)Log in ubuntu.Right click on the network icon on the top right of your desktop and choose VPN connection>Configure VPN> Wired>auto etho>edit>IPV4 setting>Method> Manual> Now properly input the noted down IP,Netmask,gateway and DNS. Click Aplly.
(3) Close the window and again open it to check you have entered the configuration  properly.[ Check the gateway : it may become all zeros for wrong input.
(4) restart the machine.
(5) Log in ubuntu and browse through  Mozilla firefox.

** I suppose you have forgotten step (4)

---

### Post by jon zendatta on 2009-11-12
thanks bilol..about to do that. could be a while before i reply

---

### Post by jon zendatta on 2009-11-13
still no internet. looked at the above & resolvconf.
Oddly I was able to get internet  on a wimax connection & do all the updates. Now back at home(ADSL) I can only use XP still to access internet with or without cable.
PS: I can access my router web-page

---

### Post by Wim Sturkenboom on 2009-11-14
> **jon zendatta said:**
> still no internet. looked at the above & resolvconf.
Oddly I was able to get internet  on a wimax connection & do all the updates. Now back at home(ADSL) I can only use XP still to access internet with or without cable.
**PS: I can access my router web-page**Using wireless or wired or both? Please be complete in the information that you provide.

If only wired works, I think that it's a config issue like wrong SSID or password. What do the router logs say?

---

### Post by jon zendatta on 2009-11-14
neither wired or wireless works. The network icon states I have connection with either, but I cannot get internet with either. No issue with my network settings as that is how I'm communicating now via XP.

---

### Post by Wim Sturkenboom on 2009-11-15
As you can access the router, you have an IP address so that part is OK.

Try to ping google.com. The firewall might block the actual ping but you shoudl be able to figure out if this is a dns issue.
```

fortyfourgalena@desktop1:~$ ping google.com
ping: unknown host google.com
fortyfourgalena@desktop1:~$ ping google.com
PING google.com (74.125.53.100) 56(84) bytes of data.

```If you get the message from the first command, the name can not be resolved and you have a dns issue; if you get an ip address as shown in the second example, the dns is ok and you must look somewhere else.

---

### Post by the.scarecrow on 2009-11-29
Hi 
I had exactly the problem you described and solved it like this.

Can't access Internet. Goto System>Preferences>Network Connections, on Wired and Wireless Ipv4 Tab change from “Automatic DHCP” to “Auto (DHCP) addresses only” add IP address 208.67.222.222 in the DNS servers box. Restart any internet connection.

Don't ask me why it works cos I haven't a clue but it solved the problem for me and Karmic is superb.

---

