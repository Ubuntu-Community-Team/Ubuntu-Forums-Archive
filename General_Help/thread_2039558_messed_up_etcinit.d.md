---
title: "messed up /etc/init.d"
date: 2012-08-09
forum: General Help
---

### Post by marjenni on 2012-08-09
Hi,
   Just made a really dumb mistake and don't know how to recover.

I created a .sh file with this in it:

java -Xmx512m -jar /home/mark/osm2po/osm2po-core-4.4.55-signed.jar tileSize=5x5 prefix=my /home/united_kingdom.highway.osm

Placed it in /etc/init.d and ran a command to update the list.

Rebooted the server, and I can see the script running, but it kinda locks up the rest of the server. How do I undo the change?

best regards

Mark

---

### Post by marjenni on 2012-08-09
Ok, I could login and remove it, but how do I run the above command on startup without it locking up the server?

many thanks

Mark

---

