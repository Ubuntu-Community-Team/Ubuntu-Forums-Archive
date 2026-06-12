---
title: "Removable storage device difficulty"
date: 2010-04-16
forum: General Help
---

### Post by Ron W on 2010-04-16
What can I do if a removable storage device is clearly active when plugged into a USB port, but there is no corresponding icon showing on the desktop?

Thanks for any suggestions

Ron

---

### Post by mikewhatever on 2010-04-16
By clearly active you mean... a led is on? Does the drive show in the left panel on the file browser?

---

### Post by Ron W on 2010-04-16
Thanks for the reply.

Yes, the screen on the camera comes on, but there is no drive shown in the left panel on the file browser.

Ron

---

### Post by cdenley on 2010-04-16
```

sudo fdisk -l

```

---

### Post by mikewhatever on 2010-04-16
Try pluging it in, and then in a terminal,
```
dmesg | tail
```

...and post the output.

---

### Post by Ron W on 2010-04-16
What do I do with:

sudo fdisk -l

Thanks

---

### Post by cdenley on 2010-04-16
> **Ron W said:**
> What do I do with:

sudo fdisk -l

Thanks

-Applications>Accessories>Terminal
-type in "sudo fdisk -l"
-press enter
-enter your password if prompted (you will not see your password on the screen, but it is being entered)
-copy the resulting output
-paste the output here inside "CODE" tags
[NOPARSE]
```

output goes here

```
[/NOPARSE]

---

