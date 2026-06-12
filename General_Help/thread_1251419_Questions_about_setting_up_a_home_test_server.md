---
title: "Questions about setting up a home test server"
date: 2009-08-27
forum: General Help
---

### Post by Jmz360 on 2009-08-27
Hi,

I'm trying to set up an old computer as a home test for my PHP/MySQL web applications but I'm a bit confused on where to start.

I downloaded the server version of Ubuntu and installed it but I'm a bit stuck with the command prompt. I've tried a few commands I found on the internet to install a GUI but have had no luck with them.

So here go my questions,
Should I even be using the server distro of Ubuntu? After I installed it I saw a few people recommending different versions as it's only a home server so security and performance isn't too much of an issue. Ideally I'd like a GUI to make it a bit more simple to use.

My home network is secured with WPA Personal, will Ubuntu still be able to connect with this?

Thanks!

---

### Post by SuaSwe on 2009-08-27
This here might help:

[http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/](http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/)

I use Ubuntu Server myself and as the command line interface is quite easy to use, I've never thought to attempt to install a GUI onto it, but it should be possible (see link).

---

### Post by MTGap on 2009-08-27
You could just use a normal Desktop version and install PHP and MySQL to it. But if you want to use it only as a server and want to keep resource use to a minimum you should stay with ubuntu server.

---

### Post by bchurchill on 2009-08-27
Server vs. Desktop is up to you.  Server is just a slimmed down version that has less toys on it initially.  If you're just starting out with Linux, I recommend Desktop since it's easier to start with.  As far as server applications, Apache2 is very easy to get started with.  Something like

sudo apt-get install apache2 php5

will get you started.  You may need to install another package for mysql, but i'm not sure what.  However, if you're looking for a GUI interface to manage your sever, I don't think apache has one by default.  Although I bet someone has made one...  I don't know much about this though.

EDIT: yes, Ubuntu can connect to WPA.  NetworkManager comes installed on Desktop and does this easily.  I would recommend using wicd instead though (sudo apt-get install wicd), as many people find it works better (although not all).

---

### Post by bear24rw on 2009-08-27
im pretty sure you can
```
sudo aptitude install ubuntu-desktop
```
and you should be able to reboot into a desktop (never tried it but i would imagine i would work)

honestly though i would just reinstall with the normal version of ubuntu there is really no difference in terms of capabilities.

and yeah ubuntu can handle wpa encryption

---

### Post by Jmz360 on 2009-08-28
Thanks for all your help, I'm re-downloading the desktop version to install when I get back from work tonight.

Now, is it possible to use some sort of remote desktop to control the ubuntu installation from my mac (os x leopard) over my wireless network?

---

### Post by P4man on 2009-08-28
Yes.
:)

By default in ubuntu you have a "remote desktop" option (system > preferences > remote desktop)  which is compatible with vnc clients, available for mac too Im sure. But I find it works slow. Painfully slow even over a LAN. YMMV.

I find freeNX to be MUCH faster:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Its also has both windows and OS-X clients.

(oh and if you dont need a gui, there is always ssh)

---

### Post by nothingspecial on 2009-08-28
> **Jmz360 said:**
> Hi,
 I've tried a few commands I found on the internet to install a GUI but have had no luck with them.


I`m not sure how the server edition works but I think you probably need to connect to the internet.

```
sudo ifconfig eth0 up 192.168.1.2
```

specify whatever ip address you like.

Then you can ```
sudo apt-get install ubuntu-desktop
```

This assumes you have a wired connection.

---

### Post by bchurchill on 2009-08-28
> **p4man said:**
> 
(oh and if you dont need a gui, there is always ssh)

+1

---

### Post by Jmz360 on 2009-08-28
> **nothingspecial said:**
> I`m not sure how the server edition works but I think you probably need to connect to the internet.

```
sudo ifconfig eth0 up 192.168.1.2
```specify whatever ip address you like.

Then you can ```
sudo apt-get install ubuntu-desktop
```This assumes you have a wired connection.

That will be what's my problem with installing the GUI, I wouldn't know where to start setting up my wireless through command lines.


I've only used SSH a few times so hopefully FreeNX wont be too slow for me!

---

### Post by nothingspecial on 2009-08-28
Turn on your wireless

```
sudo ifconfig wlan0 up
```

Scan available networks

```

iwlist wlan0 scan
```

Connect
```

sudo iwconfig wlan0 essid *[COLOR="Red"]networkname_here[/COLOR]*
```

Give the key if needed

```
sudo iwconfig wlan0 key [COLOR="Red"]passphrase_here[/COLOR]
```

Get your ipadrress
```

sudo dhclient
```

Then you`re done.

Although wlan0 (see first 2 lines) is usually your wireless interface it is not always, you can check by typing ```
ifconfig
```

---

### Post by Jmz360 on 2009-08-28
So if I run those commands and then:

```

