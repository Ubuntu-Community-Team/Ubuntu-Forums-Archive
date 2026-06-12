---
title: "RAM disk in Ubuntu?"
date: 2009-11-10
forum: General Help
---

### Post by xjgnsdof on 2009-11-10
Every tutorial I've found for setting up a RAM disk in Ubuntu is either outdated, overly involved (I am NOT recompiling my kernel), or ineffective. Does anyone know how to set on up in Karmic?

---

### Post by jbrown96 on 2009-11-10
[http://en.wikipedia.org/wiki/Tmpfs]("http://en.wikipedia.org/wiki/Tmpfs")
[http://kevin.vanzonneveld.net/techblog/article/create_turbocharged_storage_using_tmpfs/]("http://kevin.vanzonneveld.net/techblog/article/create_turbocharged_storage_using_tmpfs/")
[http://www.howtoforge.com/storing-files-directories-in-memory-with-tmpfs]("http://www.howtoforge.com/storing-files-directories-in-memory-with-tmpfs")

Those are the top three results from google. Please try searching before you post here.

It's extraordinarily easy. Just a single command, and there's been kernel support for years. I have no idea what you're talking about...

---

### Post by xjgnsdof on 2009-11-10
The only reason you found those links is because you know what tmpfs is and are aware of the built in ram disk functionality in the kernel. I was not aware of those things; that is why I asked! Obvious search terms like "ubuntu ram disk" or "linux ram disk" do not turn up any of those links. I will look at those results, but watch the condescending tone, prick. Thank you.

---

### Post by XCan on 2009-11-10
It may not be obvious. But simply speaking, just stick stuff into /dev/shm and they'll end up on the ram. Very handy for transferring data between processes for me. :)

---

### Post by xjgnsdof on 2009-11-15
Putting the cache in /dev/shm seemed to do the trick. Now that I know about it, it's simple to implement.

---

