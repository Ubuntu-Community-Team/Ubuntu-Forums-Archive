---
title: "Transmission issues ( &quot;checking port ..&quot; ) - help appreciated !"
date: 2009-07-08
forum: General Help
---

### Post by credobyte on 2009-07-08
Any ideas ? Why it's not working ? I've tried various torrents and Transmission does not start downloading process ( waited for hours ).

[[IMG]http://img516.imageshack.us/img516/9812/transmissionportcheckin.th.png[/IMG]](http://img516.imageshack.us/i/transmissionportcheckin.png/)

---

### Post by moster on 2009-07-08
You did not tell that various torrent apps worked or not. If they worked do not waste time with transmission.

If you must use transmission look at that other apps what is their port number and copy it to transmission.

If torrent are not working in any app, including transmission then you must login to your router and enable NAT-PNP or open some port manually. It is not that hard, just open something like 50000.

Go here for instructions on that. [http://portforward.com/ ]("http://portforward.com/")

---

### Post by credobyte on 2009-07-08
[LIST=1]
[*]I'm not behind a router !
[*]I have no problems in downloading torrents from other clients ( deluge, vuze, etc. )
[*]Port is closed ( can't be reached ) - that's why I made this thread .. to get some answers ( probably on how to open this port ).
[/LIST]

---

### Post by moster on 2009-07-08
Well, what is stopping you to copy port number to transmission and try with that port? Maybe just that default transmissions port is blocked because God knows what reason.

You can try to disable that NAT PNP in transmission.

---

### Post by credobyte on 2009-07-08
Port changed - still nothing ( "testing port" ).
NAT thingy disabled - still nothing .. :(

---

### Post by moster on 2009-07-08
If I were you, I would go to transmission site, on their irc channel and ask them directly what could it be.

[http://www.transmissionbt.com/resources.php](http://www.transmissionbt.com/resources.php)

You also can try beta, they have some version for ubuntu.

edit:
Transmission lack of some features so it is not exactly fastest torrent around. It is quite minimalistic, I like that. I would be using it if he could use UDP trackers, be he cant for now.

---

### Post by credobyte on 2009-07-08
Not sure what it was, but .. [COLOR=Blue]iptables[/COLOR] and [COLOR=Blue]allow established[/COLOR] solved this problem !

---

