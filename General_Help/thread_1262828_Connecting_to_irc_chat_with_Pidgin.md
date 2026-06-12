---
title: "Connecting to irc chat with Pidgin"
date: 2009-09-10
forum: General Help
---

### Post by hwttdz on 2009-09-10
Solved: solution, firewall problem, ports were blocked on my local network, ssh -X to a remote network and running pidgin from there got it done

I'd like to connect to some of the irc chats with pidgin and can't quite figure it out.  

Right now what I'm trying is 
accounts -> manage accounts -> add
protocol=irc
username (I can pick anything right? do I need to create this account somewhere else?)
password (I'm leaving blank)
server irc.freenode.net
local alias = "ubuntu irc chats"

Under advanced I've got
port 8001
encoding utf-8 (default)
username set to the same username as above
I didn't enter a real name or select use ssl
Finally it's using gnome proxy settings.

I get a "username@irc.freenode.net disconnected \n couldn't connect to host".  Any suggestions?  This is not the first time I've attempted to set up irc, which I would think would be pretty simple, and I wouldn't classify myself as a beginner user (I've successfully run a cluster, multiple webservers, a cvs repo), but irc seems to defeat me.  Thanks for any advice.

---

