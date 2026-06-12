---
title: "Server 10.10/Samba Help"
date: 2011-04-18
forum: General Help
---

### Post by 10up on 2011-04-18
Well generally I'm not the biggest idiot, but I am really starting to feel like it.

I recently installed Ubuntu Server 10.10 on an old desktop that I'm wanting to use as a home server. I'm not really familiar with command line but I've used the terminal enough over the last few years. I am looking forward to familiarizing myself with it for the future.

I'm stuck though. I've read everything I can find on the topic but I can't get the server to show up on my Windows PC.

I'm sitting in front of it now. If anybody on here could help me work through this once I can teach the next person that comes along. Promise.

---

### Post by collisionystm on 2011-04-18
I have a solution for you that will make your life 10 times easier.

Go to [http://www.zentyal.com/](http://www.zentyal.com/)

Download the .iso and do the same thing you did with Ubuntu. It is based on ubuntu server 10.04. It has a web interface and automates everything. It even does things you wouldnt realize needed to happen. I just discovered it a week ago and it is awesome. 

Oh did I mention it is free????? However, if you want tech support or training on it, they offer it.

---

### Post by bodhi.zazen on 2011-04-18
Ubuntu will not announce itself on the network.

Add your ubuntu server to your windows hosts file or install a dns server.

dnsmask is very easy, but then you would need to point your windows box to the dns server.

You can also try installing wins 

[http://whereofwecannotspeak.wordpress.com/2007/10/24/samba-as-a-wins-server-in-a-windows-peer-network/](http://whereofwecannotspeak.wordpress.com/2007/10/24/samba-as-a-wins-server-in-a-windows-peer-network/)

---

### Post by collisionystm on 2011-04-18
However, if you feel the need to fix your Ubuntu Server, I can  help.

How far have you progressed on your install so far? Did you configure your /etc/samba/smb.conf

Have you go on your windows box, START, RUN, \\<ipaddressofubuntuserver> *ENTER* and looked for your shares?

I.E. \\192.168.1.2

To make a basic share, on your server type sudo bash

enter your sudo password
you are now root

type apt-get install smbfs

type mkdir /share

cd /

chmod 777 -R /share

nano /etc/samba/smb.conf

page down to the bottom and add the line

[<share name>]
   path=/share
   public = yes
   writable = yes
   printable = no
   create mask = 0777
   browsable = yes
   inherit permissions = yes

CTRL + X, press Y to save


Now type
restart smbd
restart nmbd

On Windows box, start, run, \\<ip address of ubuntu> *ENTER* check for share

---

### Post by 10up on 2011-04-18
Hey thanks for the quick reply!

Although that automatic server option looks appealing I'm not sure if it works for what I'm doing. I honestly just want a home server to share files between my several computers and PS3s.  

I'm interested in making the actual server install work though too.  I like learning these things and generally only have to do it once to really understand it. It's just hard to really understand a bunch of copy and pasted codes.  

I have edited the smb.conf

At this point it is pretty barebones and a collaboration of different things I've found on the forum.

When I type 192.168.0.79 into run it does bring up the "share" folder I made but I can't access it.  This is awesome though because I didn't even know I could get that far.

---

### Post by collisionystm on 2011-04-18
If you cant access it you need to set the permissions for the folder.

Do a chmod 777 -R <pathtofolder>

The 777 does a Read/Write/Execute for the Owner, Group and OTHERS hence the 3 7's

You can check the permissions of the share currently by navigating to the Root folder that the share is in, and type ls -lh

You will see what your permissions are rwxrwxrwx or rwx------

Jut remember OWNER GROUP OTHERS for chmod and the  -R is for recursive

---

### Post by 10up on 2011-04-18
okay and changing permissions to 777 allows me access inside it now.  How do I get it to show up in the windows network though?

---

### Post by collisionystm on 2011-04-18
Ubuntu does not support NETBIOS "wins" out of the box, this is a Microsoft deal. You sir need to install nmbd to make it work the same way.

Here is the information

[http://manpages.ubuntu.com/manpages/lucid/man8/nmbd.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/nmbd.8.html)

---

### Post by collisionystm on 2011-04-18
The netbios is what allows the computers to talk to eachother with names instead of IP's without a 'DNS' server hosting their name record. If you ever use wireshark you can see the traffic on the network. you will see machines broadcasting their names. The windows computers collect the names and store them away in the DNS cache on themselves. When you do a ping it checks this cache, then the DNS server and then your ISP.

---

### Post by collisionystm on 2011-04-18
You will notice that when you try to ping the name of a Windows computer from an Ubuntu box, it says host not found. But yet you can ping the IP. That is because Ubuntu relies on DNS host name records. You can edit the /etc/hosts to achieve this.

---

### Post by 10up on 2011-04-18
interesting.

okay so this raises the question then.  Will I be able to install PS3 Media Server on it like this?  I think I'm going to have a headache just figuring out how to install it via cmdline.  If I wont even be able to get it working once (read:if) I do then I may as well just scrap this whole thing.

If you're not familiar with PMS I understand. It's just a program I found that automatically pops up on my ps3 when I run it from my windows laptop. I've never used the linux side but I know it has linux support.

[http://ps3mediaserver.blogspot.com/](http://ps3mediaserver.blogspot.com/)

---

### Post by collisionystm on 2011-04-18
I have a PS3 but have not tried a media server! 

I assume you have tried this??? [https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

If you need a GUI on your Ubuntu Server, Just type tasksel in terminal check the box for ubuntu desktop with the space bar. This does a conversion.

---

### Post by 10up on 2011-04-18
you seem very knowledgeable about all of this and I really appreciate your help!

Am I going about this the wrong way in your opinion?  Like I said all I want is for this old desktop to serve as a "media-hub" for all the devices I use in the house (4 windows computers, 2 ps3s, 1 linux computer). 

It's kinda low on resources (2.66GHz, 1GB Ram, 120GB HD) so I thought not wasting resources on a GUI would be good.  I also really like to learn about this stuff.  But if it's going to be more trouble than it's worth... well.

---

### Post by collisionystm on 2011-04-18
Meh,

Your hardware is fine. It CAN be a media  server for your devices. Just dont get frustrated. I know what a pain in the *** it is to get stuff done on Ubuntu. It is free and support is lmited to forum and friends, its hard to find someone who knows what they are talking about, and things break. Thats why I suggested Zentyal but now I would like to revoke that statement. I am building a Server for 100 users at my work and zentyal will be our PDC and file sharing server replacing an exisiting 9.10 box that is going straight to hell. That's why I am on a rant about it =)

Heres my advice. Ditch Ubuntu Server. If you want Ubuntu, use Ubuntu Desktop 10.04 not that 10.10 garbage. Immediately after install, apply your system updates and reboot. Create a share folder on the desktop or home folder, whatever. Right click on it and hit SHARE FOLDER, check the box for Guest access. BOOM, DONE! Folder is made and shared via samba. There is absolutely nothing wrong with your specs to keep you from running desktop. Just dont turn on visual effects. OH and install human-theme it looks better than ambience (default theme) i.m.o. =)

---

### Post by bodhi.zazen on 2011-04-18
You are sort of going about this the hard way.

First, windows also has a hosts file:

[http://vlaurie.com/computers2/Articles/hosts.htm](http://vlaurie.com/computers2/Articles/hosts.htm)

Add your ubuntu server to that file using the proper syntax.'

Second, I would not add ubuntu-desktop to a server "for a gui". It will not help much.

If you want a graphical interface for your server , take a look at webmin or swat.

[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

Once swat is installed, you configure samba via a web interface

[http://www.liberiangeek.net/2010/09/install-configure-swat-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-configure-swat-ubuntu-10-0410-10-maverick-meerkat/)

---

### Post by collisionystm on 2011-04-18
Ubuntu is very easy to use. Just don't let people over complicate it for you. For your file sharing just do a little playing with chmod, chown, groups and users. You will notice what each number does in the 777 bit. 7 is RWX 6 is RW 5 XR  etc.... just do an ls -lh  ( LS -LH ) to check permissions, owner and groups on your files. Do it from terminal or command. You see a lot of nonsense about crazy commands and in depth trouble shooting. Bah hum bug. I try to keep it simple.

---

### Post by collisionystm on 2011-04-18
Both Webmin and SWAT are poorly created and lack any kind of information. You may as well shoot yourself in the foot. I will admit Webmin can share files nicely, but swat will drown this guy with to many features and boxes to fill. Lets keep it simple. Use a desktop install and do it the good ol fashioned windows way. Right click and share folder

---

### Post by 10up on 2011-04-18
at this point I think I'm going to continue frustrating myself.  I'd like to complete this just to say that I did.

If it gets too bad I'm going to opt for the 10.04 desktop solution though. That is certainly easy.  Sometimes I like the hard way, it's just tough swimming out there alone for the first time.

I think if I get nmbd configured so that it shows up in windows I'll call it a success.

---

### Post by collisionystm on 2011-04-18
You know, it just occurred to me. The first time I installed Samba on an Ubuntu Sever 10.10, it automatically installed nmbd

When you installed samba did you, apt-get install samba

In the 10.10 repositories it has version 3.5.4 that includes nmbd

---

### Post by bodhi.zazen on 2011-04-18
> **10up said:**
> at this point I think I'm going to continue frustrating myself.  I'd like to complete this just to say that I did.

If it gets too bad I'm going to opt for the 10.04 desktop solution though. That is certainly easy.  Sometimes I like the hard way, it's just tough swimming out there alone for the first time.

I think if I get nmbd configured so that it shows up in windows I'll call it a success.

Did you add your ubuntu server to your windows hosts file ?

How about anything else that has been suggested in this thread ?

Simply stating that you are still having a problem without telling us what you have done is unlikely to lead to a solution.

---

