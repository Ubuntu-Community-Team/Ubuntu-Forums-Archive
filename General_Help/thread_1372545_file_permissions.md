---
title: "file permissions"
date: 2010-01-04
forum: General Help
---

### Post by boondocks on 2010-01-04
I need to setup permissions for some files.
[LIST=1]
[*]The users on this Ubuntu system should be able to read/view the files.
[*]They cannot write/edit the files.
[*]Most importantly, **they should NOT be able to copy the files anywhere**.  They should NOT be able to copy these files to another folder, USB device, etc.
[/LIST]
How can I do this?

---

### Post by doas777 on 2010-01-04
you can't really. copying is just reading, to a buffer. the filesystem can't really differentiate between a read to copy, and a read to just ... well ... read.

most places try to deal with this, by disabling removable media, and attempting to lockdown web access so that the file cannot be sent outside.

writing files, and deleting them is the same way. if you can write, you can delete (just write over the file with a length of 0), so you can't have one without the other.

---

