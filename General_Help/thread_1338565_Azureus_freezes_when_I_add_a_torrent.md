---
title: "Azureus freezes when I add a torrent"
date: 2009-11-26
forum: General Help
---

### Post by arclightfire on 2009-11-26
Hi - for over a year Azureus has been working fine for me, then suddenly now it freezes upon adding a new torrent.

I am using Ubutnu 8.04 and 2.5.0.4.

Thanks

---

### Post by arclightfire on 2009-11-28
OK, I've fixed this by upgrading to Ubuntu 9.10, and Azureus gets upgraded to the new version, Vuse.

1. Upgraded from 8.04 to 8.10 [http://help.ubuntu.com/community/IntrepidUpgrades](http://help.ubuntu.com/community/IntrepidUpgrades)
2. Upgraded from 8.10 to 9.10 [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
3. However then there is a bug that stops Vuse from running so in a terminal I typed:
```
sudo nano /usr/bin/azureus
```
To edit the file 'azureus' so the first 3 lines of this file are:
```
#!/bin/sh
## JAVA='/usr/lib/jvm/java-6-openjdk/jre/bin/java -Xmx1024M'
JAVA='/etc/alternatives/java -Xmx1024M'
```
(ffi: see: [http://ubuntuforums.org/showthread.php?p=7250642](http://ubuntuforums.org/showthread.php?p=7250642))
4. Ctrl & X to exit then answer 'Y' to save the file.
4. Then run Azureus and update it. (It might keep trying to update the core over and over, you can just cancel this process once done.)
5. Then it loads torrents again....

Thanks

---

