---
title: "Configuring samba on 2 different networks"
date: 2010-07-17
forum: General Help
---

### Post by undertai on 2010-07-17
OK i have to different routers in my home.  One is at&t dsl modem other is dlink wireless n router.

I have my ubuntu server connected to my att modem as this is the only way I can get it to work.  As I can only connect to my server from the outside of my home.

Problem is my desktop and laptops use the dlink because its faster and giver me more bandwidth so everything in my home is wirelessly connected to it.

I use ubuntu as web server, proxy server, and dns server.  I have all my computers useing the proxy server my just inputting my proxy address as 192.168.1.0 which is my ubuntu address.  But my computers use 192.168.0.0 as this is how dlink is setup.



So anyone know how I can get all my pc's on the network 192.168.0.0 to connected to my samba server which is on 192.168.1.0? Can I setup my dlink dir-615 as a access point?  So that it shows up in the 192.168.1.0 network.  Or can i configure my pc's to look into the 192.168.1.0 network to see the samba server?

Thanks

---

### Post by endotherm on 2010-07-17
you should be able to configure samba to listen on and respond to queries from multiple networks, as long as they can all reach eachother. 
the two settings in your /etc/samba/smb.conf to check at 
```

interfaces = 127.0.0.0/8 eth1

and

hosts allow = 192.168.XX.0/24 192.168.YY.0/24  127.0.0.1

and mabey

hosts deny = 0.0.0.0/0

```so these settings tell the server to listen on all nics (you probably only want to specify the nic that sits on your internal network, not the one that connects to your dsl modem), 
and allow hosts from the XX and YY networks as well as the server itself. it will deny all hosts not specifically allowed. 

if you only have one nic in your ubuntsrv box, then this is a little tricker to secure, but should still give you access. having a proxy server with only one nic is a heck of an efficiency waster though, so look into installing another if this is the case.

I would recomend a network layout like the one attached if you want to continue to run with 3 routers, or if you want, you could reconfigure the dlink to operate in bridge mode, and combine both the internal networks.

---

### Post by undertai on 2010-07-17
I only have one nic as i'm using an old toshiba techra laptop.  It has one ethernet port and one wireless card.  The wireless portion is not in use.  I didn't really think that it would be much use.  But only using the one eth. port I get a 10% - 15% speed increase with the proxy.

So how would I go about setting it up with only 1 eth. interface?  

Could I setup a wins server on the ubuntu box and then have my pc's look for the WINS server

---

### Post by endotherm on 2010-07-17
well, the wins server only works for naming, so unless it works fine when you supply the IP of the samba server, but fails when the the server name is used, wins will not solve the problem. do you think your issue is with naming or routing or with the service security?
the first two can be tested with ping. if you ping both the ip and the name of the server, do both work? does ip work and naming does not?

---

### Post by undertai on 2010-07-17
i thinks the problem is routing.  I pinged 192.168.1.67 and ubuntu.example.local and got a response from both.  I also setup my pc to use the wins server 192.168.1.67 but the server doesn't show up in networking under windows 7

even pinging from outside my network works to my webserver

---

### Post by endotherm on 2010-07-17
> **undertai said:**
> i thinks the problem is routing.  I pinged 192.168.1.67 and ubuntu.example.local and got a response from both.  I also setup my pc to use the wins server 192.168.1.67 but the server doesn't show up in networking under windows 7

even pinging from outside my network works to my webserver
ok, what is the output of
```
sudo route
```from an internal machine, and from the server?

I'm gonna be offline for a while, but I;ll check back late tonight, and hopefully someone else will be able to pick up from where we left off.

also another thing to try. since your dlink router is between you and your server, the packet filter/firewall may be blocking your packets. check the logs, to see if anything is being dropped. this is another reason to consider putting the dlink in bridge mode. 

I am a little worried that you are running samba for internal stuff and a webserver for public stuff on the same box with only one nic. it means that unless you configure samba and iptables very carefully, the default settings will allow any one access to your samba.

---

### Post by undertai on 2010-07-17
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         home            0.0.0.0         UG    100    0        0 eth0

output from sudo route

I think I my have got it.  Now only problem is when I setup a share on windows it ask for my user name and password.  I enter both but it comes back and says password is wrong.  I don't have a password on my pc's but on the ubuntu box I use the right password to login and it comes back and says wrong password.

---

### Post by capscrew on 2010-07-17
You will not be able to browse multiple subnets without using a WINS server.  Samba is not a routeable protocol.  From the manual "You need to set up Samba to point to a WINS server if you have multiple subnets and wish cross-subnet browsing to work correctly."

NetBIOS works at Layer2 and will not cross broadcast domains.

---

### Post by endotherm on 2010-07-17
have you ever registered the ubuntu user with samba using smbpasswd or shares-admin?
if you haven't, then that is likely the problem. if you are using the gui to create and administer shares, then hit Alt+F2 and enter```
gksu shares-admin
```
go to the last tab, and check the user that you want to have samba access.

if you are using the  smb.conf to configure sharing, from a terminal run
```

sudo smbpasswd -a <user>

```
it will prompt you for a passsword, and confirm. after that samba will allow that user access.

lets us know how it works.

PS: Netbui/Netbios are a layer 2 protocol, but nowadays are wrapped for IP by default on most systems. I believe samba is the same. I personally have run samba over multiple networks using the smb.conf I showed above.

---

### Post by undertai on 2010-07-18
I did the next best thing.  On my other router not AT&T I installed dd-wrt; so now my new router gets it's ip's  from my AT&T router.  Everthing is on one ip adress 192.168.1.0 but now I can't see my ubuntu on my pc's still.  Maybe something with the configure files.  So I will do a "aptitude purge samba" after o get of work tonight.  Then I will reinstall and see what happens.

---

### Post by endotherm on 2010-07-19
> **undertai said:**
> I did the next best thing.  On my other router not AT&T I installed dd-wrt; so now my new router gets it's ip's  from my AT&T router.  Everthing is on one ip adress 192.168.1.0 but now I can't see my ubuntu on my pc's still.  Maybe something with the configure files.  So I will do a "aptitude purge samba" after o get of work tonight.  Then I will reinstall and see what happens.
are you still getting the unending password prompt? if so, use smbpasswd as I mentioned in my last post, or if not, post back and let us know where you are currently at with the troubleshooting.

---

### Post by undertai on 2010-07-19
I still get the unending password wrong password.  But under networking in windows I can now see my ubuntu server.  When I try and map a network I use my ubuntu login and pass.  But I noticed that the box that ask for my user and password.  Has the domain of my pc as the domain name.  Could this be the problem?  The name of my pc is MEDIA; and the box that pops up asking for user and pass.  Says domain is MEDIA!  My ubuntu box is ubuntu

---

### Post by endotherm on 2010-07-20
ok, so let me get this straight:

you are connecting from the windows box as a client, to the ubuntu box as a server, correct?

in that case, the ubuntu user account is the one you use to login with. the workgroup/domain name doesn't matter much, but what does matter is registering the ubuntu user account with samba. a samba user must exist as a unix user, and then be registered with samba. 

on the ubuntu box, open a terminal and run
```
smbpasswd -a <usernameOnUbuntuBox>
```and provide/confirm the password as prompted. 

after that, you should be able to login to the ubuntu box from the windows box, using the ubuntu users account.

in terms of the workgroup, are the windows and ubuntu machines both in the same workgroup? you can check/set the ubuntu workgroup by hitting Alt+F2, and entering 
```
gksu shares-admin
```

---

