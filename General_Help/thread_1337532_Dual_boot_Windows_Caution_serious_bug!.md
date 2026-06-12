---
title: "Dual boot Windows Caution serious bug!"
date: 2009-11-25
forum: General Help
---

### Post by Pauly BC on 2009-11-25
I discovered a very serious flaw with the mounting of Windows drives last night. Ubuntu sees the Windows page file as blank space and will write files into that space, after which Windows will overwrite them with virtual memory activities.

From an unrelated issue I recently messed my hard drive and had to reinstall Windows and Ubuntu and restore our photos and personal files from backup. The backup restoration utility yielded tens of thousands of files, many of which duplicated several times. I have been logging in to Windows to load the restored files into the public documents folder but logging in to Ubuntu to use FSLint to weed out the dupes. I found Karmic was a little flaky in how it mounted Windows partitions in that it is extremely slow and now and then it unmounts the drive mid-operation.

I booted into Ubuntu and moved the restored files off the Windows partition and onto the Ubuntu partition to gain speed and avoid hangups. FSLint was very quick and responsive and I easily pared the files down to only one copy per. When I was finished I moved the 33.7GB of photos back to the Windows partition and rebooted back into Windows. As soon as Windows started to load I noticed the hard drive was grinding away much more than normal. I got into task manager and found it was steady at 100%, including an average of 200 drive faults per second! Every one of the hard drive faults was a page file collision, meaning more than one file referenced a bit on the HDD. I dug in further and found it was the afore-mentioned photos were colliding with the Windows page file (virtual memory). I closed all unnecessary programs and moved the photos folder onto a non-OS partition, which took about 3 hours to complete due to the collisions. In all the relocated folder is now 26.3GB and about 1 in 10 files is corrupted. That means I get to start all over again in restoring my files from backups and FSLint them down to normal.

---

