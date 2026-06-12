---
title: "Chmod question/issue?"
date: 2009-11-01
forum: General Help
---

### Post by rp3 on 2009-11-01
Ok I have a LinkStation that I typically mount r/w for my pics, movies, music, etc...

So I created the dir's in /mnt then mount them via fstab... well I try to write to one and I realize i don't have write access, so I figure I will just chmod 777 it and all will be well.  Well I do that and nothing happens.

Another note, I have ln -s the dirs to my main dir if that matters?

So it looks like this
```
drwxr-xr-x  6 root root    0 2009-10-18 09:15 linkmus
drwxrwxrwx 16 root root    0 2009-10-25 10:49 linkpics
drwxr-xr-x 11 root root    0 2009-10-31 14:50 linktv
```

when I do a 'sudo chmod 777 linkmus' for example nothing happens, but as you can see somehow linkpics is correct???

Thoughts?

Ok a reboot and some changes to fstab have solved the issue...

---

