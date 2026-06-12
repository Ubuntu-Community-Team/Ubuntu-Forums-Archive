---
title: "Using swap partition on RAID volume"
date: 2011-04-04
forum: General Help
---

### Post by substanceD on 2011-04-04
Hello, it has been bothering me for a while that I am unable to hibernate my computer while using Ubuntu and I figured out the reason--Ubuntu is not using my swap partition. I would follow the existing tutorials on setting up a swap partition after installing Ubuntu, but since the volume uses hardware RAID 0, the swap partition is not assigned a /dev/ entry (like /dev/sdxx) and I am not sure how I can mount it. Any advice? Here is what I have:

```
sudo blkid -c /dev/null
/dev/sda1: LABEL="System Reserved" UUID="067E90EB7E90D531" TYPE="ntfs" 
/dev/sda2: UUID="327A972F7A96EEBB" TYPE="ntfs" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/mapper/isw_dcbichgdbd_Secondary1: LABEL="Secondary" UUID="6E5EFA515EFA1197" TYPE="ntfs" 
/dev/mapper/isw_dcbichgdbd_Secondary3: UUID="d9392528-0f84-4070-9fda-6884e24ef4db" TYPE="ext4" 
/dev/mapper/isw_dcbichgdbd_Secondary5: UUID="1be1eba5-4eb1-4592-87fb-0dd121bb4164" TYPE="swap"
```

Ubuntu is running on the ext4 partition and I am hoping to find a way to use the swap partition following it on the same volume.

Thanks!

---

### Post by cheapie on 2011-04-04
*points at your post*

/dev/mapper/isw_dcbichgdbd_Secondary5 is the device name.

Who knows if it'll work...

*remembering that my computer uses LVM, and therefore is similar*

Yeah, it'll probably work.

---

### Post by substanceD on 2011-04-04
Doh! I had answered the question myself and didn't even realize it. Yep, using /dev/mapper/isw_dcbichgdbd_Secondary5 worked. Thanks.

---

