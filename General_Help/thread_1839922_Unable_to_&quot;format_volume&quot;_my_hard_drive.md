---
title: "Unable to &quot;format volume&quot; my hard drive"
date: 2011-09-06
forum: General Help
---

### Post by freeman45 on 2011-09-06
Hello, i'm trying to save my data on a crashed hard drive and transfer it to a new one through linux (ubuntu 10.4) 
 
I'm trying to follow my friends instructions, but when it comes time to **"format volume"** the new hard drive under **NTFS **( old HD is running windows, new one is blank) it gives me some error code saying it didn't work. 
 
 
I'm told that I can also format it to FAT instead of NTFS but mentions that I won't be able to transfer files over 4G, which is a problem for me since i'm 3/4 of the way through "witcher 2" and don't want to loose my save files :redface:
 
 
I believe i'm trying to format it just so I can mount the drive, but i'm new to linux and so very clueless. Is there a way I can save my files over 4G, or should I just format it under FAT?
 
thank you

---

### Post by Linux_junkie on 2011-09-06
Has you mounted the new hard drive? If your performing this action through an Ubuntu live CD run Nautilus and select the old hard drive if its been mounted and copy or move your files over to the new hard drive once its been mounted.

---

### Post by freeman45 on 2011-09-06
How exactly do I access Nautilus? I'm pretty new at this. 
 
 
It is my understanding that I need to mount both hard drives in order to transfer data. But in order to mount my new drive, I must format it. But I can't seem to format it under the correct "NTFS" setting. 
 
Is there another way around this problem?

---

### Post by grahammechanical on 2011-09-06
Is Ubuntu 10.04 on a Live CD? What exactly is the error message? If you are using the Live CD in the try Ubuntu option, are you using Gparted to format the drive? Make sure the drive is not mounted before you set the program to format the drive.

Is there a drive icon on the desktop? Right click on it and select Unmount and then run Gparted.

Regards.

---

### Post by Miljet on 2011-09-06
"some error code saying it didn't work" isn't really very helpful in trying to isolate any problem. It would be most helpful if you could copy the exact error message and post it here.

Oh and by the way, welcome to the Ubuntu forums.

---

