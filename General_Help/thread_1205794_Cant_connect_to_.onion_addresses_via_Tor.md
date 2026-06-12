---
title: "Cant connect to .onion addresses via Tor"
date: 2009-07-06
forum: General Help
---

### Post by BigB'sLinux on 2009-07-06
Hello everyone,    Not really new to Linux so I posted this here. If it needs to be moved so be it, I did my best. I am using Ubuntu Live CD 9.04    My problem is I have Tor installed and it works well, shows usability on torcheck, but I cannot connect to .onion addresses..? -------------------------------------------------------------------------  Like I said [https://torcheck.xenobite.eu](https://torcheck.xenobite.eu) shows everything is on time, however a more in depth check at metasploit's decloak.net shows this: -------------------------------------------------------------------------     External Address     83.91.86.29    Browser Internal Host     unknown    Java Internal Address     unknown    Java  DNS Server (Java)     unknown    Java DNS Server (HTTP)     151.164.11.206    Browser DNS Server (FTP)     151.164.11.206    Browser DNS Server (Word)     unknown    Office DNS Server (iTunes)     unknown    iTunes DNS Server (Quicktime)     151.164.11.209    Quicktime  External NAT (FTP)    83.91.86.29    Browser External NAT (Java)    unknown    Java External NAT (Flash)    unknown    Flash External NAT (Word)    unknown    Office External NAT (iTunes)    unknown    iTunes External NAT (Quicktime)     83.91.86.29    Quicktime       I am NOT in Missouri as the above IP: 151.164.11.209  suggests.  --------------------------------------------------------------------------  I added the line &quot;forward 4a socks&quot; line in the privoxy config file to see if that would change things, but it didnt..any suggestions as to why this is happening.  --------------------------------------------------------------------------    History:  I installed Tor via copying to my /etc/apt/sources.list, sudo aptitude update , sudo apt-get install tor. Then FoxyProxy and all the necessary addons(no script,cookie safe, etc.) Like I said Tor is working beautifully its only when I try to connect to onion forums or any .onion address that the problems start.. Do I need to config something??   --------------------------------------------------------------------------   Any help would be greatly appreciated I have a server running on .onion and am sick of windoz. Wish I could fully install Ubuntu on my HDD, but I have to decrypt my system first. Thanks   --------------------------------------------------------------------------- [Sorry couldnt format this the way I wanted too, BB'sLinux]

---

### Post by michy99 on 2009-07-06
I had a little trouble reading your post, but it looks like the line you put in the privoxy config file is```
forward 4a socks
```The line needs to be```
forward-socks4a / 127.0.0.1:9050 . 
```Note the period at the end.

If you want to put text in a code box, select it and press the # button at the top of the edit area.

EDIT: got it wrong the first time.

---

### Post by Soul-Sing on 2009-07-06
I have [COLOR="Red"]much[/COLOR] trouble reading your post. Really, and I am fam. with TOR/ vidalia/ etc. (not really using it very much though..)
A more in depth check at metasploit's decloak.net....what are you checking there?

---

### Post by BigB'sLinux on 2009-07-06
Tried that yesterday, but ill give it another go..?

---

### Post by BigB'sLinux on 2009-07-06
Metasploit decloak does a thorough check and tries to snatch your IP using flash, javascript, media players, etc..just a much stronger check then torcheck

---

### Post by Soul-Sing on 2009-07-06
> **BigB'sLinux said:**
> Metasploit decloak does a thorough check and tries to snatch your IP using flash, javascript, media players, etc..just a much stronger check then torcheck

Ok thx. And you expect TOR to pass this test...
This forum has some (one?) great howto's how to set up TOR.
The off. sites: [http://www.torproject.org/index.html.en](http://www.torproject.org/index.html.en)
              : [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)
please try Vidalia is a gui for TOR, it is in the repos. of jaunty I think.
Remember TOR gives you not a full or real anonymity.
To improve anonymity: [https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#RelayAnonymity](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#RelayAnonymity)

---

### Post by BigB'sLinux on 2009-07-06
^^Thanks for the advice..and of course I expect it to pass the test..which it did..after I killed quicktime and re-edited my etc/privoxy/config file. I had forgotten the &quot; . &quot; as you said. I thought I put it..?   :-) Thanks!  Edit- I agree Tor by itself isnt very good anonymity. I will be running a relay.(not an exit node though) I always do and of course its configed with all the right addons(no script,Ref contol, flashblock,cookie safe,etc)   I am having to reformat after a tweak or a "project" I should say..

---

