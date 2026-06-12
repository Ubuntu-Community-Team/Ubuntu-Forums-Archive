---
title: "error while hash checking of torrent"
date: 2010-06-08
forum: General Help
---

### Post by nitstorm on 2010-06-08
```

nits@nits-desktop:/mnt/Storage/Tors/Incomp$ btdownloadcurses --check_hashes 1 filename.torrent 
/usr/lib/python2.6/dist-packages/BitTorrent/Storage.py:4: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  from sha import sha
These errors occurred during execution:
[09:37:48] IOError - [Errno 5] Input/output error

```

Got this error when I tried hash checking, was downloading the file using rtorrent when there was a sudden powercut and my system shutdown abruptly, tried restarting the torrent and kept encountering problems while restarting.
Please help.
Thanks in advance.
Cheers

---

### Post by nitstorm on 2010-06-08
Looks like the file got corrupted. Tried forcing a chkdsk from the MS side on that NTFS partition by *ntfsfix /dev/sda3* but to no avail. Going to let it go :( let me know if there is a fix for this....

---

### Post by nitstorm on 2010-06-19
Seems the file got super corrupted coz of a power cut, So I had to delete the file and restart the torrent.

---

