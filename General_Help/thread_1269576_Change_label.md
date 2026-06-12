---
title: "Change label"
date: 2009-09-18
forum: General Help
---

### Post by mr.suchy on 2009-09-18
Hi,

I want change label on my sda8, when I type
```
sudo blkid
```

I see:
```
/dev/sda1: UUID="EE3CBB2A3CBAED29" LABEL="Windows" TYPE="ntfs" 
/dev/sda5: UUID="7DF696DE2E9CCE35" LABEL="Dane" TYPE="ntfs" 
/dev/sda6: UUID="9dd15a26-64da-4f4c-bab4-cba165793e63" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="70487248-b556-4773-aecc-286b45f86a47" 
/dev/sda8: UUID="0c166cc7-47ac-439e-b52e-e5f718c9391e" SEC_TYPE="ext2" TYPE="ext3" LABEL="Dane" 
```

why I have this in sda8 ```
SEC_TYPE="ext2" TYPE="ext3"
``` ?? and why I can't see label "dane". When I open my computer I have all of my partition but I can't see "Dane" only label "No&#347;nik 19GB". Why sda8 can't display right label ?

Regards!

---

### Post by stderr on 2009-09-18
SEC_TYPE stands for secondary type, and I believe it's intended to be used as a fallback position if the drive can't be mounted as having TYPE filesystem. I don't know why it's sometimes listed for ext3 partitions, but I wouldn't lose sleep over it :)

You can also view disk labels with **sudo e2label /dev/sda1** and change them with **sudo e2label /dev/sda1 myNewLabel**. Have you rebooted since you made the change? If that doesn't work, try changing the label for either sda8 or sda5 so each label is unique.

---

### Post by mr.suchy on 2009-09-18
I restarted and it's works!. Thanks

---

### Post by Jerubaal on 2009-10-17
Fantastic - now I don't have 3 drives all called 'Gutsy', when none of them actually have Gusty on any more!

---

