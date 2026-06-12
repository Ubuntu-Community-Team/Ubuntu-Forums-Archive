---
title: "Changing Dynamic IP"
date: 2010-03-27
forum: General Help
---

### Post by srdr on 2010-03-27
Is there any way to change Dynamic IP on Linux ?

I have found[_** this**_]("http://ubuntuforums.org/showthread.php?t=1406300")thread regarding this issue 

as smeagol271006 mentioned in his thread , we have to disable avahi daemon to get this above code to work properly. dhcpcd trick worked like a charm for me but i have 2 major problem.

problem 1. I always get the same dynamic ip. I need to change dhcpcd -r IP by hand to get a new dyn IP.
problem 2. since i disabled avahi and network manager , i can no longer use DHCP feature . I have no choice but to enter dhcpcd code snippet manually to assign a dynamic IP for every system restart.

Is there any clean way to get a new dynamic IP without using dhcpcd ?

I am using cable modem.

i really need your answers.

thank you

---

### Post by srdr on 2010-03-28
anyone?

---

### Post by pbrane on 2010-03-28
Your ISP is giving you your IP using DHCP. There is a lease time on that IP. You will likely get the same IP until the lease expires.

---

### Post by smeagol271006 on 2010-03-29
Here are instructions I forgot to post here (I will translate them)

A friend of mine post them on my request in this site:

[http://www.taringa.net/posts/linux/4689579/Jdownloader-|-Reconnect-|-Ubuntu-|-Cablemodem-|-NO-Router.html]("http://www.taringa.net/")


We want Jdownloader to give us a new IP automatically

In my case I don't have router, only the cablemodem.



This was the first solution supplied by 123andres

[http://www.taringa.net/posts/linux/3946536/Cambiar-IP-de-Fibertel-en-Ubuntu-9_10.html](http://www.taringa.net/posts/linux/3946536/Cambiar-IP-de-Fibertel-en-Ubuntu-9_10.html)

Now I will show you how to change it automatically on demand.

This is the script we will use (thanks 123 andres!):

```
#!/bin/bash
dhcpcd -k eth0 ; sleep 4s; dhcpcd -r 190.189.48.70 -l 10000 eth0
```What I think the script does is the following (The ones who have approved CCNA are free to correct):

1) End the connection in interface eth0 y deletes the previously used  ip's cache.

2) Waits for 4 seg.

3) dhcpcd informs ISP hardware (Internet Service Provider) that our IP is 190.189.48.70 or any reasonable number we want. This would appear to the ISP to be the last IP we used (it actually isn't), before connection ceased.

4) Hardware from the ISP does not recognize IP in it's lists of cablemodem clients; then what it does is give us a new ip (lease).

