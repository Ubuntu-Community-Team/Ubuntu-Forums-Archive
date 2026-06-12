---
title: "dd cmd caused GNOME power management problem"
date: 2010-03-11
forum: General Help
---

### Post by morenogabr on 2010-03-11
OK, I think I F'ed big time. I was running:
 
dd if=/dev/zero of=/media/(long_device_name) bs=1M
 
with the intention of wiping clean a salvaged hard drive from an old Mac. It was a command I found on a forum and cant say Im familiar with at all. I made the mistake of not adding the visualization option so couldnt see progress for starters. After not too long I noticed that the free space on the Ubuntu partition of my laptop had gone down to zero. No free space! I realize now that may have been part of the command I was running. At the time I freaked and quit terminal. Free space on disk stayed at zero and after restarting it wont let me log in and is giving me a message about GNOME Power Management not being installed or something along these lines. 
 
Im in completely uncharted territory here. Any idea what couldve gone wrong and how I can correct it?

---

### Post by alfplayer on 2010-03-11
It could have happened that the hard drive was not mounted. So you just wrote an enormous and useless file called (long_device_name) on /media directory. If this is what happened, that file should be in /media taking up a lot space, and you should just delete it. Be careful not to delete a directory, you should be deleting a file.

If you can't log in to ubuntu, you can try this from the ubuntu installation disc or any linux live cd.

---

### Post by morenogabr on 2010-03-17
You saved me alfplayer. Thanks a lot. Learning more everyday...

---

