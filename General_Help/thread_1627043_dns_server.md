---
title: "dns server"
date: 2010-11-21
forum: General Help
---

### Post by cschamber on 2010-11-21
hi, I've been using Ubuntu for almost a yr now and have learned more about computers than i have in the previous 12 yrs I've been on the Internet, but in all actuality I'm still learning lots of stuff. its mostly thanks to the Ubuntu community that I have really come as far as i have. now i have another question, i really need someone to explain to me in laymen terms what a DNS server is, how i can manipulate it, how it effects Internet speed, and the advantages and disadvantages of manipulating it on my laptop. thank you for your time.

---

### Post by maruchin on 2010-11-21
Hi,

a dns-server is a server, that translates a domainname into a IP.
Like ubuntuforums.org is translatet into 91.189.94.12
by "manipulating" i think you mean changing your dns-server.
In my opinion the easiest way is to open the /etc/resolv.conf
There you have your nameserver/s listed.
advantage/disadvantage....
well if you change it into a dns, that is not existent, you won't use the internet in it's original way :)
because if you type an url in your browser, it won't get the IP to it.
and, as far as i know, a dns server does not effect your internet speed.
well it's another "hop" in your route, but that is really nothing.

hope i could help you

regards
maru

---

### Post by cschamber on 2010-11-21
yes that actually helps a lot, i was asking all that info because i was searching ways to increase my Internet connection speed, and that kept coming up, I'm glad I asked before I actually tried doing it, or I might not have been able to ask about it LOL, again thank you for a great explanation

---

