---
title: "Several errors in Karmic"
date: 2009-10-30
forum: General Help
---

### Post by DeMus on 2009-10-30
At the moment I have the following errors:

[LIST=1]
[*]When listening to music while playing a game I don't hear the game sound. I only hear the music Banshee is playing. I had the same in Hardy while in Jaunty this was solved. Now it is back again. What can I do about this?
[*]I have 2 cd-rom players. Only my first one shows up in nautilus, the other one just does not exist. What to do?
[*]I can't install Google Earth. I get the following message in terminal:
[/LIST]
```
jan@2-Quad:~/Downloads$ ./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3509.4636...............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
```

I am sorry to say this but new is not always better.

---

### Post by Soul-Sing on 2009-10-30
long time ago thread: [http://ubuntuforums.org/showthread.php?t=551205](http://ubuntuforums.org/showthread.php?t=551205)
same error, did you "find" the right way to install googleearth on a 64 bit system? i do run the progr. from a 64 bit hardy via medibuntu...
or search for: lib32nss-mdns in synaptic package manager.

---

### Post by DeMus on 2009-10-30
> **leoquant said:**
> long time ago thread: [http://ubuntuforums.org/showthread.php?t=551205](http://ubuntuforums.org/showthread.php?t=551205)
same error, did you "find" the right way to install googleearth on a 64 bit system? i do run the progr. from a 64 bit hardy via medibuntu...
or search for: lib32nss-mdns in synaptic package manager.

No luck. I did install the lib32nss-mdns package but also with that it did not work.
I had it working on Jaunty, which was also 64-bits. So what changed in Karmic?

---

