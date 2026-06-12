---
title: "Can the clipboard keep contents after app closes?"
date: 2006-02-06
forum: General Help
---

### Post by oldmanstan on 2006-02-06
Can the clipboard in gnome keep what you've copied after you exit from the program you copied it in? Having switched from windows about 6 months ago after several aborted attempts over the years that is still the one thing that makes me want to throw my monitor through the window, when I close a window only to find that whatever i copied from that window is now gone.

Is this possible? Maybe a special daemon i can install? Something?

---

### Post by Leif on 2006-02-06
ok, first off a **disclaimer** : this method is old ! I'm copy/pasting from an old install log, so it may be out of date. I'm pretty sure searching the forums for "gnome clipboard demon" will get you what you're looking for.

anyway, here's my old method :

```
wget -c http://frankandjacq.com/ubuntuguide/gnome-clipboard-daemon-1.0.bin.tar.bz2
sudo tar jxvf gnome-clipboard-daemon-1.0.bin.tar.bz2 -C /usr/bin/
sudo chown root:root /usr/bin/gnome-clipboard-daemon
sudo chmod 755 /usr/bin/gnome-clipboard-daemon
sudo gnome-clipboard-daemon &
add to sessions, order 80
```

---

### Post by quonsar on 2006-02-06
read this thread:

[http://www.ubuntuforums.org/showthread.php?t=126348]("http://www.ubuntuforums.org/showthread.php?t=126348")

i downloaded and installed gnome-clipboard-daemon. then i added it to my startup programs in session manager. works great!

---

