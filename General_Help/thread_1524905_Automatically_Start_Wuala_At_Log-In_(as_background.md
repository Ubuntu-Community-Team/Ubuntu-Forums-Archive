---
title: "Automatically Start Wuala At Log-In (as background)"
date: 2010-07-05
forum: General Help
---

### Post by techunit on 2010-07-05
Can I start wuala as a background task in ubuntu? I know you can add it to the start up applications but I don't want to close the window that comes up after it starts... Thanks Guys...

---

### Post by JohnnyZero on 2011-11-20
I know it is out of date but I spend some time with this problem. 
The easiest way in Ubuntu 11.10 is actually to start Wuala  in "Startup Applications" as "wuala -nogui".
It is fairly simple if you look at "cat /usr/bin/wuala" but nowhere documented.

Edit: What is stated above is wrong, it will simply start in a kind of server mode and prevent you from starting the GUI at all until you kill this process.

What works is rather something like this

/usr/bin/java -ea -Xmx384m -Djava.net.preferIPv4Stack=true -jar /usr/lib/wuala/loader3.jar -alternateprogrampath /usr/share/wuala/ -basepath /home/XXX/.wuala -mount /home/XXX/WualaDrive -package -installed -silent

---

