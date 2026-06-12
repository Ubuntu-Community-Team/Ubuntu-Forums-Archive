---
title: "Network Problems"
date: 2010-12-19
forum: General Help
---

### Post by routumuro on 2010-12-19
Hello, my name is Rodrigo, I'm an _absolute newbie_ in Ubuntu, so please keep that in mind.
   I have installed it a couple of days ago, and everything's working just fine except for my network connections. There are other computers in my house (all with Windows), and there's a big hard drive with music for everyone to access through LAN connections. My internet connection works fine, but when I try to access this hard drive an error pops up and the folder crashes and I'm forced to quit. 
   I've taken a picture of the error.

I'd be most grateful if anyone would give me a hand.

Thanks again.

Rodrigo

---

### Post by unplugged23 on 2010-12-19
I've never tried using ubuntu to access a home server before, but the same problem seems to be discussed here: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8839731](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8839731)

Hopefully this is what your looking for, if not let us know!

---

### Post by techunit on 2010-12-19
Sorry Mate, I can't help ya hear, although the home server idea seems somewhat probable. I think the networked drive should just appear on your desktop or in Computer. I hope this helps in some remote way, and gives you an idea on what to do.

Best of hopes to ya.

---

### Post by Ceiber Boy on 2010-12-19
The HDD should show up in your <places> <Network> folder if not you can find out all the ip addresses on your LAN using the 'nmap -sP 192.168.1.0/24' command. if nmap is not installed use 'sudo apt-get install nmap'.

this will give you all the ip addresses. once you knoe the addresses you can start using the <Places> <connect to a server ..> use the fields 'service type' and 'server' in the server field type the ip address of the service you wish to connect to, in the service type select your protacal, you would be able to access your other windows machines if they have sharing turned on.

hope this helps

---

### Post by routumuro on 2010-12-20
Thanks a lot! Problem solved!

---

