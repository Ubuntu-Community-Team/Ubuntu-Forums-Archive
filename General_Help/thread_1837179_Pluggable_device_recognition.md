---
title: "Pluggable device recognition"
date: 2011-09-01
forum: General Help
---

### Post by steviefordi on 2011-09-01
When I plug in my media player (or any storage device), I get a folder appear on the desktop named something like "3.8Gb Storage Device".

How do I set up my system so it's named something more descriptive like "Steve's media player"? (I guess it's a udev thing or a Gnome thing but I'm not sure which!)

---

### Post by steviefordi on 2011-09-02
Found a solution here:
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

For me, I ignored the bits about mounting the drive in a specific place as I only needed to label the drive.

I labelled the drive using mlabel (option 2 in the guide on labelling FAT partitions) and now the icon on my desktop is named the same as the label.

I did have to disable a check in the configuration file, but the message from mlabel told me what to do.

---

