---
title: "Swap space shows 0k total"
date: 2010-11-24
forum: General Help
---

### Post by emonti on 2010-11-24
Hi,

1GB RAM, 80GB HDD, Travelmate800 laptop, Lucid.

Would appreciate a little advice on the issue of swap space on my travelmate800 using Lucid.

I wondered why my machine's fan/disk was always going hell-for-leather and checked how much swap space was being used. It(top) showed it was all being used up. Occassionally my machine would simply slow right down and in one or two cases it never came back.

 Anyway, the problem is this. I noticed I had two swap partitions which I was not expecting to see. In an attempt fix the problem, I removed the smaller swap partition (1GB) and now there is only the 4GB partition. But now when I do 'top' it shows as Swap 0k total. So it appears as though the 4GB swap is not being recognised - is this a bad thing?

This is quite an old laptop (2003) but it has 1GB RAM and should be adequate to use as a java development workstation. But it seems the idea of swap - the way I understood it - was that when you run out of RAM you have a fallback situation where you can continue to run your applications but at an increased cost in CPU cycles due to all the swapping.

The only reason I ask, of course, is that short of upgrading my RAM which will be more expensive to do because I will have to ditch existing modules to free up slots, I want to improve my laptop's performance. Running Eclipse tends to take up a lot of space.

Should I do something to link the remaining swap space?

---

### Post by mikewhatever on 2010-11-24
To make use of the remaining swap partition, you'd have to edit your /etc/fstab file and modify the UUID of the swap partition there to the UUID of the correct partition. To find out what the correct UUID is run **sudo blkid** ...

Also check what's using a lot of ram when you see the swap partition beginning to fill up.

---

### Post by emonti on 2010-11-24
Thanks Mikewhatever.

That did the trick. Will keep an eye on memory usage. Seems always to involve a browser (firefox or chromium)

Is that what swap is designed for? i.e. kicking in when your RAM is full?

---

### Post by mikewhatever on 2010-11-24
Yes. Swap is an extension to ram, used when ram starts filling up.

---

### Post by oldos2er on 2010-11-24
You can tune "swappiness": [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

