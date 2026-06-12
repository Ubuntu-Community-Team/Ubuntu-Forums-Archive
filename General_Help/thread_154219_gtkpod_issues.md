---
title: "gtkpod issues"
date: 2006-04-02
forum: General Help
---

### Post by Piggah on 2006-04-02
Hi,

I've been trying for a quite a while to get gtkpod working with my iPod, which is a shuffle btw. I'm having the same problem everytime I try to write any changes to the iPod. When I click sync, I get this error: 

```
Path not found: '/media/ipod/iPod_Control/Music/F11'.

Path not found: '/media/ipod/iPod_Control/Music/F12'.
```

Strange thing about the error is that the 'F' file changes everytime I try to sync. 

I've read through some documentation on gtkpod, but nothing has turned up.

Any ideas?

Thanks in advance

---

### Post by wile_e8 on 2006-04-02
I'm getting the same sort of error on my nano, except that the 'F' folder always starts at F09.  FWIW the Ipod_Control/Music/ folders are F00 through F02.

---

### Post by wile_e8 on 2006-04-03
OK, after playing around a bit, I fixed it.  In gtkpod, go to File->Create Ipod Directories, and that will create the directories it says are missing.  I think that should fix it.

---

### Post by Edward The Bonobo on 2006-04-03
See also: [http://ubuntuforums.org/showthread.php?t=151566&highlight=ipod](http://ubuntuforums.org/showthread.php?t=151566&highlight=ipod)

---

