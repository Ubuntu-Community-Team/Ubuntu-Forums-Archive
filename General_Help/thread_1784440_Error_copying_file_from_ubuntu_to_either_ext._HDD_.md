---
title: "Error copying file from ubuntu to either ext. HDD or over network"
date: 2011-06-17
forum: General Help
---

### Post by negatiiv on 2011-06-17
Hi All,

I have Ubuntu 10.10 on my nettop PC. I've downloaded a bunch of video including a 1.1gb MKV file. The folder it resides in is shared via smb. Normally I access this folder by my windows 7 pc and stream the video over the network. However this video I was watching locked about 90% of the way through (nearly done the episode! argh!). I tried it over again but the file wasn't accessible according to windows.. so I VNC'd into my ubuntu pc and everything was super lagged, I couldn't even get it to restart. So I powered it off, back on, and tried watching the video again. Locked up in the same spot. I thought I would then just copy the whole file over to my windows 7 pc (ntfs) and watch it from there.. but the file copy stops near the end also! Then I tried copying the file to an external HDD (also ntfs) and it does the same thing!

Okay I thought, if this was windows, I would run a ```
chkdsk /f
``` to fix any filesystem corruption. I googled and decided to run ```
sudo shutdown /Fr now
```. Ubuntu rebooted, found some issue, and rebooted again. Still doesn't work.

So my question after that longwinded explanation is.. How do I find out the cause of the corruption? What tools can I use, logs, etc, such as the event viewer in windows? Should I just give up and download the file again? 

Thanks!

---

### Post by dcstar on 2011-06-17
> **negatiiv said:**
> 
..........
 Normally I access this folder by my windows 7 pc and stream the video over the network. However this video I was watching locked about 90% of the way through (nearly done the episode! argh!). I tried it over again but the file wasn't accessible according to windows.. so I VNC'd into my ubuntu pc and everything was super lagged, I couldn't even get it to restart. So I powered it off, back on, and tried watching the video again. Locked up in the same spot. I thought I would then just copy the whole file over to my windows 7 pc (ntfs) and watch it from there.. but the file copy stops near the end also! Then I tried copying the file to an external HDD (also ntfs) and it does the same thing!

.........

Use the Disk Utility to do a SMART scan of your disk for bad blocks.

---

