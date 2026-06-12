---
title: "Grub error 22, help"
date: 2009-08-02
forum: General Help
---

### Post by Blu Fox on 2009-08-02
So recently I made a separate partition to try out kubuntu, ended up not liking it so I deleted that partition from ubuntu. Things went fine until I restarted. When I booted I got this error. 

Right now this is adding to the frustration I've been having today (dogs got out today, stomach feels terrible, feeling really upset in general) so really this is the last thing I need. 

So any nice, simple, easy enough to understand for a noob help? =D?

---

### Post by merlinus on 2009-08-02
Boot from live cd, open a terminal and enter these commands, one at a time.

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

Remove cd and restart.

---

### Post by Blu Fox on 2009-08-02
Thanks man! You're a life saver

---

### Post by merlinus on 2009-08-02
Glad it worked!  Have fun...

---

