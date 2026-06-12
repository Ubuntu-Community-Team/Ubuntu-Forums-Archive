---
title: "Wired LAN not working"
date: 2010-08-22
forum: General Help
---

### Post by grey1beard on 2010-08-22
I have been happily running EMC on 8.04 Hardy Heron since last year, with several updates during that time, but the last time was 139 days ago.
I connect the pc to the web via a Belkin "ASDL modem with wireless G", using a LAN connection, and until today all worked well.
Today, all attempts to use the update manager failed.
I brought my laptop(which uses a usb/Sagem router) into the workshop to test the line and that's OK.
The lights on the front of the router indicate both the PC and phone line are connected, but when I use the update manager, the pc led flickers(but not the line led), but it fails to download any files.
Each of the url's it tries to connect to "not resolved".
I tried launching Firefox with similar results, and I tried plugging in the laptop to a LAN connection on the Belkin with equal results.(That may be insignificant, as I can't remember if I set the laptop up to use the Belkin anyway.) :confused:

Right clicking on the wired network connection icon(which shows no activity) gave -
IP Address 192.168.2.2
Broadcast address 192.168.2.255
Subnet mask 255.255.255.0
Default route 192.168.2.1
Primary DNS 192.168.2.1
Secondary DNS 0.0.0.0
Hardware address 00:02:A5:B1:4B:46

While some of the above is just gobbledegook for me, I can follow explicit instructions.
Any help, especially with a view to increasing my understanding, would be greatly appreciated.
John

---

### Post by grey1beard on 2010-08-22
Further to the above.
A couple of months ago after my isp tiscali was taken over (?) by Talk Talk, I might have needed to change some settings for my connection in the house system(ie the laptop). 
These ancient brain cells can't remember if it was necessary or not for the laptop, but I certainly haven't changed anything in the workshop router, as I haven't been out here for 139 days, according to the update manager !
Is this the problem ?
If so, I've no idea what to do next.
John

---

### Post by jward3010 on 2010-08-22
Well we should first test the basics and see if you're ethernet connection is actually sending packets.

Go to terminal and type:
```
ping -c 3 8.8.8.8
```
If you get "successful" replies back then your network card and driver ARE ok. You may have a DNS issue after that, you may have set a manual IP in the past which is on a different subnet to your current network or you're broadband may actually be dead as ducks.

---

### Post by anirudhtomer on 2010-08-22
Are u able to ping your router?...like at home I have 192.168.1.1 as my router address

Check your /etc/resolv.conf file as well. It should have the IP of the DNS server which resolves the domain names of various sites.

---

### Post by grey1beard on 2010-08-22
Thanks guys.
I tried pinging 8.8.8.8 but I got three lines
"From 192.168.2.1 icmp_seq=1 Destination net unreachable"
ditto seq=2, ditto seq=3.

---

### Post by grey1beard on 2010-08-22
I tried pinging 192.168.2.1 (my default route) and got "3 packets xmitted, 3 received."
Ditto for 192.168.2.2

How do I "Check your /etc/resolv.conf file as well." It should have the IP of the DNS server which resolves the domain names of various sites.

Seems incongruous to be a total newb at 72 !
John
PS found and opened etc/resolvconf (no dot) but this only contaned update-libc.d, and this contained avahi-daemon greyed out.

---

### Post by QLee on 2010-08-23
[QUOTE=grey1beard]...
Seems incongruous to be a total newb at 72 ![/QUOTE]
Not to me, I know there are a few things I haven't yet done and that is all it takes to be a newb at something.


[QUOTE=grey1beard]PS found and opened etc/resolvconf (no dot) but this only contaned update-libc.d, and this contained avahi-daemon greyed out.[/QUOTE]

That was a directory (folder). What anirudhtomer wanted you to look at was a file (further down the directory tree, below the folders). The file does have the dot.

---

### Post by grey1beard on 2010-08-23
> **QLee said:**
> 
That was a directory (folder). What anirudhtomer wanted you to look at was a file (further down the directory tree, below the folders). The file does have the dot.

Thanks QLee, something new learnt - a good day.

I've now managed to identify the source of the problem, the clue being in my remembering the change of isp.
Problem at the time required me to change my log on password, and I had overlooked the need to change this in the router settings, which I only need for the workshop system. (See "139 days...":rolleyes:

Problem solved.
Thanks all.
John

---

