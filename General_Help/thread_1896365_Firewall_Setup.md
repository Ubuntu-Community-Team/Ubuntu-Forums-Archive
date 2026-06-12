---
title: "Firewall Setup"
date: 2011-12-16
forum: General Help
---

### Post by adamantasaurus on 2011-12-16
I'm following this tutorial to setup a server for my website. 

 [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/comment-page-1/#comments](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/comment-page-1/#comments)

I get to the part where it wants me to install shorewall and then theres a problem.

It tells me to enter sudo cp /usr/share/doc/shorewall-common/examples/one-interface/*/etc/shorewall.

and I get an error of....

cp: missing destination file operand after '/usr/share/doc/shorewall-common/examples/one-interface/*/etc/shorewall'

Why is it doing that?

Then the next problem is.........

It tells me to edit the rules file of shorewall 

sudo nano /etc/shorewall/rules
Add these lines above where it says “#LAST LINE”
HTTP/ACCEPT	net		$FW
SSH/ACCEPT	net		$FW

But after I enter 
sudo nano /etc/shorewall/rules

A blank screen just shows up with no code on it what so ever so I just wrote the code in as I see in the picture 

I wrote this...

Ping/REJECT     net            $FW
ACCEPT            $FW          net       icmp            
HTTP/ACCEPT	net		$FW
SSH/ACCEPT	net		$FW


Is that ok to do??

Then the final problem is I go to start shorewall by entering.....

sudo /etc/init.d/shorewall start

and it give me an error of.......

Starting "Shorewall firewall": not done (check /var/og/shorewall-init.log).

How do I fix this and all these problems??

Thanks So Much in Advance 

Any Advice is really appreciated I am very new to ubuntu and willing to learn anything I can.

---

### Post by lukeiamyourfather on 2011-12-16
That tutorial is no longer current. What version of Ubuntu are you using? See the Ubuntu Server Guide if you haven't already, note the version in the URL.

[https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

It has many other entries that should cover most of or all of your needs, for example setting up Apache to serve pages.

---

### Post by haqking on 2011-12-16
> **adamantasaurus said:**
> I'm following this tutorial to setup a server for my website. 

 [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/comment-page-1/#comments](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/comment-page-1/#comments)

I get to the part where it wants me to install shorewall and then theres a problem.

It tells me to enter sudo cp /usr/share/doc/shorewall-common/examples/one-interface/*/etc/shorewall.

and I get an error of....

cp: missing destination file operand after '/usr/share/doc/shorewall-common/examples/one-interface/*/etc/shorewall'

Why is it doing that?

Then the next problem is.........

It tells me to edit the rules file of shorewall 

sudo nano /etc/shorewall/rules
Add these lines above where it says &#8220;#LAST LINE&#8221;
HTTP/ACCEPT	net		$FW
SSH/ACCEPT	net		$FW

But after I enter 
sudo nano /etc/shorewall/rules

A blank screen just shows up with no code on it what so ever so I just wrote the code in as I see in the picture 

I wrote this...

Ping/REJECT     net            $FW
ACCEPT            $FW          net       icmp            
HTTP/ACCEPT	net		$FW
SSH/ACCEPT	net		$FW


Is that ok to do??

Then the final problem is I go to start shorewall by entering.....

sudo /etc/init.d/shorewall start

and it give me an error of.......

Starting "Shorewall firewall": not done (check /var/og/shorewall-init.log).

How do I fix this and all these problems??

Thanks So Much in Advance 

Any Advice is really appreciated I am very new to ubuntu and willing to learn anything I can.

first of all any reason for shorewall ?

all firewall interfaces in Linux do the same thing, they configure IPTables whether it be UFW/GUFW/Firestarter/Shorewall etc

anyways the first cp command is bad syntax i think you need a space after the * im guessing as i am not familiar with shorewall

the second point, does the file exist in the location and is it correct syntax ? which is likely down to the first command not working

and what are the errors in the log ? which again are likely due to the first command not working

you may want to see here for firewall configuration [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

---

### Post by adamantasaurus on 2011-12-16
> **lukeiamyourfather said:**
> That tutorial is no longer current. What version of Ubuntu are you using? See the Ubuntu Server Guide if you haven't already, note the version in the URL.

[https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

It has many other entries that should cover most of or all of your needs, for example setting up Apache to serve pages.

I'm using version 11.10 and I see the tutorial is for 10.04 should I just restart everything with that version and use the tutorials on this site?

What would you suggest?

---

### Post by haqking on 2011-12-16
> **adamantasaurus said:**
> I'm using version 11.10 and I see the tutorial is for 10.04 should I just restart everything with that version and use the tutorials on this site?

What would you suggest?

IPTables directly from CLI.

or UFW with GUFW GUI front end.

---

### Post by adamantasaurus on 2011-12-16
> **haqking said:**
> IPTables directly from CLI.

or UFW with GUFW GUI front end.

What does all that mean all I understand is User Interface?

---

### Post by haqking on 2011-12-16
> **adamantasaurus said:**
> What does all that mean all I understand is User Interface?

it is all in the link i posted in my first post and it explains UFW/GUFW/IPTables and how to install and setup the most popular configuration for a firewall in Ubuntu.


read the basic security wiki [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
its firewall section [https://wiki.ubuntu.com/BasicSecurity#Firewall](https://wiki.ubuntu.com/BasicSecurity#Firewall)
and the link on there on how to configure one [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124) which is all done in 11.10

Cheers

---

### Post by adamantasaurus on 2011-12-16
> **haqking said:**
> it is all in the link i posted in my first post and it explains UFW/GUFW/IPTables and how to install and setup the most popular configuration for a firewall in Ubuntu.


read the basic security wiki [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
its firewall section [https://wiki.ubuntu.com/BasicSecurity#Firewall](https://wiki.ubuntu.com/BasicSecurity#Firewall)
and the link on there on how to configure one [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124) which is all done in 11.10

Cheers

thanks so much

---

### Post by lukeiamyourfather on 2011-12-17
> **adamantasaurus said:**
> I'm using version 11.10 and I see the tutorial is for 10.04 should I just restart everything with that version and use the tutorials on this site?

What would you suggest?

There's a server guide for every version of Ubuntu, including 11.10 but I linked to 10.04 LTS because most people setting up servers for use in production will use the Long Term Support (LTS) releases because the server version has five years of support and security updates. Normal releases of Ubuntu have two years of support and updates, so 11.10 will no longer have support or security updates much sooner than 10.04 LTS. At the moment 10.04 LTS is the current LTS release. Here's the server guide for 11.10 if you choose that route.

[https://help.ubuntu.com/11.10/serverguide/C/index.html](https://help.ubuntu.com/11.10/serverguide/C/index.html)

---

