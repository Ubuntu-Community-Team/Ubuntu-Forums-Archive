---
title: "How to stop raid resync/chek"
date: 2012-05-22
forum: General Help
---

### Post by quickk on 2012-05-22
I just managed to get my raid array set up, after waiting 20+ hours for it to assemble.  

Now I accidentally clicked the "check" option in the stupid palimsest/gnome-disk-utility which launched a complete resync of my array.   How do I stop this?  I don't want to wait another 20+ hours!

There should be some warning that this will take an inordinate amnount of time.

---

### Post by quickk on 2012-05-22
Found the solution [here]("http://chris.farhood.org/2010/04/04/how-to-stop-an-mdadm-resync/")

So I did:

```
 sudo /usr/share/mdadm/checkarray -xa 
```

and it worked!  

(all the other things that I tried, like echo "idle" > /sys/block/md1/md/sync_action didn't).

---

