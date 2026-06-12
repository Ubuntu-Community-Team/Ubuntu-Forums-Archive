---
title: "Restart Nautilus File Copy Crash"
date: 2011-05-07
forum: General Help
---

### Post by MikeyDL on 2011-05-07
One of the big things that always had me wincing was file copies over the network to cifs shares.  It always seemed about 1/3 as fast as a windows desktop copy.  At home I've got three d-link NAS servers which can host NFS shares so I decided to see if I could setup mounts on my client laptop as NFS shares and see if the file copies were any faster.  After researching it bit figured out how to mount the NFS shares on my desktop.  Started coping files and a wondrous 32MB per second file copy rate was rapidly transfering an avi file from my laptop to the NAS.  However, at 90% on bar the transfer seems to get stuck in the file copy dialog.  Did a couple of test copies and in each case for the NFS transfer the file completes the copy over but the file copy copy and nautilus windows freeze at about 90%.  I end up having to close the windows and eventually a "force quit" error dialog pops up and I can restart the nautilus windows.  

I had two questions.  

1.  Is this most likely a but that I should report or could it be a setup issue for the mount.  I've got r/w permissions setup on the NAS an the CLI line I use is:

```
sudo mount -t nfs ds9:/mnt/HD_a2 /home/michael/shares/ds9
```

Are there any options I'm missing in the mount command?

2.  Is there any command to restart nautilus in the CLI so I don't have to wait for the "force quit" line to pop up?

Thanks!

---

### Post by everthonvaladao on 2011-05-31
> **MikeyDL said:**
> 
2.  Is there any command to restart nautilus in the CLI so I don't have to wait for the "force quit" line to pop up?


To quit nautilus on the command line, type on a terminal
```
nautilus --quit
```

And, if necessary, to force it to restart type on a terminal
```
killall -9 nautilus
```

---

