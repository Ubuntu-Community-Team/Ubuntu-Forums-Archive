---
title: "Apps cant access internat"
date: 2011-09-02
forum: General Help
---

### Post by lesleytitus on 2011-09-02
It first started with Jdownloader no having access to the internet.
It wouldn't check for online status, would even update.

I was googling around and still couldn't find a solution. Then i decided to use Torrents for a while, so i tired the default "Transmission" Torrent client. 

Now, it doesn't connect to any peers and also has a download and update stat as 0. My modem doesn't even flicker. It tried the same with Vuze, still no change.

I assume that there is something wrong with my Network setting, or smtg like that.

PS: I can use firefox perfectly and am able to browse and download files... Also update manager and Ubuntu packer manager work fine. Im running ubuntu 11.04, on a alienware m15x... i7 740QM...

Cheers

---

### Post by 2F4U on 2011-09-03
Do you use a firewall that is blocking certain ports?

---

### Post by sum1nil on 2011-09-03
Good point about the firewall. It can cause headaches.
Try to turn it off in a terminal then see if you can connect:
'sudo ufw disable'. 'Sudo ufw enable' to turn it back on.

---

### Post by lesleytitus on 2011-09-03
Just tried it, no difference, 

sudo ufw status gives "inactive", yet still nothing is downloading

UPDATE: no one knows a solution to this problem... really???

---

