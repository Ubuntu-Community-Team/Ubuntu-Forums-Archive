---
title: "Mounting hfs+ drives"
date: 2011-01-19
forum: General Help
---

### Post by rmcellig on 2011-01-19
I have several external HFS+ formatted drives that I use on my Mac. Is there a way for me to connect them to my HP laptop running Ubuntu 10.10 and have them read/write capable? I hope there is a tool or some way I can do this.

---

### Post by sum1nil on 2011-01-19
Open synaptic package manager and search for 'hfsplus'. 
I'm not sure about 'automounting' them, but after making a mount point in your home directory like 'mac', you can issue a manual mount using hfs+ as the file system.

Not having external drives, I'm not but assume it's like a usb.

'sudo mount -t hfs+ /dev/sdb1 ./mac'

sda is the main drive sd[letter] would be the additional drives.

Hope this helps.

---

