---
title: "Is NFS safe from outside sources"
date: 2010-12-12
forum: General Help
---

### Post by NertSkull on 2010-12-12
I'm sure someone can answer this really easily.  But everything I look up on security with NFS talks about security from people within your own network and permissions etc.

I just want to make sure if I set up NFS on my home network that there isn't something special (like IPsec) that I need to set up to prevent the rest of the internet from accessing it.  I don't care if all users and computers in my home network access it (thats what I want).

Is it secure as long as I have the normal firewalls and such things running?  Or is there any risk of turning on NFS and then letting the outside world have access to my stuff? 

Thanks

---

### Post by lensman3 on 2010-12-12
I have blocked the following (at one time or another) from going to the Internet.  There several ports that should be blocked.  The following is from an iptables script I once used.

```
  $IPTABLES -N Bad-Ports

#***************************************************************************
#************not used for internal interface********************
#***************************************************************************
# Block various ports to the internet

   # nfs-2049, openwindows-2000, socks-1080, squid-3128, lockd-4045, 2745 (used by back door viruses)
   DENIED_PORTS_TCP="69,111,135,593,444,515,2049,20034,27374,27665,27444,31335,10498,12754,2745"
   $IPTABLES -A Bad-Ports -p tcp -m multiport --destination-port $DENIED_PORTS_TCP --syn -j blocked

   # Block the X windows port range (6000-6063)
   XWINDOWS_PORTS="6000:6063"
   $IPTABLES -A Bad-Ports -p tcp --syn --destination-port 6000:6063 -j blocked

   # Block udp NFS, LOCKD, 7100-X-font server
   DENIED_PORTS_UDP="69,111,135,445,515,593,444,2049,7100,31337,27444,31335,10498"
   $IPTABLES -A Bad-Ports -p udp -m multiport --destination-port $DENIED_PORTS_UDP -m state --state NEW -j blocked

   # Block smb ports ms-rpc(135)
   $IPTABLES -A Bad-Ports  -p tcp --sport 135:139  --dport 135:139 -j DROP
   $IPTABLES -A Bad-Ports  -p udp --sport 135:139  --dport 135:139 -j DROP

   $IPTABLES -A Bad-Ports -j RETURN
   ##------------------------------------------------------------------------##

```

Look at the file "/etc/services".  It has the assigned tcp/udp assigned ports.  

Hope this helps.

---

### Post by NertSkull on 2010-12-12
So that makes it sound like you do need to specifically block certain ports.

I can't totally figure out what portmap is.  Some of the NFS tutorials say you need to use, it others don't mention it.

What exactly is portmap, and is it important to set up with my NFS if its just between a couple of computers on my home network?

---

### Post by Zill on 2010-12-12
NertSkull:  FWIW, my understanding is that if you are running your LAN *behind* a DSL router that uses NAT (Network Address Translation) then your local network should be *reasonably* secure.

I am certainly not an expert but I have been running my LAN in this way and using NFS for years with no problems.

I believe the most important files to configure for NFS security are the hosts.allow and hosts.deny files.  If the /etc/hosts.deny file contains the line ALL:ALL then *all* access will be denied *except* from the specific addresses listed in the /etc/hosts.allow file.

See ["Setting Up an NFS Server"]("http://tldp.org/HOWTO/NFS-HOWTO/server.html") for more background info on this.

---

### Post by NertSkull on 2010-12-13
Allright, that sounds good.  Thats kind of the impression I have got as well - to use the /etc/hosts.deny and allow files.

So I put in deny all in the deny file

And then in the allow file just the internal network like 192.168.0.0/24

So hopefully that will be good enough.  Thanks

---

### Post by Zill on 2010-12-13
> **NertSkull said:**
> ...So I put in deny all in the deny file

And then in the allow file just the internal network like 192.168.0.0/24...
The entry in the /etc/hosts.deny file should be:
```
ALL: ALL
```
To allow access from localhost and the internal network I suggest the following entry in the /etc/hosts.allow file:
```
ALL: 127.0.0.1 192.168.0.0/24
```

---

### Post by NertSkull on 2010-12-13
Thanks I didn't think about putting in the 127 loopback thing.  Thats probably wise.

Also the guides I have read suggest putting it in as a portmap thing.  So endy hosts looks like

```
portmap: ALL
```

and in the allow

```
portmap: 127.0.0.1 192.168.0.0/24
```

So that's what I put in.  Is it better to use ALL: ALL

I'm still not entirely positive on what portmap is doing.  I just know I've seen it a handful of times as the suggestion to install it and put it in the deny/allow files.

---

### Post by Zill on 2010-12-13
NertSkull:  I use exactly the same syntax shown in post [#6]("http://ubuntuforums.org/showpost.php?p=10234314&postcount=6") above.  I have found no reason to use "portmap" specifically as I believe this is implicit in using "ALL".

Like you, I am unsure exactly how portmapping interacts with NFS.  All I know is that by using the "ALL" descriptor, NFS (and presumably portmap) works as I expect it to :-)

