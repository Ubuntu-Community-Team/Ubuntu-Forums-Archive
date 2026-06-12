---
title: "Only I can view the server, not even other people on my network"
date: 2009-11-08
forum: General Help
---

### Post by AndrewRenn on 2009-11-08
Alright, so I'm not using Static IP right now, I got Apache configured, but now i'm trying to get it to be viewable everywhere.

My IP is [http://70.101.xxx.xxx/](http://70.101.xxx.xxx/) (I'm going to leave the last 2 areas blank, just incase ;)).

My Internal IP that is running on the VMWare Ubuntu is [http://192.168.45.133/](http://192.168.45.133/)

But, only I can view that page, not even other people on my network..

I have Ubuntu on a VMWare on my computer currently - I can access the FTP, I haven't tried to on other computes, but i doubt i'll be able to if they can't view it.

I'm wondering why no one else can view it but me? (Not even people on the same network as me!)

And another question is:

How would I configure DNS and all of that stuff, so I could run my domain on it? (My domain is mydomain.com for example)..

Thanks!!

---

### Post by The Cog on 2009-11-08
Firstly, I think that by default, apache only listens on the loopback address. Post the output of ```
netstat -lnt
``` and we can tell you if that's so. 

Second, I'm not familiar with vmware, but if it's using address translation (NAT) to connect your VM to the main network then I don't think incoming connections will be possible.

---

### Post by AndrewRenn on 2009-11-08
> **The Cog said:**
> Firstly, I think that by default, apache only listens on the loopback address. Post the output of ```
netstat -lnt
``` and we can tell you if that's so. 

Second, I'm not familiar with vmware, but if it's using address translation (NAT) to connect your VM to the main network then I don't think incoming connections will be possible.

Thanks for replying so fast!

And here is a screen shot of what it said (it was a lot of info, ;))

also - I'll check to see if its using NAT to connect. If it is, what would you recommend I set it to? _**/e it is nat**_

Thanks

[IMG]http://i177.photobucket.com/albums/w214/DiabloKiller12/vmwarelinux.jpg[/IMG]

---

### Post by The Cog on 2009-11-08
You need to set the VM to bridged. Be aware that bridged puts the VM on the network just like a real host - all your normal security worries should apply.

Looks like MySQL is listening OK already - its the 3306 line, listening on 0.0.0.0. Had it been listening on 127.0.0.1 instead then it would have only been accepting connections from the machine it's installed on.

---

### Post by munky99999 on 2009-11-08
Ya unless you have gotten into iptables. Which if you are exposing in to the net. Would be a very good idea to do.

[http://ubuntuforums.org/showthread.php?t=1046738]("http://ubuntuforums.org/showthread.php?t=1046738")

The issue I think you are having is that you havent set the vm to bridged. Meaning when the other people on the network aim toward hitting that. They hit your host OS and not the guest. Your host not knowing what's going on really.

---

### Post by AndrewRenn on 2009-11-08
> **The Cog said:**
> You need to set the VM to bridged. Be aware that bridged puts the VM on the network just like a real host - all your normal security worries should apply.

Looks like MySQL is listening OK already - its the 3306 line, listening on 0.0.0.0. Had it been listening on 127.0.0.1 instead then it would have only been accepting connections from the machine it's installed on.

I have it set to bridged now - and when I do ifconfig on it, i see this
[IMG]http://i177.photobucket.com/albums/w214/DiabloKiller12/vmwarelin2.jpg[/IMG]

It doesn't give me an IP to try to get onto though. :/

So I dont know how to get onto it now :(

Also, do you know where the Apache config file is? I tried nano /etc/apache2/httpd.conf and that didn't work.


Thanks!

---

### Post by munky99999 on 2009-11-08
it actually did.

[http://img8.imageshack.us/img8/4933/vmwarelin2.jpg](http://img8.imageshack.us/img8/4933/vmwarelin2.jpg)

you got an ip6 address with a /64 subnet. 

which probably means it never got a dhcp release. 


You could try 

ifconfig eth0 down
then 
ifconfig eth0 up

or simply restart

---

### Post by AndrewRenn on 2009-11-08
Alright, gnona try that now, just turned it back on.

I foudn the config file btw, and I dont know what to look for to allow everyone to view my site?

Thanks ;)

---

### Post by AndrewRenn on 2009-11-08
> **AndrewRenn said:**
> Alright, gnona try that now, just turned it back on.

I foudn the config file btw, and I dont know what to look for to allow everyone to view my site?

Thanks ;)

Alright - so I still see that ip6 address - what would that be in my web browser?

I'm still confused on what to do now :/

---

### Post by munky99999 on 2009-11-08
> **AndrewRenn said:**
> Alright, gnona try that now, just turned it back on.

I foudn the config file btw, and I dont know what to look for to allow everyone to view my site?

Thanks ;)

Literally soon as you installed apache with the whole

sudo apt-get install apache2

You pretty much had an accessible webpage on that computer. The only configurations would would have needed to do would be ssl sort of things or if you have iptables or similar running for security.

The actual html stuff you edit and look at will be in /var/www/

---

### Post by munky99999 on 2009-11-08
> **AndrewRenn said:**
> Alright - so I still see that ip6 address - what would that be in my web browser?

I'm still confused on what to do now :/

Your problem is that you arent getting onto the network basically. Not getting a dhcp release. Thusly arent speaking on the network.

Make sure your virtual nic within vmware is bridged. Next issue might be your dhcp server isnt giving a lease to the vmware maybe because of mac filtering. Your ubuntu may itself not be setup to use dhcp.

That I believe is the issue you are having.

---

### Post by The Cog on 2009-11-09
The ipv6 address will always show - fe80::* is a link-local address and doesn't indicate that a proper ipv6 address has been assigned.

The lack of an ipv4 address suggests that either bridging isn't working or there is no DHCP server on the network. The fact that the interface also reports 0 packets received also suggests some kind of problem with the bridging setup - it's basically deaf as a post.

---

