---
title: "Unable to download torrent file"
date: 2010-03-28
forum: General Help
---

### Post by sm_here on 2010-03-28
I have ubuntu 9.10. I have downloaded Deluge 1.1.9. I have a added a torrent file but download isn't happening. It shows 2 peers are available but it doesn't download. 
I am also getting the following error messages:

[ERROR   ] 12:31:31 config:293 Error backing up old config..
1.1.9
[ERROR   ] 12:31:32 config:293 Error backing up old config..
/usr/lib/pymodules/python2.6/deluge/ui/gtkui/statusbar.py:109: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/usr/lib/pymodules/python2.6/deluge/ui/gtkui/statusbar.py:229: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(item.get_eventbox(), tooltip)
/usr/lib/pymodules/python2.6/deluge/ui/gtkui/statusbar.py:175: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(self.dht_item.get_eventbox(), "DHT Nodes")
/usr/lib/pymodules/python2.6/deluge/ui/tracker_icons.py:70: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  log.debug("%s %s %s" % (url, e, e.message))
[ERROR   ] 12:36:31 config:293 Error backing up old config..

I am new to Deluge. Please help.

---

### Post by sm_here on 2010-03-28
It also gives me a 'No incoming connections' message at the bottom of the window. In the OPtions tab, the Max Download Speed, Max Upload Speed, Max Connections and Max Upload Slots are all  set to -1 KiB/s, -1 KiB/s, -1, -1 respectively. Is this the cause?

---

### Post by wojox on 2010-03-28
Look here [BitTorrent optimization and troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=1259923")

---

