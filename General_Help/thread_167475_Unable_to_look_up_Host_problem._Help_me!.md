---
title: "Unable to look up Host problem. Help me!"
date: 2006-04-28
forum: General Help
---

### Post by jscrilla on 2006-04-28
I've not turned my Ubuntu box on for a few months, due to a move and whatnot. Anyhow, I turned it on and it seems some of the fiddling when I last used it has caused some errors. 

I get an error when I try to do sudo gedit hosts

sudo: unable to lookup carver via gethostbyname()

Carver is the name of my box, but I was trying to get my server live off an IP last time I messed around with it. 

I'm sorry...I'm such a newbie and don't remember exactly what I did. If it helps my hosts file has the following information...

127.0.0.1	localhost
70.225.169.90	jscrilla.myftp.org

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Can anyone help me get my system working properly again? Mucho Gracias!

---

### Post by elamericano on 2006-04-28
I think you need to add a line that says:

127.0.0.1     carver

---

### Post by elamericano on 2006-04-28
You may need to go into rescue mode to edit it, if you haven't set up a root password. (That's why I always set up a root account with a secure password.)

---

### Post by jscrilla on 2006-04-28
I'll try that, as soon as I can get my hands on my Ubuntu disk. Thanks for the suggestion.

---

