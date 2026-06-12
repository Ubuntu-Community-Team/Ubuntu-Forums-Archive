---
title: "NEED HELP PLEASE sudden loss of network"
date: 2006-03-20
forum: General Help
---

### Post by chronusdark on 2006-03-20
my ubuntu breezy (that has been working without a hitch for 4 months now) has suddenly stopped being able to connect to my router also if i try to reinstall or use the live CD i still cant connect However if i use a gentoo live cd it works fine any ideas?

PLEASE HELP ME

thanks

---

### Post by bluevoodoo1 on 2006-03-20
I had a problem somewhat similiar to what's going on here... Here's the the thread I wrote, maybe something there can [hopefully] help.

[http://ubuntuforums.org/showthread.php?t=135151](http://ubuntuforums.org/showthread.php?t=135151)

---

### Post by chronusdark on 2006-03-20
ok tried that and it didnt work

i have noticed that for some reason my eth0 is trying to use ipv6

but i disabled ipv6 and it still doesnt work

someone please help me i really dont want to have to switch distros

---

### Post by chronusdark on 2006-03-20
i fixed it you wont blieve how i did it tho...i booted into the gentoo live cd and did  

sudo rmmod sk98lin (my driver) and i rebooted and it worked weird huh

---

