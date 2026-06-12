---
title: "Internet disconnects shortly after logon"
date: 2006-06-08
forum: General Help
---

### Post by SSB on 2006-06-08
On the live CD my internet worked perfectly so I have no idea what could be causing this...

My internet disconnects about 15 seconds after i log on to the system. Meaning it is connected for the 15 seconds prior to that. I can do anything normally, then it just dies out.

I'm VERY new to Linux so I may be missing something.. I've checked my eth0 connection and it said I had a few error'd packets. None of the networking tools gave me any results (I tried to ping 192.168.1.1 and I got nothing)

Any ideas? Remember that I'm new so the more technical answers I will need some help with. A lot of different things from windows here :O

---

### Post by bionnaki on 2006-06-08
what is your setup? dhcp? router?

---

### Post by SSB on 2006-06-08
WRT54G linksys router (if you needed that), I'm connected via ethernet so it's not a wireless problem. DHCP is enabled.

---

### Post by bionnaki on 2006-06-08
did you enter the correct dns?

---

### Post by SSB on 2006-06-08
I'm.. not sure. The DNS server is typically the default gateway, right?


I never had to do that on the live CD though..

---

### Post by bionnaki on 2006-06-08
no.
open up your router interface when you're online (open firefox and go to 192.168.1.1) and then go to the "status" tab. see what your dns is.

should be a typical IP address. enter this number (I have two with comcast) into your network manager.

---

### Post by SSB on 2006-06-08
In the network properties it already has 2 IP addresses there. I'll go double check to confirm that they are the same..

---

### Post by SSB on 2006-06-08
bump

---

### Post by Video Toaster on 2006-06-08
Don't DNS addresses get assigned by DHCP, though?

---

### Post by scxtt on 2006-06-08
if you're using DHCP you shouldn't need to enter anything - at all ...

and if you can't ping 192.168.1.1 it seems like there's a problem -- assuming that's the address your router uses, i have a linksys as well and i've never changed it to be anything else ...

i can ping 192.168.1.1 w/ no problem ... i'd check your router config first ...

---

### Post by SSB on 2006-06-09
thing is, scxtt, I can get into my router config page before the internet goes out. I'm connected for about 20 or so seconds, EVERYTHING works perfectly. It dies and I can't access any kind of network. I open up the network properties and it says that eth0 is have a lot of error'd packets. The ipv6 tab is fine. It's eth0 with about as many error'd packets as received packets.

---

### Post by scxtt on 2006-06-10
i don't know much about ipv6, but i've read that i can make things difficult at times ... what's your hosts tab contain under "network settings"?

and did you mean to say you "CAN'T get into my router config page before the internet goes out."?  if you can before and after, do you notice any differences in DHCP status after things stop working? ... almost sounds like your router is releasing your DHCP connection for no reason ...

---

### Post by SSB on 2006-06-10
[http://ubuntuforums.org/showpost.php?p=1116327&postcount=9](http://ubuntuforums.org/showpost.php?p=1116327&postcount=9)


Solution found. Thank you for your help, though. It's a very peculiar problem..

---

