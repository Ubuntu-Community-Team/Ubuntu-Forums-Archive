---
title: "Azureus Problem!"
date: 2005-03-13
forum: General Help
---

### Post by cdhotfire on 2005-03-13
At first it worked wonderful, but now everytime i open it up, it says you have closed Azureus in a wrong manner or something.  Then it goes good for about 10 minutes and then it shutsdown for some reason, and the cycle continues, can anyone help me out?

---

### Post by kassetra on 2005-03-13
[QUOTE=cdhotfire]At first it worked wonderful, but now everytime i open it up, it says you have closed Azureus in a wrong manner or something. Then it goes good for about 10 minutes and then it shutsdown for some reason, and the cycle continues, can anyone help me out?[/QUOTE]

Ok, I've had this problem before.  Here's how I fixed it.  Let me know if this doesn't work.

1. Open Azureus and let it get all started up.
2. Close it all down from the menu.  (The "nice" way)
3. Start it back up.

---

### Post by cdhotfire on 2005-03-13
ya i though that would work also, but it hasnt, ive actually came accross this problem many but many times. I even re installed ubuntu once to see if it would fix it, but no luck.  And yesturday, i left the comp on all day before i went to work and i get back and  Azureus is not even open and the torrent was at 1 percent, what a waste of electricity :(.  But anyways thxs for trying to help :)

---

### Post by oobuntoo on 2005-03-24
Anybody has problem with Azureus not downloading to FAT32 partition? I can read and write to this partition just fine. I also have the Tools -> Options... -> Files -> "Enable incremental file creation" option in Azureus checked like many people suggested. When I try downloading to FAT32 partition, I get 

Error:/mnt/fat32/...  (Permission denied),open fails(....

This is how I mounted my FAT partition through fstab

/dev/sda5       /mnt/fat32      vfat    defaults,auto,uid=1000,gid=1000	 0  0



Any help is appreciated.  ](*,)

---

### Post by oobuntoo on 2005-03-24
:oops: Never mind! I figured it out. I made some changes to my fstab like this

/dev/sda5       /mnt/fat32  vfat    rw,users,auto,umask=000  0  0

---

### Post by egg on 2005-04-09
[QUOTE=cdhotfire]At first it worked wonderful, but now everytime i open it up, it says you have closed Azureus in a wrong manner or something.  Then it goes good for about 10 minutes and then it shutsdown for some reason, and the cycle continues, can anyone help me out?[/QUOTE]
 I'm having the same problem.. works for a while, then crashes. I'd like to know how I can fix this :-o

thnx

---

