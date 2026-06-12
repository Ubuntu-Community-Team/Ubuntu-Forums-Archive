---
title: "Linux NOOB - How to connect to the internet on ubunto?"
date: 2011-04-09
forum: General Help
---

### Post by mark5008 on 2011-04-09
Hi, i just got linux on my laptop yesterday and i am having troubles with installing my BT Voyager 105 modem card to connect to the internet. I did how ever find this HOWTO sheet : [http://ubuntuforums.org/showthread.php?t=140010](http://ubuntuforums.org/showthread.php?t=140010) . I was fine until i had to type in 'eciadsl-config-tk' where it said 'bash: /usr/bin/eciadsl-config-tk: /usr/bin/wish: bad interpreter: no such file or directory'.... this has left me utterly stumped. Although i have been reading around and i think i may have to install tk8.3 (i have no idea what this is, or how to install it)... 
 
I was also thinking of maybe just buying another modem that might work easier, if this is a better route to take in your opinion?
 
Anyway all advice is appreciated, Thanks for your time :)

---

### Post by spikoley on 2011-04-11
Are you able to connect to the internet in any way?  It looks like you need to install tk8.3 first.  If you go to Applications> Ubuntu Software Center you can install tk8.3.  Once it is install then go back to the tutorial.

---

### Post by spikoley on 2011-04-11
Are you able to connect to the internet in any way?  It looks like you need to install tk8.3 first.  If you go to Applications> Ubuntu Software Center you can install tk8.3, but you need to be online.  Once it is install then go back to the tutorial.

---

### Post by Spyderkid on 2011-04-11
try doing this....

```

sudo mkdir /usr/bin/eciadsl-config-tk
sudo mkdir /usr/bin/wish

```

then try what you did again.
This might not work but it can't harm trying

---

### Post by fela on 2011-04-11
Try doing this:

```
sudo apt-get install apt-file
sudo apt-file update
sudo apt-file search wish
```

A packagename should come up with the file /usr/bin/wish. Install it like this:

```
sudo apt-get install packagename
```

Now try what you were doing before.

HTH

---

