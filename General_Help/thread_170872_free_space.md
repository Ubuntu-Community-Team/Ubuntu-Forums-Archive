---
title: "free space"
date: 2006-05-05
forum: General Help
---

### Post by bobanshirl on 2006-05-05
can anyone help,I copied and printed the full install for ubuntu with NTFS it was going along great exactly as each page which had the command Highlighted told me then as always happens I clicked on the Yes button expecting a screen with 

                  IDE1 master (hda)     etc etc
                  #primary                  etc etc     ntfs
                    pri/log                      etc  FREE SPACE
                  #5 LOGICAL                               fat32

the problem was there was no entry for FREE SPACE  what happens if I continue without Free Space I dont know how to tell it I want Free Space.
Where I have typed etc etc these enties are okay it is the missing free space entry what do I do.

---

### Post by kingmonkey on 2006-05-05
hda5 is a logical partition that contains extended partitions therefore it shouldnt contain any freespace.

Hope this helps because I dont really know what your problem is.

---

