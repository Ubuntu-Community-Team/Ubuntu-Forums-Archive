---
title: "some info"
date: 2010-04-24
forum: General Help
---

### Post by freeway29 on 2010-04-24
Hi all im a long time windows user and just installed Ubuntu 9.10 and have heard that i dont need any antivirus or spyware program on it, also is the firewall enabled by default if there is one and last thing do you need to do things like disk clean and defrag if so how thanks.

---

### Post by howefield on 2010-04-24
Here's a couple of links to start you off.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by themusicalduck on 2010-04-24
Welcome to Ubuntu :)

It's true you don't need any antivirus or spyware software. Linux viruses are virtually non-existant, although it's sometimes good to scan files if you are transferring or sending them to people with windows computers. For this purpose you could install clam, which should be in the Software Centre under Applications.

The firewall isn't enabled by default, you could enable it in the command line (Applications > Accessories > Terminal) with ```
sudo ufw enable
``` or ```
sudo ufw disable
``` to disable it.

Or you could install a graphical interface for it if you search for firewall configuration in the software centre.

You don't need to worry about defragging generally. Some people say it's necessary, some say it isn't. I haven't bothered to and I haven't noticed any slowdowns. As for disc clean, I think there are some applications, but whatever you do don't use Computer Janitor (installed by default for some reason), it is notorious for causing people problems.

Also worth mentioning, there is a new release coming out on the 29th - 10.04, which is a long term support release, which means you won't need to upgrade it to the next release for 3 years. It's definitely worth trying that out if you want to. You could even try the release candidate which is for download from the front page of [www.ubuntu.com](www.ubuntu.com)

Hope this is helpful.

---

### Post by freeway29 on 2010-04-24
Thanks heaps for replying so fast and yes very helpfull.

---

### Post by freeway29 on 2010-04-24
Hey just want to know i just tried to request the new 10 ubuntu and it said ship it is closed beck in few days , so does that mean ill still be able to get it but later or what any ideas.

---

### Post by 3rdalbum on 2010-04-24
> **freeway29 said:**
> Hey just want to know i just tried to request the new 10 ubuntu and it said ship it is closed beck in few days , so does that mean ill still be able to get it but later or what any ideas.

This is really a different topic, but yes when 10.04 is released you'll be able to request it through ShipIt.

I'll just add something about your previous topic. On Windows you need a firewall because components of Windows listen for incoming connections, and attackers can take advantage of those components to attack your system and plant malware.

On Ubuntu, by default there is NOTHING listening for incoming connections, so to outside appearances it's the same as having a firewall. If you install something that listens for incoming connections (such as an FTP server or Bittorrent client) then you probably want it to listen anyway, and a firewall still won't do anything useful.

So if you want to enable a firewall, go ahead. I've never had one turned on apart from the one on my router (which protects my whole network), and even when I'm outside my network on mobile broadband I still don't bother with a firewall because nothing on Ubuntu is listening for connections.

---

### Post by howefield on 2010-04-24
Yes, you should try back in a few days as it suggests and you should be able to order a CD.

Note : There were some changes to shipit availability when Karmic was released, essentially, shipit is aimed at those who cannot download a copy.

---

