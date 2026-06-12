---
title: "Ubuntu 9.04 Vuze problems"
date: 2009-10-20
forum: General Help
---

### Post by aust77 on 2009-10-20
I apologize if this is in the wrong section; I am new and believe that this can be called general. I am not too much of a newbie with Ubuntu, but I have much to learn. I am running 9.04 Jaunty, and recently got into torrenting. I used Transmission for some time but switched to Vuze as it is much more in-depth. I downloaded a torrent, but my upload rate was extremely slow and after about a GB of uploads, it completely stopped. The torrent icon was yellow, signifying a NAT problem. My connection comes from a household wireless network, running Windows. My webmaster opened a port I requested, 44977, so I would be able to be "connectable" and seed on Vuze. I also made sure this port was opened but running several recommended commands, mainly using iptables, but they were posts from long ago and several versions ago. Vuze is still telling me that I have a NAT problem, though I have done everything in my knowledge to fix it. To be slightly more specific, here are two commands I issued:
[I]iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
[/I] *iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT*


I also created a file and made it excecutable, according to what the Azureus wiki recommended:




      **create a file** /etc/init.d/iptables_azureus **and add the lines below**
        (sleep 220
         /sbin/iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
         /sbin/iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT ) &


Finally, I ran some commands to make it excectable:
   chmod +x /etc/init.d/iptables_azureus **make the file executable**
   update-rc.d iptables_azureus start 51 S . [B]links the file into the startup sequence

[/B]I am new to these type of things and all I need is one port opened. Can anyone help? Any remote assistance would be greatly appreciated. Thanks,


Aust77
Ubuntu "Jaunty" 9.04

---

### Post by mikewhatever on 2009-10-20
You don't have to mess with iptables because by default. Ubuntu doesn't restrict connections. I think the problem is either with your router or your ISP.

---

### Post by lovinglinux on 2009-10-20
[BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by aust77 on 2009-10-21
Started using Deluge, as recommended by your guide. It works great. Thank you, lovinglinux and mikewhatever for helping me.

---

### Post by lovinglinux on 2009-10-21
> **aust77 said:**
> Started using Deluge, as recommended by your guide. It works great. Thank you, lovinglinux and mikewhatever for helping me.

You are welcome.

I'm using Ktorrent since I moved to KDE. It has some nice advanced features like vuze, but not bloated as the first. So Deluge and Ktorrent are my choices for each Desktop Environment.

---

### Post by aust77 on 2009-10-22
The bright beginning of my usage of Deluge has dragged down, unfortunately. The port reads as closed. but within my **own** computer, not my network host's. He can connect to the port with ease, while mine is closed. I used several techniques to find if it was open, and often the problem was that the connection timed out to my computer's IP address. Any solutions? I have skimmed through lovinglinux's guide without any results. If I am missing something, please let me know ASAP.

---

### Post by aust77 on 2009-10-22
SUCCESS! My network admin changed the port forwarding settings, and now canyouseeme.org reads port 44977 as open. Thanks a million lovinglinux for your great guide.

---

### Post by lovinglinux on 2009-10-22
> **aust77 said:**
> SUCCESS! My network admin changed the port forwarding settings, and now canyouseeme.org reads port 44977 as open. Thanks a million lovinglinux for your great guide.

You are welcome again :)

---

### Post by aust77 on 2009-10-23
I hate to be revisiting this same topic yet again, but now it is not downloading, but uploading, that is my problem. I have set my outgoing port on Deluge to 44977, the same one I use for downloading. I am downloading a torrent which has seven peers, all leechers, on it, because I want to seed when I'm finished so my ratio goes back to normal. Unfortunately, Deluge does not connect to any of these peers, a problem I experienced previously, but it didn't matter as there was ten seeders. Does a conflict occur if the download and upload ports are the same? Thanks,



aust77

---

### Post by lovinglinux on 2009-10-23
> **aust77 said:**
> I have set my outgoing port on Deluge to 44977, the same one I use for downloading...Does a conflict occur if the download and upload ports are the same?

That's the problem. Select the "Random Ports" option for uploading and use the port 44977 only for downloading.

---

### Post by aust77 on 2009-10-23
Unfortunately on my router, all other ports than 44977 and the necessary ones are blocked. Will this affect it? Can I just use a separate port? And should I use a port in the dynamic range instead of 44977?

---

### Post by lovinglinux on 2009-10-23
> **aust77 said:**
> Unfortunately on my router, all other ports than 44977 and the necessary ones are blocked. Will this affect it? Can I just use a separate port? And should I use a port in the dynamic range instead of 44977?