5) Sets leasetime (I don't know if this option does work with all servers, but as the server does assign another IP different to the one asked for, I think it does not take effect (the -l flag). Most servers use a parameter already definde by them, not always changeable (you have to try). Fibertel ISP takes various days to renew IP by the server system. Option is in seconds.


Obviously you have to install dhcpcd!

Once we installed the program we do the following:

We save the script in a file. For example "change-ip"

```
#!/bin/bash
dhcpcd -k eth0 ; sleep 4s; dhcpcd -r 190.189.48.70 -l 10000 eth0
```If we create it in our home/$USER directory

```
chmod u+x ~/change-ip
sudo mv ~/change-ip /usr/bin/
```To try it

```
ifconfig -eth0
sudo change-ip
ifconfig -eth0
```If ip numbers are different it should be working. Check connectivity with web browser.

If browser is not working and you have Karmic, it is surely not working because of the following  (other variants could be).



** First Problem**


* Package "network-manager-gnome"*

This package is responsible for the applet that manages connection and laptops daemon. Daemon can be instructed from the tray.

If you are using a laptop with a router you shouldn't be reading this; but if you connect your laptop by cable and also use public networks, uninstalling this packages is maybe not the best option. You should investigate how to work the connections with other program.

The problem with this program, is that I have not found console commands supports. So every time you run the script you have to decconect by hand using the tray option ande then reconnect again with the tray. a Pain in the *** ...

We can uninstall it if we don't use it or if we find a better alternative  (laptop with cable).

If you are using a Desktop PC you can remove it. I will explain later hot to configure it manually (very easy with DHCP)


Try again:

```
ifconfig -eth0
sudo change-ip
ifconfig -eth0
```If a warning bugger has appeared on sceen and browser does not work, probably you are being affected by another daemos. See following section then.



** Second Problem**


*Avahi*

You can see what it does by following the link. Uninstalling is not necessary. Disable it with by modifying a configuration file.

HERE they explain the HOW.

I transcribe

[quote=Ubuntu]
Avahi will always start even if a .local domain is present

The avahi-daemon package, which implements the mDNS "zeroconf" standard, formerly included a check to avoid running when a conflicting .local DNS domain is present, as it was reported that some ISPs advertise such a .local domain on their networks, leaving Ubuntu hosts unable to see names advertised on the local network (327362). In Ubuntu 9.10, avahi-daemon is started regardless.

It is possible that this may cause other problems. If your network is configured this way, you can disable mDNS using the following command:

sudo stop avahi-daemon
sudo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf
[/quote]I recommend to backup it just to be safe.

```
sudo cp /etc/init/avahi-daemon.conf /etc/init/avahi-daemon.conf.old
```With that done you can rest peacefully.

Now everything should work. WAIT Before trying do the following.



[COLOR=Red]**IMPORTANT**[/COLOR]


If you uninstalled NetworkManager and disabled avahi-daemon keep reading:

Your file /etc/network/interfaces probably looks like this:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
```If the following line is not there, then leave 2 or 3 blank lines and add this line (I presume your interface is eth0)

```
auto eth0
iface eth0 inet dhcp
```With that ends DHCP configuration (¿It was easy, no?)


We try again:

```
ifconfig -eth0
sudo change-ip
ifconfig -eth0
```If browser works, You can start dancing in one leg!



** Configuring the system**


Now that the IP does change and not any program does interfere, we move to the next:

The  idea is that the script is called by Jdownloader to be interpreted by Bash. So that Jdownloader calls it when necessary.

The problem is that dhcpcdneeds super-user grants to run (not a problem, but a security measure).

The ideal solution would be for it to not ask for a password (would be really great for the ones that leave their computer alone) (UPS with automatic emergency shutdown recommended ).

¿How can we do this?

AS sudo deals with authentication, we have to reconfigure it, in order to be password-less only for our script.

We make use of visudo command that will alow us to edit file sudoers in a secure way.

```
sudo visudo
```We insert a line at the end of the file that contains the following:
```
# Line created for Jdownloader
user hostname = NOPASSWD:/usr/bin/change-ip
```In user you replace it with your user
In hostname you replace it with your hostname (use hostname command to get hostname)

You can also do it this way. This would allow command execution in all hosts. If the first one does not work try it.

```
# Line created for Jdownloader
user ALL = NOPASSWD:/usr/bin/change-ip
```Quit vi with ":wq" or pressing "Shift + z + z"

Now we run it to see if it works.

We run
```
sudo -k
```to delete previously given permissions (sudo does not ask you for a password if you have used it just before)

```
sudo change-ip
```If it works see following section



** To configurel Jdownloader!!**


Go to "Reconnect" and then "External" tab

In Command we write: "/usr/bin/sudo"
In Parameter we write: "/usr/bin/change-ip"
In Advanced we write something more or less logical:

My configuration of the fields in descending order

20
1
30

Or we leave it as it is


With all this done it should work no problem

You can go and dance in two legs, leaving your machine alone and downloading. Also saving energy!



**Advantages**


Some servers make you wait 1 hour for files downloaded in 15 minutes. Now it only takes %20 of that total time. Is a whole lot less and you help reduce energy consumption



**Limitations**


It could also be possible that your ISP does not have dynamic IP or une that you can change on demand like this. This method has only failed me once. Maybe there is a limit? ...



Thanks to all the users that helped me

I wil ask moderators to merge the posts

---

### Post by srdr on 2010-03-30
thanks for the great tutorial smeagol.

edit : it's really working now. But you must change the IP address in the code with the one  thats within your ISP's IP range. Otherwise it won't work.  
thank you

---

### Post by smeagol271006 on 2010-03-30
Yes I forgot to specify that. If your ip is currently 190.189.48.701 try something in range like
190.189.48.702.

You are welcome!

---

