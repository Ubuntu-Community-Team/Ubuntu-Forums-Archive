---
title: "How to call a program in X trought ssh?"
date: 2009-06-29
forum: General Help
---

### Post by Shex Nivis on 2009-06-29
Hello,
I got a computer running vuze(graphical bit torrent client) and SSH. The problem is Vuze takes almost all the bandwidth witch makes the ssh works slow. So what I wanna do is kill vuze and after I'm done everything I have to do with ssh I wanna call vuze again. The command to start it is 'vuze'. Alreald tried adding -X when calling ssh, nohup vuze, vuze.
Thanks for the help,
Shex~

---

### Post by Shex Nivis on 2009-06-29
Solved.
killall -STOP java
killall -CONT java
that did the trick : )

---

