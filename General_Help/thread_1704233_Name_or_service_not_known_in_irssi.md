---
title: "Name or service not known in irssi"
date: 2011-03-10
forum: General Help
---

### Post by ToJa92 on 2011-03-10
Hello, I was using irssi just fine yesterday until I wanted to add more networks and servers. After quiting the only network I was on at that time(Sorcerynet), I tried to restart irssi and instead of connecting as it should, I got this:

> 
[18:28:39] [Sorcery] -!- Irssi: Unable to connect server irc.sorcery.net port 9999 [Name or service not known]
[18:28:39] [irchighway] -!- Irssi: Unable to connect server irc.irchighway.net port 9999 [Name or service not known]
[18:28:41] -!- Irssi: Unable to connect server lindbohm.freenode.net port 7000 [Name or service not known]
[18:28:41] -!- Irssi: Removed reconnection to server chat.freenode.net port 6667
[18:28:41] -!- Irssi: Looking up chat.freenode.net
[18:28:43] -!- Irssi: Unable to connect server chat.freenode.net port 6667 [Name or service not known]
First I thought something was wrong with the internet connection, but then I tried "telnet irc.sorcery.net 9999" and it connected successfully:
> 
$ telnet irc.sorcery.net 9999
Trying 75.119.201.232...
Connected to irc.sorcery.net.
Escape character is '^]'.
Connection closed by foreign host.
So question is, did I break irssi? I'm running the SVN version(pretty sure it's the newest one).

Also, it's on a server so I can only SSH in(and get root if I want), no GUI.

PS: I hope I put this in the right category ;)

EDIT: Fixed by moving my config file. Seems like irssi doesn't like multiple networks, or something.

---

