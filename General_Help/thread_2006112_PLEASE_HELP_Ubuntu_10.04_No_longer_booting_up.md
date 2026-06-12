---
title: "PLEASE HELP Ubuntu 10.04 No longer booting up"
date: 2012-06-18
forum: General Help
---

### Post by mztrujillo on 2012-06-18
I'm having a problem with getting my version of Ubuntu 10.04 to boot up. Last week the system crashed. I rebooted my machine, and rather than having Ubuntu go through its normal boot up process like it always has, it just kicks me out to a GRUB terminal, of which I know absolutely nothing about. My guess is that somehow the needed boot up files have become corrupted (my computer is a little old) due to the crash. 
Like I said, I know nothing about GRUB, and I have no idea how to use it to possibly get Ubuntu to load up again. Any help would be much appreciated.
 So bear in mind that Ubuntu was not installed as an actual hard-drive partition on my laptop. Rather it was installed with the Windows-as-host option. 
 In the worst-case scenario, if I cannot get Ubuntu to boot up I may have to resort to reinstalling the entire OS. However, I would prefer not to do this as I have some rather important files on the Ubuntu side, which I don't want to lose forever if I don't have to. So I have Windows-as-a-host installation. I know that from Ubuntu I can access the Windows file system directly through the /host directory. Is there not then a way for me to access Ubuntu's file directory directly on Windows? I would like to at least be able to salvage my needed files before I reinstall Ubuntu if I could. 
Thanks.

---

### Post by Arand on 2012-06-18
Try to boot it manually from the Wubi GRUB shell, as per [http://www.omaregan.com/?p=583](http://www.omaregan.com/?p=583)

EDIT:
Also, there are instructions on how to get files off the Wubi filesystem (in case restoring it doesn't work) over at [http://askubuntu.com/questions/130408/can-i-mount-a-wubi-disk-image-in-a-new-wubi-installation/130440#130440](http://askubuntu.com/questions/130408/can-i-mount-a-wubi-disk-image-in-a-new-wubi-installation/130440#130440)

---

