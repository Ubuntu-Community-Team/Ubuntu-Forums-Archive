---
title: "Is anyone else having Networking Issues?"
date: 2010-05-06
forum: General Help
---

### Post by theozzlives on 2010-05-06
I wanna know if it's my config or Ubuntu.

I have a laptop with the standard SAMBA setup I've always done (always worked).

I have Ubuntu Server with my shares specified in my smb.conf.

I have Windows 7 with the standard file/print sharing.

I I try to access my workgroup via Nautilus I get, "Failed to recieve share list from server". I can accec\s my shares just fine using ip addresses. My Windows 7 box doesn't have that problem. I can access my whole network from there.

Any ideas?

---

### Post by theozzlives on 2010-05-08
Bump

---

### Post by Jive Turkey on 2010-05-08
So windows can discover your shares on your samba box without having to type in the addresses but your ubuntu box can't browse the same way to other samba or windows shares?

make sure this line is uncommented in /etc/samaba/smb.conf
```
name resolver order = lmhosts hosts wins bcast 
```
Also, add the "browseable = yes" directives to your share definitions, and of course make sure all the samba ports are open in your firewall.
It might also help to have the ips and hostnames all set up your hosts file(s) everywhere.

I almost forgot, make sure everyone has the same workgroup setting.

---

### Post by theozzlives on 2010-05-08
> **Jive Turkey said:**
> So windows can discover your shares on your samba box without having to type in the addresses but your ubuntu box can't browse the same way to other samba or windows shares?

make sure this line is uncommented in /etc/samaba/smb.conf
```
name resolver order = lmhosts hosts wins bcast 
```
Also, add the "browseable = yes" directives to your share definitions, and of course make sure all the samba ports are open in your firewall.
It might also help to have the ips and hostnames all set up your hosts file(s) everywhere.

I almost forgot, make sure everyone has the same workgroup setting.

The line in the "Code" box is the only thing I haven't checked, but that didn't do it. I click on Places > Network and it winds up its "rubber bands", then just quits. Then a couple of seconds later Nautilus pops up with only Windows Network. I click on that and get my workgroup. I click on that and I get an "opening" dialog. Then a dialog comes up with "cannot retrieve share list from server".

The workgroup is MSHOME and all computers are set to that. I also have browsable = yes in my smb.conf on my server. I'm getting tempted to install a GUI on my server, but don't want to.

---

### Post by Jive Turkey on 2010-05-08
You could always bookmark the shares in nautilus as a workaround, the only other thing I can think of is setting the server to enable WINS if you haven't already.  It works on my LAN I have ufw rules to allow anything from my trusted IP's on the LAN.  I'm running lucid on all of them.  If you'd like to see any of my configs for comparison just ask.

---

### Post by theozzlives on 2010-05-08
> **Jive Turkey said:**
> You could always bookmark the shares in nautilus as a workaround, the only other thing I can think of is setting the server to enable WINS if you haven't already.  It works on my LAN I have ufw rules to allow anything from my trusted IP's on the LAN.  I'm running lucid on all of them.  If you'd like to see any of my configs for comparison just ask.

I already have by machines bookmarked, it's just easier to browse the network by name. WINS is an intriguing option.

---

### Post by Jive Turkey on 2010-05-10
Was experimenting and found that it doesn't always work for some reason for me either.  Some more investigation led me to try some new global directives  to smb.conf particularly the last two lines:
```

wins server = <ip of box a>
netbios name = <hostname>
dns proxy = no
name resolve order = lmhosts host wins bcast
client lanman auth = Yes
lanman auth = Yes
interfaces = <ip of box b (local)> eth0
bind interfaces only = yes
```
It seems to have made a difference for now but I haven't tested it that much.

I also found this thread that looks promising:
[http://ubuntuforums.org/showthread.php?t=388337](http://ubuntuforums.org/showthread.php?t=388337)

---

### Post by theozzlives on 2010-05-12
> **Jive Turkey said:**
> Was experimenting and found that it doesn't always work for some reason for me either.  Some more investigation led me to try some new global directives  to smb.conf particularly the last two lines:
```

wins server = <ip of box a>
netbios name = <hostname>
dns proxy = no
name resolve order = lmhosts host wins bcast
client lanman auth = Yes
lanman auth = Yes
interfaces = <ip of box b (local)> eth0
bind interfaces only = yes
```
It seems to have made a difference for now but I haven't tested it that much.

I also found this thread that looks promising:
[http://ubuntuforums.org/showthread.php?t=388337](http://ubuntuforums.org/showthread.php?t=388337)

Do I have this in my config of my laptop or server, and what about box c (the Windows 7 box)?

EDIT: Now my laptop isn't broadcasting the Host Name to my Windows 7 computer here's my config:

Workgroup = MSHOME
ozzie-laptop = 192.168.1.4 (wireless)
www-server = 192.168.1.6 (wired)
windows-7 = 192.168.1.3 (wired)

All computers can access the net fine, server is headless and IS the Lucid server software.

---

### Post by gwpritch on 2010-05-12
After migrating to lucid where I had so many problems I didn't know where to start, I went back to Karmic where I am now having a similar problem. Browsing shares worked fine before. My windows box is running XP. I would be interested in anyone's ideas on this.

---

### Post by gwpritch on 2010-05-12
Just found this. It didn't work for me but might for you:

[http://ubuntuforums.org/showthread.php?t=1480632](http://ubuntuforums.org/showthread.php?t=1480632)

---

### Post by theozzlives on 2010-05-13
> **gwpritch said:**
> After migrating to lucid where I had so many problems I didn't know where to start, I went back to Karmic where I am now having a similar problem. Browsing shares worked fine before. My windows box is running XP. I would be interested in anyone's ideas on this.

I went back to "good ole" Jaunty, same probs. I never had a prob with Jaunty before.

---

### Post by Scunnered on 2010-05-13
It appears that this is a big problem.  I have tried and tried to obtain a resolution to the problem but so far without any joy.

In post No 6 on [http://ubuntuforums.org/showthread.php?t=1471126](http://ubuntuforums.org/showthread.php?t=1471126) there was some way forward but as this went totally over my head I asked for further guidance but so far nothing has been given.

I think that I will findout how to seek a resolution via launchpad as this problem seems to be growing like mad and needs to be resolved quickly.

---

### Post by gwpritch on 2010-05-13
Oh man am I stupid. I thought I had done everything but I missed out adding host names to /etc/hosts.

```
sudo gedit /etc/hosts
```

below line that says something like '127.0.0.1  localhost'

add the IP addresses and names of other hosts on your network, including the IP and name of the local box.

eg 192.168.x.xxx  <name of host>  so you end up with something like this:
```
127.0.0.1     localhost
127.0.0.1   mycomputer.ipserver.com   mycomputer
192.168.0.100     mycomputer
192.168.0.101     hercomputer
192.168.0.102     hiscomputer
```

save and exit file. 

restart network.

Now I can browse my network to my hearts content.

Hope this helps someone.

---

### Post by theozzlives on 2010-05-13
Kool, that worked!

---

