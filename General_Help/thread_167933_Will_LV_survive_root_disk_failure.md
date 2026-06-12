---
title: "Will LV survive root disk failure?"
date: 2006-04-29
forum: General Help
---

### Post by theProf on 2006-04-29
I just created a new file server with 4 hard drives:

hda is a 60 GB drive with root mounted on a 58G partition and swap on the other 2G

hde, hdg, and hdi are 160G drives in a raid5 array called md0

I have a 320G volume group created on this array called lvm-raid

I have a 200G logical volume on this called "documents".  I'm going to use this to store files that are near and dear to me like music, video, pictures, etc...

[B]
The Question:[/B]
If my 60G drive fails (the one with root on it), will a new installation (on a new HD) be able to detect my data and the logical volume structure?

I would think, yes, as this is supposed to be a safe way to store data (and I will be creating backups anyway), but I just want to make sure before I forge ahead and load this thing with data.

Thanks for your help.
Marc

---

