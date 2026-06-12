---
title: "Nautilus Network Browsing Troubles"
date: 2011-10-01
forum: General Help
---

### Post by max1e6 on 2011-10-01
Using 10.04 New install.

There are hundreds of posts on this... none both relevant and working for me.

I can navigate to share: smb://192.168.57.25/ and open the files. But I can't browse/navigate the windows network from Nautilus. "Network" appears in the "Places" column (with a folder icon!). Clicking it shows "Windows Network" in the list (also with the folder icon). Clicking the "Windows Network" item throws the error: "Unable to mount location Failed to retrieve share list from server"

The computers running Windows on my LAN are setup correctly. Another computer on my network, also with 10.04, can navigate and browse them. There's nothing wrong with the hardware; a duel boot 10.04 is OK. The smb.conf appears to be OK. It is the same as that of the working installs. Even a VBox 10.04 guest (with a bridged network adapter) can browse the windows network through Nautilus.

Oddly, all of the other (working) installs show a "Twin monitor" icon for both the "Network" place and the "Windows Network" item.

I'm stuck.

---

### Post by dino99 on 2011-10-01
of course your best friends are logs, glance at usefull errors/warnings (thinking to samba , shared partitions, groups & users)

sudo dpkg-reconfigure -phigh -a

mountall might do the job
maybe look at /etc/fstab & mtab

---

### Post by max1e6 on 2011-10-01
For the logs, I don't see anything very exciting. But then, I'm probably too stupid to know where to look.

Doing dpkg-reconfigure didn't change anything. 

The VBox machine's Nautilus browses the network. Do you suppose there is a config I can copy from it (other than smb.config)?

Anyway, to eliminate the possibility it was related to the user account,   I logged in as root and tried it - no luck. I also tried with WICD after removing Networkmanager.

---

### Post by max1e6 on 2011-10-01
Humm?

Installed netdiscover. Probably has nothing to do with the fix but everything works now.

---

