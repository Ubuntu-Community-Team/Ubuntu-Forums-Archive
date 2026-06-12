---
title: "WD My Book Live - green light"
date: 2012-08-15
forum: General Help
---

### Post by Shadius on 2012-08-15
Hey everybody! :)

I notice that my WD My Book Live sometimes has a constant green light lit on it. This green light means that there's some activity on the drive, but I'm not accessing it. So I'd like to know what's going on with it. How can I find out?

---

### Post by Shadius on 2012-08-16
Anyone?

---

### Post by lisati on 2012-08-16
Don't panic! We haven't forgotten you.

I noticed your question not long after you first posted it, but the best answer I could think of at the time related to Windows indexing the drive. :(

---

### Post by Shadius on 2012-08-16
> **lisati said:**
> Don't panic! We haven't forgotten you.

I noticed your question not long after you first posted it, but the best answer I could think of at the time related to Windows indexing the drive. :(

Thank you lisati! :) I thought it might have to do with indexing. Indexing is for it to be able to find the files faster, right? I'm a little foggy on what exactly indexing means.

---

### Post by lisati on 2012-08-16
> **Shadius said:**
> Thank you lisati! :) I thought it might have to do with indexing. Indexing is for it to be able to find the files faster, right? I'm a little foggy on what exactly indexing means.

The sort of thing I had in mind, not directly relevant to Ubuntu, is described here: [http://en.wikipedia.org/wiki/Indexing_Service](http://en.wikipedia.org/wiki/Indexing_Service)

---

### Post by Shadius on 2012-08-16
> **lisati said:**
> The sort of thing I had in mind, not directly relevant to Ubuntu, is described here: [http://en.wikipedia.org/wiki/Indexing_Service](http://en.wikipedia.org/wiki/Indexing_Service)

Thank you for that link. As of right now, I'm using Ubuntu and there's no green light on the WD My Book Live. I'll have to check to see if the green light comes on when I use my Windows laptop to know for sure. At least, now I know where to begin looking. Much appreciated! :)

---

### Post by wallaroo on 2012-08-16
Actually a solid green light means it is awake and ready to be used, flashing green means it is busy doing something.
If it's in standby the light will be blue, but local network broadcasts can wake it up and change the blue to green.
I've noticed however that this light is a bit erratic, it's inconsistent and often there is no light at all, even during heavy activity.

If you want to explore the device a bit more, it's just another Linux box so you can SSH to it as root and run the usual Linux utilities to check what's running and what's connected (e.g. 'top' to see what's running, 'net status shares' to see what is currently connected, and so on.).

---

### Post by Shadius on 2012-08-16
> **wallaroo said:**
> Actually a solid green light means it is awake and ready to be used, flashing green means it is busy doing something.
If it's in standby the light will be blue, but local network broadcasts can wake it up and change the blue to green.
I've noticed however that this light is a bit erratic, it's inconsistent and often there is no light at all, even during heavy activity.

If you want to explore the device a bit more, it's just another Linux box so you can SSH to it as root and run the usual Linux utilities to check what's running and what's connected (e.g. 'top' to see what's running, 'net status shares' to see what is currently connected, and so on.).

Oh okay. Makes sense. I've never done SSH, so is there a guide I can look at to learn more?

---

### Post by Shadius on 2012-08-17
> **lisati said:**
> The sort of thing I had in mind, not directly relevant to Ubuntu, is described here: [http://en.wikipedia.org/wiki/Indexing_Service](http://en.wikipedia.org/wiki/Indexing_Service)

So I believe you are right. I was on my Windows laptop today and I looked to see if the green light came on, and there it was. Thank you for the help.

---

