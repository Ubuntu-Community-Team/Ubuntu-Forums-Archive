---
title: "put frequently used programs in ram for faster startup time?"
date: 2010-06-12
forum: General Help
---

### Post by fireandspike on 2010-06-12
Hi

I was wondering if there is any tool or program that stores a copy of frequently used files eg. Binarys, program library's  etc. in memory so when they are requested by the OS they load instantly. I'm asking because I have a system with plenty of ram but very slow hard disks. 

Having programs like opera and java/eclipse load from ram would greatly speed up their start time. Ideally they would be loaded into ram in the background after I log in. Of course all writes made to these files would have to be made to the files on disk for obvious reasons.

I don't want the entire OS in ram because it will not fit, just frequently accessed files.

Is there any such program available?

Thanks

---

### Post by dcstar on 2010-06-12
> **fireandspike said:**
> Hi

I was wondering if there is any tool or program that stores a copy of frequently used files eg. Binarys, program library's  etc. in memory so when they are requested by the OS they load instantly. I'm asking because I have a system with plenty of ram but very slow hard disks. 

Having programs like opera and java/eclipse load from ram would greatly speed up their start time. Ideally they would be loaded into ram in the background after I log in. Of course all writes made to these files would have to be made to the files on disk for obvious reasons.

I don't want the entire OS in ram because it will not fit, just frequently accessed files.

Is there any such program available?

Thanks

```
man ureadahead
```

---

### Post by john newbuntu on 2010-06-12
You could try and use preload:
[http://techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/](http://techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/)

---

### Post by fireandspike on 2010-06-12
thanks, preload is what I was looking for

---

### Post by dino99 on 2010-06-12
linux work like that by itself, depend on available ram

---

