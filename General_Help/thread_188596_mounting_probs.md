---
title: "mounting probs"
date: 2006-06-04
forum: General Help
---

### Post by slimdog360 on 2006-06-04
Okay, I wrote a poat earlier saying that I couldnt see my fat32 partion, well now I can only I cant mount it.
a little window comes up saying unable to mount volume then in the details section i get this
error: device /dev/hda3 is not removable

error: could not execute pmount


whats going on? this is so frustrating

---

### Post by badrad on 2006-06-04
This guide helped me get my windows partitions working great, maybe it will help you:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Other than that I dont know, I've only been using Ubuntu for two days :)

---

### Post by taurus on 2006-06-04
What's the output of this command from a terminal then?  What command did you try to run to mount it?
```

sudo fdisk -l /dev/hda

```

---

