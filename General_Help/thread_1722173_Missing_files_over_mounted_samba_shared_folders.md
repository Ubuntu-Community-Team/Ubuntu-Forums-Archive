---
title: "Missing files over mounted samba shared folders"
date: 2011-04-05
forum: General Help
---

### Post by MatanUbe on 2011-04-05
I'm having the same problem on Ubuntu 10.10: [http://ubuntuforums.org/showthread.php?t=1281411](http://ubuntuforums.org/showthread.php?t=1281411)

Some files are missing over samba mounted shares. These files seem to be random, but are always the same ones that are missing.

Has anyone found a solution?

Background info:
Mounted from Windows 7 Ultimate x64 to Ubuntu x86
Wired network.
4 folders shared with guest privileges. Movies, Music, Photos, Work.
Lamp running.
Primarily used for Boxee and remote access.

---

### Post by MatanUbe on 2011-04-06
Found a solution! [http://ubuntuforums.org/showthread.php?t=1312553](http://ubuntuforums.org/showthread.php?t=1312553)

Instead of doing a "smbfs" mount do a "cifs" mount and add "noserverino" as one of the options.

Change:
//my-pc/share /home/share smbfs guest 0 0

To:
//my-pc/share /home/share cifs guest,noserverino 0 0

Another thing, "sudo mount -a" didn't show the results, I rather made sure and did a "sudo reboot" and it worked.

I hope this helps someone, I've been struggling for days! Really hard to google this...

---

### Post by MatanUbe on 2011-04-07
After closer inspection, I still have the problem. :( Although is seems a bit better.

Anyone have a different solution? Maybe I should just upgrade to Ubuntu 11.

---

