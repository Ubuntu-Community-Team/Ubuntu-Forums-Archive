---
title: "How to set up network at startup"
date: 2006-03-02
forum: General Help
---

### Post by davidhong on 2006-03-02
Hi,

I don't really know how this works but I know it works. But here's a summary of what I am doing in order to get my WG311v2 working with my wireless network.

First, I go into terminal and type in:
```
sudo iwconfig wlan0 ap xx:xx:xx:xx:xx:xx
sudo iwconfig wlan0 key xxxxxxxxxx
sudo ifconfig wlan0 up
sudo dhclient wlan0
```
This enables my internet.

Now, I am tired of doing this procedure manually after every boot. Is there a way to make this procedure happen automatically at boot, so that any network related processes such as updating ubuntu time (during boot) works? So I am guessing something like Window's startup applications or services.

PS: If you could explain why those cmds get my wlan0 working, it will be great. I don't even have ndiswrapper installed.


Thanks,

David G. Hong

---

### Post by localzuk on 2006-03-02
Hi and welcome,

Here is what those commands do:

1. Set the card to use a specific wireless access point
2. Set the WEP security key for that wireless lan
3. Brint the network card 'up' ie. turn it on
4. Send a request for an IP address from the network's 'dhcp' server

The reason they work without ndiswrapper is likely that you have a wireless card that has a driver that works in Ubuntu already.

To get it do it automatically, take a look in  /etc/network

It should contain something like this for your wireless card:

```

iface wlan0 inet dhcp
wireless_keymode open
wireless_ap xx:xx:xx:xx:xx:xx
wireless_key xxxxxxxxxxx
wireless_mode managed
wireless_essid XXXXXenter here your essidXXXXXX
wireless_nick XXXXXXXXXXX

auto wlan0

```

(By this I mean insert this in place of any other mentions of wlan0, if you are not sure it may be best to post your /etc/network file here before you make any changes so we can say what to change it to).

Hope this helps

---

### Post by akiro.yamamoto on 2006-03-02
You can probably use the Network Config under System to do this or
Enter the info into /etc/network/interfaces.

---

### Post by davidhong on 2006-03-02
[QUOTE=akiro.yamamoto]You can probably use the Network Config under System to do this or
Enter the info into /etc/network/interfaces.[/QUOTE]
Can you elaborate on this please?

I tried editing the interfaces file according to manuals, but it didn't work out.

I need to run those 4 command lines (previously mentioned in my thread starter) in order to get my internet working. Right now I've created a sh file inside ```
/etc/init.d/
``` and then ran ```
update-rc.d filename defaults
```
But that doesn't seem to run before Ubuntu bootup processes contacts the ntp.ubuntu.org for time sychronisation. So I guess what I ultimately want to do is make ntp.ubuntu.org time sychronisation work by making my internet connect prior to that.

In correspondance to localzuk, yes the ```
/etc/network/interfaces
``` file has a whole lot of those stuff, but it doesn't seem to work. I tried setting somethings like ```
wireless-key xxxxxx
wireless-essid xxxx
...
``` but how do you get it to connect? I did this after saving a backup and when it didnt work, I restored the file. I will post up the file's contents soon, but right now I am not home.

Thanks for the help guys.

---

### Post by Ramses de Norre on 2006-03-02
Yes, post the file here. It really should start when it's configured right.
Have you've got another network card that's set as default? Because then ubuntu will always try that card.

This is what my /etc/network/interfaces looks like: (don't mind the #'s)
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface ath0 inet static
wireless-essid RAFAEL
wireless-key ##########
address 192.###.123.106
netmask 255.255.248.0
gateway 192.###.123.254

auto ath0

```

---

### Post by localzuk on 2006-03-02
Looking at your file, I don't know what ath0 is?

I would replace

```

iface ath0 inet static
wireless-essid RAFAEL
wireless-key ##########
address 192.###.123.106
netmask 255.255.248.0
gateway 192.###.123.254

auto ath0

```

with 
```

iface wlan0 inet dhcp
wireless_keymode open
wireless_key xxxxxxxxxxx (should be s:xxxxx if it is an ascii key)
wireless_mode managed
wireless_essid RAFAEL
wireless_nick wireless

auto wlan0

```

This should ask the wireless lan for an ip like your 4th command. 

If ath0 is the name of your wlan card, swap wlan0 out of my example and put ath0 in.

---

### Post by davidhong on 2006-03-02
Okay, I will try this and let you guys know. Meanwhile, let me ask some questions regarding the scripts you guys have put up.

I can see that the key is being set (this is step 2 of 4)
I can see that from the very last code section, dhcp method is being used which localzuk explained as the 4th step.

Where are steps 1 and 3? Cheers.

