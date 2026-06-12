---
title: "How To Map Network Drives"
date: 2012-05-19
forum: General Help
---

### Post by carmenin87 on 2012-05-19
I have network shares on a Windows computer and an Ubuntu computer.

When I want to map a drive to these shares from another Ubuntu computer, I have to use the IP address, which I always forget.

Using places=>connect to server=>Windows share, is there a way to map a network drive using the computer name rather then the IP address?

Right now when I try it this way (\\server name\share), I get the error "failed to retrieve share list from server".  However, if I map using \\192.168.1.5\share, it works.

Thank you

---

### Post by bodhi.zazen on 2012-05-19
You either need to add an entry in /etc/hosts or use a dhcp server.

```
gksu gedit /etc/hosts
```

Add an entry for your server

server_ip server_name

---

### Post by carmenin87 on 2012-05-19
> **bodhi.zazen said:**
> You either need to add an entry in /etc/hosts or use a dhcp server.

```
gksu gedit /etc/hosts
```

Add an entry for your server

server_ip server_name

The only thing is that the home network is DHCP so sometimes when these workstations boot up, they get a different IP address.

Rather then putting entries in the file which could potentially change, isn't there some code that could be downloaded from the repositories that would recognize computer names so I can move away from IP addresses.

---

### Post by bodhi.zazen on 2012-05-19
> **carmenin87 said:**
> The only thing is that the home network is DHCP so sometimes when these workstations boot up, they get a different IP address.

Rather then putting entries in the file which could potentially change, isn't there some code that could be downloaded from the repositories that would recognize computer names so I can move away from IP addresses.

Set static ip addresses. This can be done from the router (most routers will do this) or clients.

If you have multiple clients, you will need a dns server, dnsmasq will do all this for you.

---

### Post by redmk2 on 2012-05-19
> **carmenin87 said:**
> The only thing is that the home network is DHCP so sometimes when these workstations boot up, they get a different IP address.

Rather then putting entries in the file which could potentially change, isn't there some code that could be downloaded from the repositories that would recognize computer names so I can move away from IP addresses.
No need to download anything.  You need can force the host to broadcast its NETBIOS name on the  local subnet regardless of what its IP address is.  Since both Windows shares and Samba on Ubuntu use NETBIOS names ultimately this is all you need.

See [**_[COLOR="RoyalBlue"]here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11951371&postcount=3") for how to do this.

---

### Post by Morbius1 on 2012-05-20
In addition to what redmk2 posted you might want to make sure that the name it's broadcasting is legitimate. The hostname name automatically becomes the netbios name in a default install so count the number of characters in your host name. If it's 15 characters or less in length then you're fine. If it's 16 characters or more then you need to change it.

You can do that for samba purposes in smb.conf itself by adding a line to the [global] section:
```
netbios name = something
```[COLOR=Blue]*Just make sure "something" is 15 characters or less in length.*[/COLOR]

---

