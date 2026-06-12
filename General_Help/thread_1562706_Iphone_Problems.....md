---
title: "Iphone Problems...."
date: 2010-08-28
forum: General Help
---

### Post by warrior_juggalo on 2010-08-28
I can't Delete music with Rythmbox, I delete them from the Iphone with rythmbox, Disconnect, And they just appear again but they don't even play after i've deleted them, How can i 100% remove them from the iphone?

---

### Post by tekkidd on 2010-08-28
This is an issue with the ipod state in Rhythmbox, but dont worry their is a quick fix. Go into:
/home/<username>/.gconf/apps/rhythmbox/state/ipod/

and then delete the file inside the folder (%gconf.xml)

then restart rhythmbox

---

### Post by warrior_juggalo on 2010-08-28
Still does not work?

---

### Post by warrior_juggalo on 2010-08-28
It was my bad, It works perfectly, I was unmounting straight after i deleted them, The sync would say "Sync in progress" for ages I worked out that if you go to, "Music" Than "Quit" It won't exit until the Music is Sync'd or songs are deleted properly, Once it closes you know your good to go!!!

---

### Post by xjesse on 2010-08-28
That was exactly my problem. Just be patient. ;)

Cheers!

---

