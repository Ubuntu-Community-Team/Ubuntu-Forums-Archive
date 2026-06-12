---
title: "Host: fanaticalvps Error: Could Not Determine Fully Qualified Domain Name"
date: 2012-03-23
forum: General Help
---

### Post by The8thLegion on 2012-03-23
Hi. I have a shared host with 5 sites on it. 3 wordpress blogs that almost have nothing on it. 1 xenforo forum that is a year and a 1/2 old and another xenforo that is a couple months old, but inactive. I have all of that on urljet shared hosting. My site is around 3GB total. 

Just recently decided to move to an offshore unmanaged vps because of several problems I have with urljet such as I'm not able to use cdns properly with their service and i can't use geoip with them either for digitalpoint's user map.

I have fanaticalvps medium package which is 70gb space, unmetered bandwidth, 700 something ram. but their control panel is confusing in some ways in that yes i can install multiple os that they provide but i keep getting stuck on 'the perfect server' kind of guides because some settings don't match from what i see.


I've been trying to follow [The Perfect Server guide for Ubuntu 10.04]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p3") for some time now and I keep running into several errors. None of the how-to guides have addressed this issue and the customer support for fanaticalvps answers aren't helping me either. 


First issue. 

A fellow customer who has the same host as me told me not to touch the network/interfaces file as mentioned in Step 7: Configure The Network.

I think it has something to do with the fact that we are able to install Linux distros at the click of a button: [http://wiki.fanaticalvps.com/info:distros](http://wiki.fanaticalvps.com/info:distros)

As a result, I've skipped that step and went straight to the second part of Step 7. The second part of Step 7 asks me to edit the etc/hosts/ file to look like this:

127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


When I opened my /etc/hosts file it looked like this:

::1 localhost.localdomain localhost
127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
189.4.232.100 rubix


^^^BTW using a made up number for ip address and host name.

Because my ip address and host name were already showing but looked different from the sample shown (no server1.example.com type entry) I created a ticket and asked fanaticalvps customer support the following question:

Q: Hello. I'm trying to set the host name. I changed it to rubix but it is asking me for the FQDN. What do I use as the FQDN? For example, in The Perfect Server guide it asks me to update this file. /etc/hosts

For example:
Update /etc/hosts


File:/etc/hosts
127.0.0.1 localhost.localdomain localhost
189.4.232.100 rubix.rubix.com rubix



I'm following this guide: [http://library.linode.com/getting-started#sph_set-the-hostname](http://library.linode.com/getting-started#sph_set-the-hostname)

and this one mainly: [http://www.howtoforge.com/perfect-server-ubuntu-11.10-with-nginx-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-11.10-with-nginx-ispconfig-3-p3)


This is their answer

A: Hi, To set the hostname all you need to do is change it in the control panel, otherwise it will be reset every time you reboot the VPS.

Also note /etc/hosts is not the correct file, /etc/hostname contains the hostname.


-----

So I checked the hostname and it is the same as the host name in the hosts file (rubix).

When I type hostname in command line and hostname -f as well, I get rubix. 

So then I asked them this:

Q: Are you saying that my My Fully Qualified Domain Name is the same?

That doesn't look right from all the guides I've been looking at. 


and they answered


A: Hi, You can set the hostname to anything you like, it makes no difference (it's merely there so you can track multiple servers/etc by naming them).


then I asked.

Q: Oh okay so I can name it rubix.com I've named the host as rubix. 

The example that the perfect server guide gives me is:
192.168.0.100 server1.example.com server1

So I can enter it as:
189.4.232.100 rubix.rubix.com rubix

? 

and they reply

A: Where would you be entering this? If it's for DNS you only need to set an A-record for the domain/sub-domain to the IP (hostname makes no difference to this, you can point the domain/sub-domain to the IP with or without the hostname set).

and I respond

Q: It says it here in Step 7 Configure The Network [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p3)

I'm assuming that is the first step that I start at when following that guide since Ubuntu 10.04 is already installed fresh. 

New password for the MySQL "root" user: <-- yourrootsqlpassword
Repeat password for the MySQL "root" user: <-- yourrootsqlpassword
Create directories for web-based administration? <-- No
General type of mail configuration: <-- Internet Site
System mail name: <-- server1.example.com
SSL certificate required <-- Ok

Do I put rubix.rubix.com for the System mail name?

----

Several hours later there is no answer so I restart a fresh installation of Ubuntu 10.04 and follow their directions from here: [http://wiki.fanaticalvps.com/tutorial:stack:apache_php_mysql](http://wiki.fanaticalvps.com/tutorial:stack:apache_php_mysql)

Then I come upon the same problem: 

apache2: Could not reliably determine the server's fully qualified domain name using 189.4.232.100 for ServerName 


Still no answer so I'm creating this thread here in hopes of getting some kind of answer that makes since. I am a noob but I've been at this for a couple days now and have learned a lot.

---

