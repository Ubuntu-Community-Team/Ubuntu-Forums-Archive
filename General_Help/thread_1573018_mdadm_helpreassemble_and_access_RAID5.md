---
title: "mdadm help/reassemble and access RAID5"
date: 2010-09-12
forum: General Help
---

### Post by disconap on 2010-09-12
Ok, so I had a server crash and now finally have everything back up and running except the file drives; they are in a RAID5, and attempts to assemble and mount have been...odd at best.  When trying to assemble, I'm getting a response that it's already assembled, and when trying to mount I'm getting:

mount: /dev/md127 already mounted or /mnt/raid busy

and here is the result of cat /proc/mdstat:

```

md_d0 : inactive md127[4](S)
      2930287424 blocks
       
md127 : active raid5 sdb[0] sde[3] sdc[1]
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/3] [UU_U]
      
md_d127 : inactive sdd[2](S)
      976762496 blocks
```

Which is odd, since md_d0 and md_d127 shouldn't actually exist.  Help?

EDIT TO ADD: running 10.04 server

---

### Post by disconap on 2010-09-12
Well, no idea what was going on, but a clean install of 10.04 solved it.  *shrug*

---

