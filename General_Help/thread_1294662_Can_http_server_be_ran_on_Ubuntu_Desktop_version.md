---
title: "Can http server be ran on Ubuntu Desktop version?"
date: 2009-10-18
forum: General Help
---

### Post by NobuStarwind on 2009-10-18
can an http server such as apache run on Ubuntu 9.04 Desktop version or does one need to switch to the server edition? I really don't want to switch to the server version because what I read the server edition has to wipe out my entire system to run. And I still need Windows for certain apps.

---

### Post by bboston7 on 2009-10-18
It works on the desktop version.

---

### Post by wmcbrine on 2009-10-18
Ubuntu has no artificial restrictions on what you can do with what version. The differences between Server and Desktop are for user convenience, not marketing purposes. :)

---

### Post by Mal Bridgeman on 2009-10-18
[COLOR=DarkRed]This is a reasonably good guide .... well it got me going and I'm a total noob....
[/COLOR]
[http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server](http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server)
[COLOR=DarkRed]
HTH
Mal[/COLOR]

---

### Post by jward3010 on 2009-10-18
The reason theres a server edition and a desktop edition is down to performance, complexity and level of failure or fallover. Server edition has no desktop software whatsoever, doesn't load anything but an immensely powerful command line and hence gives better performance and has less complications which in turn equal less crashing, freezing etc but be prepared to use the console exclusively (not that hard). Desktop edition comes chock full of desktops, graphical programs, configuration for them and they'll use up memory when they run, memory much more suited to apache when it's running. Although you might want the best of both worlds which is possible.

Keep this in mind, if you're hosting an intensive website getting a lot of hits use server edition, if just testing stuff or you get small hits a day stick with Desktop.

---

### Post by NobuStarwind on 2009-10-18
Thanks for the replies folks. It's not for a huge server bandwith. Likely only be 5 or 10 users at the most per day. I'm only on High Speed connection through the cable company.

---

### Post by jward3010 on 2009-10-19
Then I'd say have the best of both worlds and stick with Desktop.

---

