---
title: "Home folder on separate partition"
date: 2010-01-16
forum: General Help
---

### Post by akand074 on 2010-01-16
Hello,
This is most likely already asked so I apologize if its a repeat but I was going to do a clean install of Ubuntu on a new hard drive I'll be purchasing soon, I always have a separate storage partition for all my data, but I heard it was good to also have your home folder on a separate partition and thinking about it I can really see why. Anyways searching the internet I found some sites explaining how to move your already existing home folder to a separate partition but I would rather create it initially in a separate partition (well in my case it will be a completely different hard drive). Anyways is there anyway I can have my home folder created on a separate hard drive during the initial installation or will I have to do the clean install and then boot into it and copy my home folder into the storage partition and I guess...link it? so the OS knows that its the home folder. Anyone know enough about this to give me a hand?
Thanks a lot for the help!

---

### Post by sgosnell on 2010-01-16
Easy as pie.  When you run the installer, the partition window will come up, and when it does, choose to specify the partitions manually.  If there is only one partition on the drive, you'll have to make another, or use a different drive.  The easy way is to boot to the LiveCD, then run GParted, or Partition Editor, depending on what the Start/Administration menu says.  They're the same thing, just a different term in some versions.  Partition the drive to the sizes you want, then run the install program.  Select the appropriate partitions or drives for / and for /home, and Ubuntu will happily install that way for you.  You can choose to format the partitions or not, your choice.

---

### Post by akand074 on 2010-01-17
Oh sweet so just like I put "/" as the mount point for my ubuntu partition, I'll make the mount point "/home" for my storage partition? and I'm good to go?

---

### Post by sgosnell on 2010-01-17
Yes.  You can use any available partitions or drives for either, or if you want more, you can put other system folders on other partitions, however you like.

---

### Post by akand074 on 2010-01-17
Sounds easy enough, last question. If /home is on a separate partition during installation. Will it automatically set it to mount on boot or would i have to do that myself? Not that its a labour intensive thing to do

---

### Post by ratcheer on 2010-01-17
It will be automatic. As long as everything works, properly.

Tim

---

### Post by sgosnell on 2010-01-17
If you tell the installer to mount a partition or drive as /home, it will be mounted automatically that way until you change it.

---

