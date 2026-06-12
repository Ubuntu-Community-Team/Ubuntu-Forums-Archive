---
title: "still haven't got a solution the dsl internet connection problem!!!"
date: 2010-01-21
forum: General Help
---

### Post by chrislionheart on 2010-01-21
The bug in Ubuntu 9.10 Network Manager that caused problems in connecting DSL and Wireless internet connection has totally wracked my brains. 

I searched for many solution but none of them worked

the ```
sudo pppoeconf
``` didn't work

some other solution caused problems...

some person told me to put ```
sudo apt-key adv--keyserver keyserver.ubuntu.com--recv-keys BC8EBFE8 
```

thing also gave a lot of problems....

some other solution removed the Auto eth connection and gave more problems....

I love Ubuntu and I'm a big fan of Linux. Please help me, since without using the internet, I can't do anything...

[SIZE="6"]**Please help!!! I'm begging!!!!**[/SIZE]

---

### Post by dineshs on 2010-01-21
sudo pppoeconf is used to connect/disconnect internet only when required.You can configure your modem with the username and password given by ISP,so that internet will be always ON and you can directly use the web browser.Did you try that?

---

### Post by chrislionheart on 2010-01-21
hey fellow Indian, Thanks for the reply

Bro can you please provide me instructions on how to do that....

---

### Post by dineshs on 2010-01-21
There are 2 steps
1.configuring ethernet 
ref this link ( reply no 4)
[http://ubuntuforums.org/showthread.php?p=8656479#post8656479](http://ubuntuforums.org/showthread.php?p=8656479#post8656479)

2.configuring modem
What modem are you using ? which is your ISP ?

---

### Post by djchandler on 2010-01-21
My solution would be to get a wireless router. pppoe is no fun on any platform.

My wife and I shared our dsl modem through an ethernet switch while running Windows 98 and NT4 10 or so years ago. We had to yell from our offices to make sure the other was not online before we went online. Each of us had to run the pppoe software. Once you have the router, you do not have to worry about pppoeconf.

Getting a router is money well spent, even if you only have one user/computer. Many other devices, such as printers, have ethernet ports. And most wireless routers have at least 4 hardwired ethernet RJ-45 ports.

---

### Post by sububtu on 2010-01-21
Hi [chrislionheart]("http://ubuntuforums.org/member.php?u=935166") ,, 
please quote the actual problem currently u hav...
and details about ISP?

---

### Post by chrislionheart on 2010-01-21
I am using Ubuntu 9.10 Karmic. I use DSL connection to connect to my Internet. 
I have taken the internet connect from my cable operator. (Cablenet)
I have been given a username and password, so as to start my Internet.

When I was using Ubuntu 9.04 Jaunty, then I use to right-click on the Network manager Icon and then click Edit Connections. 
There I used to create a new dsl connection. (put in the information) and my connection used to start. 

But in Karmic there is a problem in the Network Manager and connection to DSL doesn't work.

So please help me out!!!

---

### Post by chrislionheart on 2010-01-21
@dinesh  bro thats a solution for bsnl connections.

I am using Cable internet connection.

---

