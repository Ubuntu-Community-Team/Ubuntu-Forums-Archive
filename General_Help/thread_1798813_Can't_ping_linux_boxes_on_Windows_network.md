---
title: "Can't ping linux boxes on Windows network"
date: 2011-07-06
forum: General Help
---

### Post by Potters Son on 2011-07-06
I'm setting up an Ubuntu-based kiosk for my organization, and I can't seem to ping it by its hostname. The network is an Active Directory domain.

I tried editing /etc/dhcp3/dhclient.conf (I filled in the hostname where it said <hostname>), but no dice.

I also tried editing /etc/network/interfaces (the machine authenticates via DHCP but its network configuration is manually specified -- can't have users messing with NetworkManager):
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
        hostname <the computer's hostname here>
```

Finally, I tried joining it to the domain using likewise-open, and while it shows up in Active Directory, I still can't ping it.

Any ideas?

---

### Post by linuxuser12345 on 2011-07-06
Do the Linux machines have network and file sharing on? Do they have Samba installed?

---

### Post by Potters Son on 2011-07-06
For most of my testing, samba wasn't installed. Is it necessary?

---

### Post by drdos2006 on 2011-07-06
Looking through my notes as to previous problems relating to hostnames, I brought this up.
 
> 
Let me start with a little background info. I manage a computer lab with 85 workstations. I ocassionally use either RDP or VNC to do some maintenance. I have no problem doing this from windows, but I wanted my lonely Ubuntu workstation to be able to do the same thing. After about a week of research I am finally able to ping my windows workstations via their Netbios names. Woohoo!!

All you have to do is:

edit /etc/nsswitch.conf

change the line that says

Quote:
hosts: files dns
to this:

Quote:
hosts: files dns wins
finally, you need to install winbind

Code:

sudo apt-get install winbind

that's all that it took for me.

now ping <hostname> works great. And I can finally use the built-in terminal server client with hostnames instead of IP addresses.


I hope this brief guide can be of help! Thank you all for always providing such great support in these forums!


regards

---

### Post by Potters Son on 2011-07-06
> **drdos2006 said:**
> > ...I wanted my lonely Ubuntu workstation to be able to do the same thing. After about a week of research I am finally able to ping my windows workstations via their Netbios names.

Close, but unless I'm mistaken that's the reverse of what I'm trying to do.
I'm not trying to ping Windows computers from the linux machine (I was able to do this from a vanilla install!); I'm trying to ping the *Linux machine* from the *Windows computers*.

In testing, I'd set up a small LAN consisting of a couple computers with an Ubuntu machine functioning as the bridge to the rest of the internet, and I was able to get Linux machines to ping each other there. But when I try to connect Linux machines to the larger, network (which I'm told uses Active Directory for DNS), it doesn't work. So, among the things I've tried, I joined the kiosk machine to the domain. No dice, though.

---

### Post by Potters Son on 2011-07-06
Oh, and editing the /etc/hosts file manually is obviously out of the question, since it seems impractical to push out host definitions to every Windows machine on the network. I don't even have authority to do so.

---

### Post by drdos2006 on 2011-07-06
Have you added the GROUPNAME to the Samba config file ?
Have you updated the /etc/nsswitch.conf file ?
Have you installed winbind ?

regards
[edit]
Do you have shared folder on the linux box that the Windows box can access via "Network Neighbourhood" ?
In my setup I can access the linux share but not ping the box on one machine.
The second machine I can ping the box with the NetBios name.
I shall have to look into this further.
[/edit]

---

### Post by Potters Son on 2011-07-06
> **drdos2006 said:**
> Have you added the GROUPNAME to the Samba config file ?
Have you updated the /etc/nsswitch.conf file ?
Have you installed winbind ?

regards
[edit]
Do you have shared folder on the linux box that the Windows box can access via "Network Neighbourhood" ?
In my setup I can access the linux share but not ping the box on one machine.
The second machine I can ping the box with the NetBios name.
I shall have to look into this further.
[/edit]

No to the first two, and doesn't the third happen automatically when you install Samba?

I'll try this tomorrow. Thanks!

---

### Post by drdos2006 on 2011-07-06
I fixed the problem.
My desktop had a static IP that I had set up. I changed that to Dynamic. I also shortened my 14 char computer name to 9 chars computer name in the /etc/host file.
I can now ping both machines from the Windows machine.

regards

---

### Post by Potters Son on 2011-07-07
Well, today I tried pinging the linux computer from a Windows PC and was able to get through (Yesterday I was pinging from a linux machine). I honestly don't know if it's Samba or Likewise-Open doing it (I currently have both installed :-? ), and I still can't ping it from another linux machine, but this is good enough for me.

Thanks!

---

