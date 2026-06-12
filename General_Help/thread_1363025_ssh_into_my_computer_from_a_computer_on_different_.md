---
title: "ssh into my computer from a computer on different network?"
date: 2009-12-23
forum: General Help
---

### Post by gfunkera on 2009-12-23
is it possible to ssh into my computer from a computer 50 miles away? (the distance is arbitrary, i mean from a different network) i can currently ssh into my computer from the same network cause i know the internal IP..

any ideas?
:popcorn::popcorn::popcorn:

---

### Post by taurus on 2009-12-23
You can connect to your machine even from Mars as long as you open a port on the router and redirect it to the right machine at home.

---

### Post by spiderbatdad on 2009-12-23
this is easily accomplished if you have your own external ip address (not nat) and if you have a router to forward ssh requests to the host machine.

---

### Post by gfunkera on 2009-12-23
oh okay i understand, but what settings in the router should i be aware of when im doing this? also what would the command look like?

---

### Post by spiderbatdad on 2009-12-23
forward port 22 to lan ip of machine. If running ufw open 22```
sudo ufw allow 22
```

```
ssh -X username@xxx.xxx.xxx
```If you do this you will want to install a program like fail2ban to block persistent unwanted attacks. You can also use the graphical connect to server program choosing sftp as your connection type.

---