sudo apt-get install ubuntu-desktop

```

[FONT=monospace]It should launch the GUI and then I can install/configure everything else through that?
[/FONT]

---

### Post by nothingspecial on 2009-08-28
It should.

---

### Post by Jmz360 on 2009-08-28
I've tried running 

```

ifconfig

```

But it doesn't tell me my interface so I tried this instead.

```

lshw -C network

```

Which tells me my interface is wmaster0 (I think).

If I try to run

```

sudo ifconfig wmaster0 up

```

I get the error

```

SIOCSIFFLAGS: Operation not supported

```

If I try 

```

iwlist wmaster0 scan

```

I get the error 

```

wmaster0 Interface doesn't support scanning

```

---

### Post by P4man on 2009-08-28
Can you post the output of ifconfig?

---

### Post by Jmz360 on 2009-08-28
It says:

```

Link encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2  errors:0 droppd:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:100 (100.0 B) TX bytes:100 (100.0 B)

```

---

### Post by P4man on 2009-08-28
thats all? I see neither a wired nor a wireless connection there!

can you post the output of ```
lspci
``` and if you use a USB dongle, that of ```
lsusb
``` ?

---

### Post by Jmz360 on 2009-08-28
It outputs quite a lot from the lspci command but the stuff to do with the networking is:

```

00:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:10.0 Ethernet controller: Realtek semiconductor co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Let me know if you need to see anything else from it.

---

### Post by P4man on 2009-08-28
before I start digging into the wireless card, which it seems, doesnt work out of the box.. does the LAN work? I see nothing in ifconfig about the lan, unless you omitted that. You would be extra-ordinarily unlucky to have both a lan and wifi card that is not supported out of the box.

---

### Post by P4man on 2009-08-28
as for the wifi card, indeed its not supported "out of the box". I googled, and found this :

[http://home.facticity.org/2009/07/26/ralink-rt2561rt61-802-11g-on-ubuntu-9-04-jaunty-jackalope/comment-page-1/](http://home.facticity.org/2009/07/26/ralink-rt2561rt61-802-11g-on-ubuntu-9-04-jaunty-jackalope/comment-page-1/)

looks like a pretty straightforward howto to get the card working. once it works, try "nothingspecial" 's commands again to connect.

---

### Post by Jmz360 on 2009-08-28
How do I check if the LAN is working?

I'd have to run a wire downstairs to my router if I wanted to use it though so I'm trying to keep away from it.

When I ran the setup it picked up my wireless card but I chose to configure it later, could that have something to do with what's happening?

---

### Post by P4man on 2009-08-28
> **Jmz360 said:**
> How do I check if the LAN is working?

eh? do you have internet connection on it? If so, its working :)
If you havent installed a gui yet, and you're not sure, then post the entire output of ifconfig. if you already did that, it certainly looks as if its not working..

> When I ran the setup it picked up my wireless card but I chose to configure it later, could that have something to do with what's happening?


Hmm.. I'm not sure. maybe they included a script or something to download those drivers for you during or after the install, a bit like with video drivers?  but ive never seen it. 3 of my wifi cards and sticks work out of the box, and one doesn't work period (except using windows drivers and ndis wrapper). But you did a server install right? Its different, and I thnk what it asked you was to configure tcp/ip settings not install drivers.

Anyway, its clear your wifi card is not running now, so just go ahead and install those drivers.

---

### Post by Jmz360 on 2009-08-28
Ah, I thought you meant the LAN card on the computer I'm trying to install Ubuntu on. The internet I'm using is on a different computer.

Yea that was the full output from ifconfig. To get those drivers on I'm going to have to download them on my mac and move them across with my usb sick which I'm guessing I'm really going to have problems with since I'm useless with this command prompt.

I downloaded the desktop installation but when I put the disk in and reboot it loads an Ubuntu GUI. Can I use this to install the drivers?

---

### Post by P4man on 2009-08-28
houston, we have a problem :)

You want to install a gui, but you dont have network connection, so scratch the "apt-get install ubuntu-desktop". you want to install drivers for a network, but you cant download them. Heh. You have live cd which gives you a gui, but anything you install there, wont be installed in the actual harddisk install unless you do some chroot wizardry at the command prompt, which you're no good at :D

Ok there are a few approaches possible here. You could use the "alternate cd" as source to install a gui. You cant use the regular live cd for that, unless you want to do a full reinstall.

I think the easiest is sticking to the command prompt for now, and installing those wifi drivers using an usb stick. If nothing else, it will help you get familiar with the CLI :)

Before I start talking you through it, let me see I get this right. You now have your server with ubuntu server and no gui, and no network connectivity whatsoever ? How did you copy paste those outputs, did you type them over, or do you have a ssh / vnc / whatever connection to the machine?

