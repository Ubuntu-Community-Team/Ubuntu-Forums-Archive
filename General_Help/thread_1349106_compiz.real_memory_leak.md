---
title: "compiz.real memory leak"
date: 2009-12-07
forum: General Help
---

### Post by The Funkbomb on 2009-12-07
Not sure when this started but Compiz.real is using up 93.7mb of memory.  It's only using that amount because I restarted it.  Before, it was around 110mb.

This makes my entire system use over a gig of ram.  I don't remember it being this high.

I'm using a nvidia 9600GT.  The only change I've made since I noticed this is I've installed WINE but it's not running right now.

I'm using the Ubuntu 185 recommended drivers but I've been using them since the beginning.

I have no idea what the problem is.

---

### Post by The Funkbomb on 2009-12-08
bump

---

### Post by milhouse07 on 2009-12-22
same issue here.
My memory footprint starts at a reasonable level, and gradually begins to increase... THE MEMORY IS LEAKING!!!

However in the Processes list Compiz.real remains at 14 MB, but i know its Compiz.real because if i switch to Metacity the leak freezes!!! 

however the memory is not released. I have to reboot to get my memory back!

I'm researching, but i have not idea how to fix it! any help will be appreciated!

Edit
Found another symptom... switching to Metacity doesnt free up the memory, however restarting the compiz fusion icon frees up the memory!

---

### Post by icek on 2009-12-23
glxgears helps to get some memory back... what I have heard, this is due some xserver patch that does fix something but causes this leak. I think I did read this at [www.phoronix.com](www.phoronix.com)

---

