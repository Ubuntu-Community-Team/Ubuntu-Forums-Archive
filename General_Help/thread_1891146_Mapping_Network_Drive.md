---
title: "Mapping Network Drive"
date: 2011-12-05
forum: General Help
---

### Post by erbad on 2011-12-05
On my home network, I have 4 computers, 2 Windows based (Win XP, Win 7) and 2 Ubuntu computers.

On one of my Ubuntu computer, if I click on places, network, I see the two Windows based computers, but the other Ubuntu computer does not show up.

What do I need to do to get this one to show up?

Thank you

---

### Post by Morbius1 on 2011-12-05
Based solely on your description of seeing every machine on your network except one Ububntu machine I suspect that it's name is too long. By default Samba will use the host name of the machine as the name it presents itself to the rest of the network ( the netbios name ) but it has length restrictions.
[COLOR=Blue][B]
EDIT:[/B][/COLOR] The first thing you should do on the box you can't see is make sure a service is running:
```
 sudo service nmbd status
```
If it's not running start it:
```
sudo service nmbd start
```

Go to the Ubuntu machine you cannot see and run the following command:
```
hostname
```Count the number of characters and if it's 16 characters or longer you need to change it. The easiest way is to leave the hostname as it is and change the netbios name itself in a configuration file:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section - I would put it right under the "workgroup" line:
```
netbios name = something
```[COLOR=Blue]Change [COLOR=Black]something[/COLOR] to any name you want as long as it's 15 characters or less in length.[/COLOR]

Save smb.conf and then restart samba:
```
sudo service smbd restart
```If that doesn't work by itself or there was not a problem with the host name length and you don't have something else in the way on that box like a firewall for example then you might want to change the order of the way that box resolves names:

Edit smb.conf again and add another line - right under workgroup:
```
name resolve order = bcast host lmhosts wins
```Then save it and restart samba again.

Note: Every time you restart samba the network has a fit so give it a few minutes to settle down before trying to access this machine.

---

