---
title: "Network Woes"
date: 2006-04-09
forum: General Help
---

### Post by abyssspecter on 2006-04-09
Okay, recently i have had a problem with my network. My brother and dads  HP laptops work via our LinkSys Wireless A+G Broadband Router. I know its Designed for Windows XP, but, it has been running for me.

I have ran route, and it always looks like so:


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref   Use Iface
```

system>administration>networking wont openeither. so....

please help

---

### Post by Ramses de Norre on 2006-04-09
What exactely doesn't work? What errors do you get on trying to do what?
Your route output seems like you haven't got a network device configured.
What's the content of /etc/network/interfaces, output of ifconfig -a, iwconfig (if wireless). What's the error on opening the network gui?

---

### Post by abyssspecter on 2006-04-09
my /etc/network/interfaces/ is a file, not a folder. and, since im on the laptop, not my computer, i cant post the output of ifconfig -a, i dont think. My computer is not wireless, so, im not worring about that.

---

### Post by neoflight on 2006-04-09
[QUOTE=abyssspecter]my /etc/network/interfaces/ is a file, not a folder. and, since im on the laptop, not my computer, i cant post the output of ifconfig -a, i dont think. My computer is not wireless, so, im not worring about that.[/QUOTE]


yes its not a folder...its a file...he was requesting you to post the contents of that FILE..... u can open it with gedit /etc/network/interfaces in the command line and copy paste....


you still havent specified what problem you are facing....then how can people help...

---

### Post by abyssspecter on 2006-04-11
okay, ifeel that i did not explain properly.My computer, which runs Breezy, is not recieving ANY form of internet/network access. i attempt to run my internet browsers (i.e. firefox, opera, epiphany, even IE), and it says that there is no signal. i attempt to access GAIM, and that says 'failure to connect, network connection'. i attempt to access system>access>networking, and it shows that its proccessing, but the window never opens. 

I am on my brothers laptop, running Windows 98. Therefore, i cannot copy and paste the contents of /etc/network/interfaces to here untill my computer is fixed. is there a way to bypass, like, saving the contents to writer, then to a disk, then putting that here, or, might that mess something up.

---

