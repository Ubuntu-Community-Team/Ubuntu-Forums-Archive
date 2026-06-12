---
title: "What happens when I install 10.10 over 11.04?"
date: 2011-07-21
forum: General Help
---

### Post by Shvesley on 2011-07-21
I have Ubuntu 11.04 right now, but I want to downgrade to 10.10. If I install 10.10 from a live CD will all of my 11.04 files be gone?

---

### Post by snowpine on 2011-07-21
You should back up all of your files to an external drive. 10.10 will overwrite/replace 11.04.

Going forward, you might consider using a separate /home partition. This will allow you to keep your personal documents/settings when doing a reinstall: [www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)

---

### Post by zero244 on 2011-07-21
It depends......if when you installed Ubuntu 11.04 you created a separate /home partition, then any personal files and folders you added will be untouched.
And some of your program data files and folders like Evolution will also reamain intact.

If you didnt install with a separate /home partition, then everything will be lost.
You might want to copy any files to a external drive or flash drive that you want to keep.
Next time you install Ubuntu I would suggest you create three partitions.

One for your / partition 20 gigs should be fine.
The above partition is your boot partition that grub looks for.

One for your /home partition this can be any size above 10 gigs. I usually make my /home partition 100 plus gigs just so I have plenty of room.

One 2 to 4 gig partition for your swapfile.

By doing it this way you can reinstall linux over itself with out losing everything, like your pictures and music and many program settings etc.

---

