---
title: "No wireless -- help!!"
date: 2010-04-01
forum: General Help
---

### Post by benekastah on 2010-04-01
I recently switched from Ubuntu to Ubuntu Studio 9.10. Installation was full of problems with drive mounts and internet and whatnot. I reinstalled a few times, and I've come to the conclusion that that isn't going to help anything.

Mounting works now, and I managed to get ethernet connections working (surprising that this didn't work out of the box). Now the main issue I'm dealing with is wireless.

Here are my specs:
Wireless hardware: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
Wireless driver: was using ath5k, switched to madwifi with no results
Network manager: I'm currently using the gnome network manager, wicd didn't work either
Computer: HP Pavillion dv7

The problem is my wireless set up is always listed as disconnected. I can't find an option anywhere to connect it. If I disable wireless and re-enable it, nothing happens. Naturally it can't see any wireless networks, and even if I manually input the connection information for a particular network it can't connect, but keeps asking for the password over and over. Other computers in the house connect just fine.

Any ideas? I have no idea what to do, having only a very limited knowledge of any solutions (command line or otherwise) for network problems. I've tried everything I know -- help!!

---

### Post by gordintoronto on 2010-04-01
The driver for your wireless is built-in in Linux.

After installation, you should have right-clicked on Network Manager, select "edit connections." A window opens, select the wireless tab. Click Add. Enter the SSID, connection type and passphrase in the appropriate locations.

The other things you have done might mean it's not that simple.

This is in the Community Docs, but it's not easy to find.

---

### Post by leftoflexo on 2010-04-02
from the sound of your installation being buggy and things acting strange i would say that you need to check your md5sum to make sure the disk image you burned isnt corrupted. if that turns out to be fine burn yourself a new copy of the disk using the slowest setting your burner software allows.

---

### Post by Elfy on 2010-04-02
moved to general help and bumped

---

