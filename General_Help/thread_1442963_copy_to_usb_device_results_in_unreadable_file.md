---
title: "copy to usb device results in unreadable file"
date: 2010-03-30
forum: General Help
---

### Post by schumifer on 2010-03-30
Weiiiirddddddddddd  things i tell you!!!
OK, i own the htc touch pro 2.
I connect it to my pc running kubuntu 9.10 32bit
I choose that it be used as a usb device, since, well, i cannot use it to sync with kubuntu (and don't need to, anyhow!)
So, while it is charging i need to transfer a file over.
I copy it either via the cp command or dolphin.
I try to read it through the device-> no go!
I copy it back to the pc(different folder) and kubuntu won't even read it. I check it versus original file with kdiff3 and it does seem a hell of a lot different!!!!!!!!!
So OK maybe it is the storage card. NOOOOOOOOOOOOOOOOOOO.
Through windows files transfered are properly read.
Want another clue? If i transfer the files though kbluetooth it works perfectly OK and of course kdiff3 says they are binary equal!
I attach the pdf i used as an example, please compare them and tell me what i am doing wrong.
Also, here are the mounting options (same for usb flash disks which work perfectly OK)
```

/dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)

```
UPDATEEEEEEEEEEEE
Just run some tests. Check this out
I connect the phone, mount it cp the file and immediately run it through dolphin but from the storage card. WORKS FINE. Kdiff3 says binary equal.
Umount properly, then try to read the file from phone ->NO GO
Reconnect, mount, open storage card through dolphin, open the file->NO GO.
Try to open the file through the phone->NO GO.
kdiff3 finds differences!
Is my phone possessed?

---

