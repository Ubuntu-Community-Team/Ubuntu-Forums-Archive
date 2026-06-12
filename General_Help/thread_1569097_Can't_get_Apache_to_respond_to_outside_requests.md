---
title: "Can't get Apache to respond to outside requests"
date: 2010-09-06
forum: General Help
---

### Post by jfusco on 2010-09-06
I've been scouring the message boards and trying different things for two days and haven't found a solution. I set up Ubuntu 10.04.1 a few days ago using the server iso and selected the LAMP installation option. I will be using it as a sandbox to try out things from a PHP/MySQL book I purchased.

I have installed Gnome since sometimes I just can't get the command prompt to let me do things and Gnome may at least tell me why. I also installed PHPMyadmin.

My problem is that I can work with this thing all I want in any way I want - HTTP, SSH, SFTP, etc. - from within my home network but Apache refuses to respond to an outside request. Since it's only a test box it usually wouldn't be that big of a deal but I am going out of town for a couple of days and would really like to start working with my new book.

I am 99% sure my ISP is not blocking any ports. I have a ComTrend ADSL modem with router. I have given my Apache server a static IP on the NAT (xxx.xxx.x.101) and set up a dyndns address so I don't have to keep remembering the IP address. 

Here is what I have tried so far:

[LIST=1]
[*]Setup a virtual server (port forwarding) on the router to to direct traffic on port 80 to internal IP .101
[LIST=1]
[*]The router told me its interface is using 80 so it would move itself to 8080
[*]Made sure to also add port trigger for port 80
[*]Made sure to save/reset the router
[*]Used my iPhone to connect via 3G - didn't work using IP or dyndns name
[*]Used iPhone to connect to 8080 and router responded
[/LIST]
 
[*]Set port forwarding/triggering for 8080 -> 80. No joy there, either
[*]Tried changing listening port to 8000
[LIST=1]
[*]Set port forwarding and triggering to allow port 8000
[*]Changed ports.conf to read NameVirtualHost *:8000 and Listen 8000
[*]Changed first line of /etc/apache2/sites-enabled/000-default to <VirtualHost *:8000>
[*]Restarted Apache service
[*]Apache responded to dyndns.com:8000 from home machine
[*]No response when trying same on iPhone (sorry, it's the easiest way for me to test from outside my home network)
[/LIST]
 
[/LIST]
At one point, I added "ServerName localhost" to the otherwise empty httpd.conf file but that didn't seem to do a darn thing.

Many of the posts I have perused are at least a couple of years old and have included information on taking action with files that are not there or are no longer where they were. I have interpolated where I can but so far nothing has worked. ANY suggestions would be appreciated.

Thanks,

---

### Post by amrypma on 2010-09-06
Can you get Apache to serve a web-page at all on the machine it self?
If it doesn't do that then fiddling with you router will never help.

i.e. [http://localhost/](http://localhost/) should show the very welcome message "It works!"

Your router should have a port forward from port 80 to xxx.xxx.xxx.101:80.
NO TRIGGERING! triggers wait for an event from your internal network before any forwards are set up. This works for games you play online but not apache. Apache has to be able to receive incoming trafic all the time.

you could/should forward port 22 the same way to use ssh and sftp. Do this anyway because if you can log in remotely you can also fix apache remotely.
Don't touch ssh's configuration. ssh listens on all interfaces and all ip addresses and only cares about your username and password. (It's the most usefull service ever and hell to fix if it's messed up.)

As for the Apache config... well it can become really complicated really fast. So first I'd advise you to completely remove apache-LAMP and install the plain apache2 package. Apache has it's own modules to handle php. Get apache to serve pages first, complicated stuff second.

I hope this help.

---

