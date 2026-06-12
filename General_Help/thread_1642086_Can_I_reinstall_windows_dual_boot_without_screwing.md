---
title: "Can I reinstall windows dual boot without screwing up my Ubuntu?"
date: 2010-12-09
forum: General Help
---

### Post by sofasurfer on 2010-12-09
I need windows because iscan under Ubuntu does not work well. So I have a dual boot. Trouble is that windows is only good for a month because I can't validate it because I have it on another machine also.

So, my month is up and I can not longer access windows. I could do a complete wipe and reinstall windows and then put Ubuntu next to it but that is a lot of work. Can I just reinstall windows and get my boot loader to operate properly again? Or is it actually easier to do a total wipe out and reinstall? I have tried to restore grub before and I failed miserably.

---

### Post by blueridgedog on 2010-12-09
You can reinstall windows, then reinstall grub using a LiveCD to get your dual booting working again.

See item 13 in this howto:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

(windows will overwrite your boot loader, so you will be able to boot into windows after the install, but not Ubuntu until you re-install grub)

---

### Post by sofasurfer on 2010-12-09
Thanks. I will probably end up trying this but I have no confidence in succeeding, so I will have to get everything backed up first. 
Sure would be easier if I could find that windows activation crack that I used a few years ago.

---

