---
title: "Ubuntu Software Center? Downloads?"
date: 2012-03-17
forum: General Help
---

### Post by linktopower on 2012-03-17
Um yeah hello again. me being a dial up user, I was wondering If I start downloading a file and my connection gets cut off. will Software center continue where it was at. or will I have to start all over from the start?

The reason why is I want to download Wine. but the download is like 80+ Mb.
EDIT: And I really don't want to download it like so far and then have to start over.

---

### Post by ajgreeny on 2012-03-17
I am pretty sure that anything already downloaded into /var/cache/apt/archives will remain there even if the connection goes.  I am not totally sure about an individual package that is interrupted halfway through downloading, but I believe the same applies to that.

The total of 80MB will probably be several separate packages, and some will undoubtedly be already downloaded so even if you do loose connection, so you wouldn't have to start from scratch with those.

---

### Post by linktopower on 2012-03-17
> **ajgreeny said:**
> I am pretty sure that anything already downloaded into /var/cache/apt/archives will remain there even if the connection goes.  I am not totally sure about an individual package that is interrupted halfway through downloading, but I believe the same applies to that.

The total of 80MB will probably be several separate packages, and some will undoubtedly be already downloaded so even if you do loose connection, so you wouldn't have to start from scratch with those.
Okay thanks for the information :) 

And I'm not to sure about one single package...But I have an idea though to test it.
I don't know why I didn't do this before. Just download a File and unhook my modem and reconnect and see if would continue where it left off.
I'll be back in awhile with my results :).

EDIT: It works At least I know that I can continue where I left off :)

---

