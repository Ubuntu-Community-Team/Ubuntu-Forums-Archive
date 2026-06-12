---
title: "Problem converting raid 1 to raid 5"
date: 2011-09-24
forum: General Help
---

### Post by justinmiller621 on 2011-09-24
Hey all,

I apologize in advance because some of these error codes are going to be from memory...

I was following this guide:

[http://scottwallace.posterous.com/converting-raid1-to-raid5-with-no-data-loss](http://scottwallace.posterous.com/converting-raid1-to-raid5-with-no-data-loss)

to convert my raid 1 array to raid 5. Since my array didn't have the OS on it, I figured I could do this all without booting into recovery mode or from a live cd. So I stopped the raid and issued the create command from the link.

It recognized the devices were part of an array and asked if I wanted to continue. I said yes, and I believe it created the array, but then failed adding my first device, saying that the device was in use.

So I rebooted into recovery mode, and I tried to reissue the create command (since it appeared to fail the first time). This time I didn't get very far -- it said that my one drive was not suitable to be added into any array. I reissued the command, this time with a -v and mdadm added that the device was in use, strange.

So then I did (on a whim) an fdisk -l and noticed that there was a raid device created, /dev/md127. I thought that was strange so I stopped that, thinking that it had been temporarily created from my initial first attempt. Once stopped, I could reissue the create command, and it appeared to go more "smoothly" this time. 

So once I did that, the link says that you should be able to, at this point, mount your raid device, and everything should still be there. I tried mounting the device, but that failed. The error from dmesg was a "bad geometry" error referring to an invalid block size.

I did a quick cat /proc/mdstat and noticed that the raid was performing a "recovery". Is this possibly why it wouldn't mount? Should I wait until the recovery is finished before trying anything else? 

Is there ANYTHING else I can try? Or is my only option to reformat? That wouldn't be the worst thing in the world... I have everything backed up, but I'd have to transfer nearly 1 TB of data so my only motivation to fix this w/o data loss is to avoid the time it would take to transfer that data. 

Thanks,
Justin

---

