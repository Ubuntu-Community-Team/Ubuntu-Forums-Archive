---
title: "Running Application from two separate drives?"
date: 2010-10-12
forum: General Help
---

### Post by conb123 on 2010-10-12
Ok kind of a strange question, but here goes. I recently bought an ssd. However due to ssd prices being extremely high I was only able to get a 60gb drive. This means my ubuntu partition is only about 8GB since my windows partition has to hold a load of games. I am going to run out of space eventually on this ubuntu partitionn so is there anyway I can make apps install on my main hdd once it fills up?

Thanks, conb123

---

### Post by James78 on 2010-10-12
> **conb123 said:**
> Ok kind of a strange question, but here goes. I recently bought an ssd. However due to ssd prices being extremely high I was only able to get a 60gb drive. This means my ubuntu partition is only about 8GB since my windows partition has to hold a load of games. I am going to run out of space eventually on this ubuntu partitionn so is there anyway I can make apps install on my main hdd once it fills up?

Thanks, conb123
Actually, you can. Instead of making the apps install "somewhere else", you could just install your Ubuntu system in a special way, where the main areas, like /usr are mounted from another hard drive (see fstab configuration for automounting, however depending on how you install the system, it might configure automounting for you already). It's an easy solution to a more complex problem. :P

Gotta love Linux huh?

---

### Post by conb123 on 2010-10-12
Right well I've currently got it set up with an 8gb ext4 partition and a 3.7gb swap partition on my ssd. I set the ext4 on the ssd to / and then I created an ext4 partition on my main hdd to hold /home. But I figure with it set up like this everything will install to the ssd which will mean it will fill up eventually. I mean, I want some applications on my ssd, the increased speed in my favourite applications would be nice. But when it fills up I'd need ubuntu to install to the hdd instead? Could I do this?

---

