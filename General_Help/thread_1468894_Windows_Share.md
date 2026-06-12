---
title: "Windows Share"
date: 2010-05-01
forum: General Help
---

### Post by francois203 on 2010-05-01
Hi,
I have lucid but I had the same problem with karmic.
I am unable to use windows share.


When I go to Places --> Network --> Windows Network, I get this message:

Unable to mount location
Failed to retrieve share list from server


And when I go to System --> Administration --> Printing, and then Add Printer --> Windows Printer via SAMBA --> Browse, I get this message:

There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration.
To do this, select System->Administration->Firewall from the main menu.


I tried many different things (installing samba, following this tutorial: [http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")) but nothing worked.

Any idea?

---

### Post by maxnutter on 2010-05-01
I've just developed a similar issue, with the same error message after upgrading to 10.04... argh!

---

### Post by fenian on 2010-05-01
I solve this problem by installing winbind...

> sudo apt-get install winbind

I then edit the nsswitch file...

> gksudo gedit /etc/nsswitch.conf

Change the ¨hosts: line to look like this...

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Reboot and you should see the network shares.

---

### Post by 3rdalbum on 2010-05-01
Turn off your firewall on the client. That's right: On the client.

Otherwise, you can connect via IP address. If you go to the location bar in Nautilus, type:

smb://

then the IP address, then a slash and then the name of the shared folder.

---

### Post by Ginsu543 on 2010-05-02
I was able to work around this problem by doing the following:

1) Open Terminal
2) Run: sudo gedit /etc/hosts
3) Add the IP address and name of the samba share:

```

127.0.0.1    localhost
127.0.1.1    Ginsubuntu
[B]
# IP addresses for home network
192.168.0.xxx    Miniserver
[/B] 
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```I've bolded the appropriate section for effect. Once I did this, I found that I could easily access my samba share on Miniserver (the name of my home server on which my samba share resides) either through the Network tab in Nautilus or by typing smb://miniserver/name_of_shared_folder in the Location bar.

---

### Post by francois203 on 2010-05-02
None of that worked...

---

