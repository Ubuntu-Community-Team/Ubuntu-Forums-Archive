---
title: "Connect two pcs, one firewalled."
date: 2006-06-05
forum: General Help
---

### Post by valfreixo on 2006-06-05
I have two pcs that i wish to connect. I have one at home, directly connected to the internet and another one at the office behind a firewall. I can access home pc with ssh, no problem. So when i'm at work i can fetch all things i've did on the previous night and scp them to my office disk and continue my work.

However i don't know how to do the oposite. I know that there's a way to establish some sorte of VPN between the two computers, just don't know how. In here i'm the only *ix user so i can't ask no one else. Can anyone point me a way to do it? 

Thank you ppl.

Ricardo

---

### Post by NiceGuy on 2006-06-05
Well... there are several ways of sorting this one! The easiest way would be to ask whoever is in charge of your office IT to open/forward a port that you can use for a ssh connection. But since your posting here I'm guessing thats not an option. 

Failing that have a look at [hamachi]("http://www.hamachi.cc").

Hamachi sets up a secure vpn and from memory I don't **think** you need to open any ports in your firewall to use it. I'm guessing thats becuse you connect to the hamachi servers first and then you make the vpn connection. I could be wrong but that sounds about right. Anyway here is a really good howto which worked for me:

[http://www.ubuntuforums.org/showthread.php?t=135036](http://www.ubuntuforums.org/showthread.php?t=135036)

Good luck

---

### Post by valfreixo on 2006-06-05
I've already tried that one. On a VPN with more computers, the windows computers "see" the linux ones, but the oposite is not true. I guess hamachi not stable on the *ix platform...

---

### Post by NiceGuy on 2006-06-05
Hurm, thats very odd! So with hamachi running your windows computer (the one at work I assume) can seen the linux one (the one at home) but not vice versa?

Just to clarify what do you mean by 'see'? Do you mean that you can access your shared folders on your linux machine, via the vpn, on your windows machine but you can't do the reverse OR do you mean that when you logon to the hamachi network the linux machine appears online (when you look at the gui in windows) but when you get home the window machines appears offine to your linux machine?

The reason I ask is that if it the latter that does seem line a problem with hamachi (maybe try a different version - I hear the 1.0 beta is out) if its the former it might be something to do with your samba settings (are you part of the same workgroup etc.).

---

### Post by valfreixo on 2006-06-05
I've just found out what the problem was. Some admin here code a small app that detects persistent connections on through the firewall and terminate the connection after a few hours. It is done to prevent ppl to do ilegal downloads during the night. now it's of and hamachi's working!

---

### Post by NiceGuy on 2006-06-05
Yep that would explain it :p

---