---

### Post by Jmz360 on 2009-08-28
I managed to get it working :P

I installed the desktop version and then followed the guide in the link you sent me and it worked! :)

Thanks for all your help! I would have been on forever. No doubt I'll be asking more questions soon.

Thanks again!

---

### Post by nothingspecial on 2009-08-28
I`m sorry, I`ve been asleep, good job you had P4man there.

Anyway, I`m glad you got it sorted.

Don`t give up on the command line. Once you get used to it you`ll see it`s advantages. If you`re not comfortable with it yet though, I can see why you want a gui.

---

### Post by Jmz360 on 2009-08-28
I'm going to try and use the command prompt as much as I can so that I can get used to it but the GUI will help with stuff I'm unsure about. 

I'm installing Apache/PHP/etc now but I'm not sure how I would set it up so that I can access the localhost folder by going to the IP of the Ubuntu computer.

---

### Post by P4man on 2009-08-28
default settings should work fine. But just to be clear, your website will be in /var/www/ on the ubuntu machine. That website should be available from the remote machine through [http://ubuntu-ip-address/](http://ubuntu-ip-address/) and on the local machine as [http://localhost](http://localhost)

and you already know the CLI command to find your local IP :D

---

### Post by Jmz360 on 2009-08-29
Ok, so I've installed Apache, PHP, MySQL and PHPMyAdmin and they're working.

I also have FreeNX installed and I can remote to the computer from my Mac without any problems.

But I do have some more questions :confused: 

First, my wireless doesn't work automatically when I log into Ubuntu, I have to click on it and connect. I Googled it an found some code to add to the rc.local file but that doesn't seem to have fixed it.

Next, I can access the var/www/ folder by going to the IP of my Ubuntu computer which is fine, but so could everybody else on my network. Can I only allow certain IPs to access it or protect it some other way?

Finally. Can I share the var/www/ folder with my Mac so that it's like a network drive or something? Then I can code the stuff on my Mac and save it straight to the www folder on my Ubuntu computer.

Sorry for taking up so much of your time! 
:)

---

### Post by bchurchill on 2009-08-29
> **Jmz360 said:**
> 
First, my wireless doesn't work automatically when I log into Ubuntu, I have to click on it and connect. I Googled it an found some code to add to the rc.local file but that doesn't seem to have fixed it.

Next, I can access the var/www/ folder by going to the IP of my Ubuntu computer which is fine, but so could everybody else on my network. Can I only allow certain IPs to access it or protect it some other way?

Finally. Can I share the var/www/ folder with my Mac so that it's like a network drive or something? Then I can code the stuff on my Mac and save it straight to the www folder on my Ubuntu computer.


Are you using NetworkManager?  If so I recomend switching to wicd (apt-get install wicd).  It will remove NetworkManager and replace it.  In Wicd there's an option under each wifi network to automatically connect.

For accessing /var/www, there are many ways of doing this, although I'm not sure what you mean.  Are you talking about viewing it over HTTP through a web browser, or some other sort of remote access?  If the former is the case then you'll want to modify Apache configuration files. A general tutorial is here:  [http://articles.techrepublic.com.com/5100-22_11-5076696.html](http://articles.techrepublic.com.com/5100-22_11-5076696.html), but conveniently the first example it gives is about what you're doing. 

Yes, you can set up /var/www to be a file share.  I forget exactly how to do this in Ubuntu, but I'm pretty sure you can just right-click a folder and choose the share option in nautilus.  Then you can setup Samba or NFS sharing, either of which should work fine with your mac.

---

### Post by Jmz360 on 2009-08-29
Wahey! I think I've got all that sorted :)

Is there anything else I should do?

---

### Post by bchurchill on 2009-08-29
> **Jmz360 said:**
> Wahey! I think I've got all that sorted :)

Is there anything else I should do?

Awesome!  I think you should go have fun with your new server :grin:

You might want to go about hardening/securing it further, but since it's just for your home network that's probably mostly unneccesary as long as you have a firewall router and your other computers are appropriately protected.  Ubuntu is pretty secure from the get-go, so there shouldn't be much to worry about.  If you do decide to go live you may want to take extra precautions though.

---

### Post by Jmz360 on 2009-08-29
Now I'm having trouble with MySQL :)

I'm sure I tested it last night and it worked, but it was late so maybe I imagined it :confused: But if I try to log into PHPMyAdmin I get an error:

```

#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

```

I've tried starting and restarting MySQL through the terminal but it just says [fail] after a while.

My my.cnf looks like (the bit to do with the socket anyway):
```

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 192.168.1.103

```

192.168.1.103 is the IP of my Ubuntu computer.

---