Btw, How do I check what my default network card is in ubuntu? And, my wireless network card's name is wlan0.

Under my Settings -> Admin.. -> Networking, there are three cards listed, only wireless network card is activated. Others are deactivated.

---

### Post by localzuk on 2006-03-02
You shouldn't have to do 1 as the essid should allow your machine to choose the access point automatically - however if it doesn't you can add it to the change I posted by adding a line ```
wireless_ap xx:xx:xx:xx:xx:xx
```

The script is ran whenever it is asked to bring up 'the network' so for instance on startup. This is done automatically during execution.

---

### Post by davidhong on 2006-03-02
Here is my interfaces content:
```
% more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

# The primary network interface
iface wlan0 inet dhcp
	network 192.168.0.0
	broadcast 192.168.0.255
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid ESSID
	wireless-ap x:xx:xx:xx:xx:xx
	wireless-key xxxxxxxxxx
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.0.1
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.1

auto wlan0
```

---

### Post by davidhong on 2006-03-02
Thanks for the help guys, it worked. Works perfectly with the previously posted interfaces configuration.

[SIZE="7"][COLOR="Green"]PROBLEM: SOLVED[/COLOR][/SIZE].

---

### Post by localzuk on 2006-03-03
Hi,
You seem to have static settings as well as dhcp settings. I would change it to:
```

iface wlan0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid ESSID
	wireless-ap xx:xx:xx:xx:xx:xx
	wireless-key xxxxxxxxxx

auto wlan0

```

---

### Post by localzuk on 2006-03-03
Woo! Good stuff :) You might as well ignore my response to the prior one then. Don't touch what isn't broken :D

---

### Post by davidhong on 2006-03-03
[QUOTE=localzuk]Woo! Good stuff :) You might as well ignore my response to the prior one then. Don't touch what isn't broken :D[/QUOTE]
But I might give it ago. :P I'll reply here if it works. :twisted:

---

### Post by mzilhao on 2006-03-03
hi, 

i have a similar problem. 
my wireless network only works if i deactivate before shutting down, and then activate it again after logging in...

my /etc/network/interfaces:

```
miguel@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface ra0 inet dhcp
wireless-essid SSID
auto ra0

```

---

### Post by localzuk on 2006-03-03
Could you explain what you mean by 'activate'. The interfaces file you have posted should be fine on a non-secure wireless network called SSID...

Do you have to run ifup ra0 in order to load the card?

Also, what wireless card are you using?

---

### Post by mzilhao on 2006-03-03
i go to system > networking > connections and i activate the wireless connection. it works, provided that i always deactivate it before shutting down. 
here's what iwconfig says when the network is working:

```
@ubuntu:/tmp$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2400PCI  ESSID:"SSID"
          Mode:Managed  Channel=11  Access Point: xx:xx:xx:xx:xx:xx
          Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:69  Signal level:24  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sit0      no wireless extensions.

```

---

### Post by localzuk on 2006-03-03
Do you use wep security on your network?

---

### Post by mzilhao on 2006-03-04
no, it's open

---

### Post by mzilhao on 2006-03-04
oh, and i've just tried the dapper live cd, and i couldn't access the internet. but i could ping the router...

---

### Post by localzuk on 2006-03-04
This indicates a lack of a 'gateway' address or 'dns server' address. Are these being served by your dhcp server?

You could try adding links to your access point and also indicate the management type of your network in your interfaces file (see the earlier examples of this). Is this card using an ndiswrapper'ed driver?

---

### Post by mzilhao on 2006-03-09
thanks for your help!
so, i've found out what was wrong. it really is the dns settings. the problem now is that my /etc/resolv.conf file (the one that keeps the dns settings), is always updated when i boot. i need to keep it from getting updated... i've tried every solution i could find on the forums, but nothing seems to work!
i have to manually replace it every time i boot...
any ideas...?

thanks again

---

### Post by brok3n on 2006-03-09
I'm not sure how yours is set up, but my resolv.conf is set up by default as

resolv.conf

search domainname.local
nameserver X.X.X.X
nameserver X.X.X.X

I think if you comment out the search option, and specify the name server that you want in the 2nd line, it won't search everytime it boots...


This may not be true however, because I'm rather new to ubuntu.

---

### Post by mzilhao on 2006-03-09
my resolv.conf file is like this:
```
miguel@ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 194.65.100.117
nameserver 194.65.5.2

```

but when i boot, it always gets updated to this:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```
which doesn't contian any information...
i always have to change it again, so that i can access the internet...

---

### Post by mzilhao on 2006-03-11
ok, my internet is now working properly, apparently.
what i did was completely remove all the dhcp3 packages and the resolvconf package...

---

