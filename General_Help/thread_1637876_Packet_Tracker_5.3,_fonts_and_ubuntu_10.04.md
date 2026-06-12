---
title: "Packet Tracker 5.3, fonts and ubuntu 10.04"
date: 2010-12-05
forum: General Help
---

### Post by Besogon on 2010-12-05
If you install PacketTracker you see that fonts are awful. They are too big and enormous. I've been seeking for a decision of that and stack at a site ([Russian blog]("http://klets.name/archives/126")).
And here is decision:
1) ```
sudo aptitude install libqtwebkit2.2-cil libqt4-script libqt4-qt3support libqt4-sql
```

2) Open file ```
sudo nano /usr/local/PacketTracer5/packettracer
``` and comment the string ```
export LD_LIBRARY_PATH=$PTDIR/lib
```
This is all you need.

The only thing that I've noticed giving a trouble is the list of Filters in Simulation mode. (With black background there is black font) So you have to change your ubuntu theme to lighter one.

---

### Post by johnbrown678 on 2010-12-05
i am also having the same problem, i wish some one could help!

---

### Post by Besogon on 2010-12-05
Please, tell me how to rid of [SOLVED] mark?

This way are cause of other problem!!

---

