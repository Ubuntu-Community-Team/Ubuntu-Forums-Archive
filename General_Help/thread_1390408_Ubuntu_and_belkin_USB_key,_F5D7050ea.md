---
title: "Ubuntu and belkin USB key, F5D7050ea"
date: 2010-01-25
forum: General Help
---

### Post by scott dillon on 2010-01-25
Hi, could someone help me out. 
When I log on to Ubuntu, I can read, Youa re now connected to the wireless network. 
Then when I try to access through Firefox, it will not connect. 

This is the error

Error: uncaught exception: [Exception... "Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIXMLHttpRequest.status]"  nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)"  location: "JS frame :: chrome://ubufox/content/startpage.html :: anonymous :: line 51"  data: no]


What to do?
Scott.

---

### Post by cariboo on 2010-01-25
Check your dns, if it is set to the ip address of your router, you need to change it to your isp's dns addresses. A quick test is to open an Applications->Accessories->Terminal and type:

```
ping www.google.com
```

if that fails try:

```
ping 74.125.53.147
```

if that works, right click on the network manager icon in the top panel.

[list]
[*] select edit connections
[*] select your network device
[*] click the edit button
[*] click the IPv4 tab
[*] from the method dropdown select Automatic (DHCP) addresses only
[*] enter your dns addresses in the DNS Servers text box
[*] click apply, and enter your password.
[*] you may have to disable and enable networking by clicking the network manager icon
[*] you should now have internet access
[/list]

---

### Post by scott dillon on 2010-01-30
cariboo907,

Thanks for your knowledge. I now have internet connection and using ubuntu for the first time. Righton.

Much appreciated. Enjoy the day.
SD

---

