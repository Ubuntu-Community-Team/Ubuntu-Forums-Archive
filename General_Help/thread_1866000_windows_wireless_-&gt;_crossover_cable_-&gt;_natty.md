---
title: "windows wireless -&gt; crossover cable -&gt; natty"
date: 2011-10-20
forum: General Help
---

### Post by cementtruck on 2011-10-20
I'm attempting to connect ubuntu Natty to windows vista using a crossover cable.  In windows I've created a Network bridge between the ethernet and wireless connections.  Ubuntu recognizes the connection by changing to the "socket icon" - a two way arrow icon.  

But,  I'm still not able to open a webpage from Ubuntu.  Any suggestions?  Please help.

I have enabled sharing from the windows wireless connection.

---

### Post by cementtruck on 2011-10-20
It's working now.  I deleted the connection bridge in windows and created a new one.  Perhaps this is why it is now working?

Here are the settings I have for my configuration in windows vista and natty
windows:
1.  click the wireless connection and the ethernet connection simultaneously -> bridge
2.  right click bridge -> properties -> check TCP/IPv6 & TCPIP/v4 -> properties -> connect automatically
3.  both networks and the bridge are located under the "Network Bridge (3)"

Ubuntu:
1.  Click connection icon -> Edit connections -> Auto Ethernet(highlight) -> Edit
2.  Check box "connect automatically"
3.  Wired - MAC addresses are both blank; MTU automatic
4.  802 tab.  Unchecked box
5.  IPv4 - automatic,  dhcp blank, box unchecked
6.  IPv6 - ignore

---