No. Outgoing ports are not affected by the router settings. Use random ports for outgoing, this is the correct way of doing it, since each connection to a new peer will select the first available port. Use only port 44977 for incoming. If you use a dynamic range instead, you will have to open the entire range in the router.

---

### Post by aust77 on 2009-10-23
All settings are good, and everything seems to be working. I guess you can say this topic has reached it's conclusion. But, quickly, one final question: Is it normal if Deluge does not upload much when downloading the file? Does it only upload at a consistent rate when seeding?

---

### Post by lovinglinux on 2009-10-24
> **aust77 said:**
> All settings are good, and everything seems to be working. I guess you can say this topic has reached it's conclusion. But, quickly, one final question: Is it normal if Deluge does not upload much when downloading the file? Does it only upload at a consistent rate when seeding?

That depends on several factors, but usually it does upload at max speed. You probably are connected to too many seeders and the peers that are downloading from you probably have reached their download speed limit. So you still have bandwidth to upload, but the peers cannot get more.

---

### Post by aust77 on 2009-10-24
I am very desperate as I am on the verge of getting banned from a great torrent site. Deluge has been seeding for twelve hours now, yet has only seeded roughly 200 MB compared to 4 GB downloaded. I have done everything according to your guide. PLEASE HELP!


EDIT:There are 4 connected peers on the torrent I'm seeding, yet it isn't seeding at all. I do not want to get my IP banned from a great torrent site. PLEASE.

---

### Post by lovinglinux on 2009-10-24
> **aust77 said:**
> I am very desperate as I am on the verge of getting banned from a great torrent site. Deluge has been seeding for twelve hours now, yet has only seeded roughly 200 MB compared to 4 GB downloaded. I have done everything according to your guide. PLEASE HELP!


EDIT:There are 4 connected peers on the torrent I'm seeding, yet it isn't seeding at all. I do not want to get my IP banned from a great torrent site. PLEASE.

I'm afraid you won't able to increase your upload speed with just 4 connected peers. There is nothing you can do (on a private tracker) if the torrent is not popular. There is probably enough seeders on the swarm to keep the peers bandwidth at maximum, otherwise their client would request additional pieces from you. Try to seed a more popular torrent or leave the torrent seeding until someone else joins the swarm.

---

### Post by aust77 on 2009-10-24
I apologize heavily for my bombardment of questions, but I believe this is the final, final piece of info i need. When I set my upload port to 44977, ilovetorrents.com reads me as "Connectable" which is considered a good thing. But when I set my upload ports to random, I am no longer connectable, though I can connect to more peers. How can I configure it so I connect to peers but am Connectable at the same time?

---

### Post by lovinglinux on 2009-10-24
> **aust77 said:**
> I apologize heavily for my bombardment of questions, but I believe this is the final, final piece of info i need. When I set my upload port to 44977, ilovetorrents.com reads me as "Connectable" which is considered a good thing. But when I set my upload ports to random, I am no longer connectable, though I can connect to more peers. How can I configure it so I connect to peers but am Connectable at the same time?

See this:  [http://trac.transmissionbt.com/ticket/776](http://trac.transmissionbt.com/ticket/776)

---

### Post by aust77 on 2009-10-24
It reads me as still connectable, even with random ports after I checked again. I will bookmark that in case I need to refer to it, and I will do the same with your optimization guide. For now, I need to "seed" back the questions I've asked and help out some others :) . If I have any problems, which is doubtful, I will create a new topic, as I don't even use Vuze. I can't thank you enough lovinglinux, for having taken time to assist a newer Ubuntu user. I will for sure be using Ubuntu from here on in as I won't have to switch to Windows, since my BitTorrent is configured. Thanks,



aust77

---

### Post by lovinglinux on 2009-10-24
> **aust77 said:**
> It reads me as still connectable, even with random ports after I checked again. I will bookmark that in case I need to refer to it, and I will do the same with your optimization guide. For now, I need to "seed" back the questions I've asked and help out some others :) . If I have any problems, which is doubtful, I will create a new topic, as I don't even use Vuze. I can't thank you enough lovinglinux, for having taken time to assist a newer Ubuntu user. I will for sure be using Ubuntu from here on in as I won't have to switch to Windows, since my BitTorrent is configured. Thanks,

aust77

You are welcome.

> **aust77 said:**
> For now, I need to "seed" back the questions I've asked and help out some others :) 

Hehehe, funny analogy. That's the spirit.

---