ps.  If things do not seem to work initially, I have found a reboot can help sync portmap and nfs.  Not a "true" Linux solution - but it works for me ;-)

---

### Post by katykat on 2010-12-13
One of the greatest problems I have had with Linux is figuring out what is best for a fully functional local network while keeping out unsolicited traffic from the Internet. 

Linux is designed for tight security on local networks, which is the opposite of what many users like myself want or need. I want maximum access and file sharing on my network, and at the same time shut off remote desktop functions, since if I need to operate those machines I can do it from their keyboards. 

I am behind a good NAT firewall on my Netgear router on a cable network. I am mainly interested in acessing the Internet without it accessing my local network. For running servers I intend to be booting up to a seperate Linux install. 

Are there any good FAQs for setting up Ubuntu security from these points of view:
1. Complete access to all users on the local network. 
2. No access to anyone trying to access the system from outside the local network. 
3. No remote desktop functions to any user on any network. 

I have found #3 to be particularly useful on the Windoze machines, where if the occasional bugger gets in it has extreme difficulty doing anything, especially with Internet Explorer sandboxed and denied access to everything.

---

### Post by Zill on 2010-12-14
> **katykat said:**
> One of the greatest problems I have had with Linux is figuring out what is best for a fully functional local network while keeping out unsolicited traffic from the Internet. 

Linux is designed for tight security on local networks, which is the opposite of what many users like myself want or need...
You are quite right to be concerned about security, particularly if you are from a Windows background ;-)  However, Linux is actually designed for tight security on *all* networks, not just local networks.  This means that, by default, an Ubuntu desktop install has no open ports, restricting access from the "outside world".

As you are behind a NAT router, your local network is isolated from the internet and, without any open ports, *nothing* can access your Ubuntu PCs without your specific approval.

If you *choose* to run any servers, such as ssh, NFS, FTP or a webserver, then you will need to understand the security implications of this.  However, no such servers are part of a default Ubuntu desktop installation.

Access for other users within your local network is fairly simple to implement.  If they are all running Linux then I suggest NFS is the way to go as this is a pure *nix system and is *relatively* secure.  However, if you have any Windows users then you will probably need to run Samba (no Windows here so I can't advise on this!).

Remote desktop access is not enabled by default in the Ubuntu install, but I understand that you can easily enable this with a few clicks.

The following links may help explain things but "Google is your friend" and there is lots of good info out there, and on this website, to ensure things are set up securely.

[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")
[Security on Ubuntu]("http://psychocats.net/ubuntu/security")
[Share your Ubuntu Desktop Using Remote Desktop]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")
[VNC]("https://help.ubuntu.com/community/VNC")

As this thread is primarily about NFS security, if you have any further questions about different aspects, I suggest you start new threads as this will help people searching for info in the future.  Good luck.

---

### Post by NertSkull on 2010-12-14
Everything Zill said about security I would completely agree with.  I've just barely started getting into NFS and security because I just got a second computer and started needing access to it.

But in general, security is the main reason I switched to linux a few years ago.  I LOVE the options for it.  Some things I do (and would recommend to anyone - especially those wanting security) is to look into a few things.

gpg - gnu privacy guard is a great way to encrypt files/emails/whatever with security keys

SSH - A great way to access your computer through encrypted channels.

dm-crypt/LUKS is an awesome way to encrypt your entire hard drive.  If your computer gets stolen, no worries about people getting your data.  It can even be set up with a dual boot and you can encrypt windows as well.

duplicity - for encrypted (through gpg) backups.  I will never leave linux because of this program alone

ufw (uncomplicated firewall) is definitely something you want to learn.

true-crypt - another, simple to set up way to encrypt files/file-systems

those are just some of my thoughts on security.  there are scores of more programs things I use and find interesting, but I really try to lock my system down tight and I love it.

anyway, sorry to take my own thread even further off topic, but I think I'm feeling pretty good about NFS security now.  I changed the hosts files from "portmap" to "ALL" and everything seems to be working great.

thanks everyone for the advice

---

### Post by katykat on 2011-05-22
Sorry for dredging this up, but  it is a very important topic.

The main thrust of it is that so much of the Linux security is based around LOCAL NETWORK security - keepin local users from doing naughty things - that there is not very much security stuff in a fundamental, easy to understand approach that deals with the issue of maximum ease of use with a SINGLE USER NETWORK.

A basic peer-to-peer network where there is nothing hidden, all files are readable/writiable, and especially when some of the other machies are Win - the user is typically admin/root.

The aim is to permit the machines to access the internet, but to not permit the internet to access the machines without explicit permissions. 

And NO Remote Desktop functions. 

I have Telnet disabled at the Router, and will prbably do the same for SSH, unless I can find any info on why it may not be a good idea. 

SO basically:
Are there any guides for those who have absolutely no interest in 'Local' security, but maximal interest in 'WAN' or Internet security beyond the recommendations with the Hosts files, and possibly IPTables?

And does SELinux provide additional protections from malware scripts when run by admins as part of routine maintenance. I've been working with *local* servers lately so running as root is the only realistic option when configuring them. I hate software that tries to second guess me.

---

