---
title: "Firestarter still running?"
date: 2006-03-05
forum: General Help
---

### Post by EBAR on 2006-03-05
Hey I wanted to thank everyone here first of all. I've set up and am currently running Ubuntu Breezy with no problems because of all the solutions I've found on this site.

I recently installed Firestarter through Synaptic. It works great i was just wondering if it's still running and protecting my computer even after I close the Firestarter GUI.

Thanks in advance for your help!

---

### Post by Randomskk on 2006-03-05
Yup, it indeed should be, so long as you clicked the apply / install in Firestarter.

Firestarter just makes rules, there's another program called iptables that is always running that actually enforces them.

---

### Post by EBAR on 2006-03-05
That's fantastic to hear. Thank you very much for your speedy response! :)

---

### Post by njzillest on 2006-03-05
you can type in "iptables" into the consol to see what its running, and you can also open up and close ports through the firestarter GUI

---

### Post by kaamos on 2006-03-05
If you are still feeling uneasy you can check this by typing in a terminal
```
sudo /etc/init.d/firestarter status
```

---

### Post by EBAR on 2006-03-05
Thank all of you for the help. I'll take a look in the terminal and see what it's doing.


EBAR

---

