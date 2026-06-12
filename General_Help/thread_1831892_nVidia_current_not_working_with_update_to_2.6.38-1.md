---
title: "nVidia_current not working with update to 2.6.38-11"
date: 2011-08-24
forum: General Help
---

### Post by stepheny on 2011-08-24
I have been using [Bumblebee]("https://launchpad.net/~mj-casalogic/+archive/bumblebee") to switch to my nvidia card when needed as my laptop uses nVidia Optimus technology. This has been working perfectly for a while now but after an Update Manager driven update to kernel 2.6.38-11 the nVidia driver is not loading any more. I have re-installed nvidia_current but that hasn't solved the problem. When I try to enable the nvidia card I get the following error message.  

```
FATAL: Error inserting nvidia_current (/lib/modules/2.6.38-11-generic-pae/updates/dkms/nvidia-current.ko): No such device 
```

If I do the command 
```
sudo modprobe nvidia
``` 
I get the resonse
```
FATAL: Module nvidia not found.
```
even after succesfully re-installing nvidia-current

I have googled "FATAL: Error inserting nvidia_current" but none of the suggestions seem to be relevant to this problem.

Any help would be appreciated.

---

### Post by LowSky on 2011-08-24
use the older Kernel...

pick it directly from GRUB to test.

if it does work you can edit GRUB using Startup Manager in the repos

---

### Post by stepheny on 2011-08-24
@LowSky.

Staying with an old kernel is not really a solution, is it?

---

### Post by PapaNoa on 2011-09-06
I am currently facing the same issue and tried all the fixes suggested in [http://ubuntuforums.org/showthread.php?t=1804394](http://ubuntuforums.org/showthread.php?t=1804394) to no avail. I also tried the 3.0.4 kernel, also no luck. Any news on this problem?

**Edit:** I hadn't in fact tried all the suggested fixes. In the end it seems purging *nvidia-current* did the trick for me. No downgrading of the kernel necessary (I do in fact use the oneiric kernel 3.0.4).

---

### Post by stepheny on 2011-09-16
I tried the solutions in your link and tried purging nvidia-current but the problem remains.

---

### Post by foureyesboy on 2011-09-16
Kernel after 2.6.37 needs an update Nvidia module.  I used the ubuntu-x-swat PPA.

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade

---

### Post by stepheny on 2011-09-16
I opened the update manager and under settings I ticked the "Pre-released updates" under the Updates tag. After downloading and installing the new packages nVidia, and therefore Bumblebee, started working again.

---

### Post by stepheny on 2011-09-17
oops, I spoke too soon. nVidia worked just once and after that the > FATAL: Error inserting nvidia_current (/lib/modules/2.6.38-11-generic-pae/updates/dkms/nvidia-current.ko): No such device
 warnings started again.I also tried foureyesboy's tip to no avail.

Fortunately for me the nVidia GPU is a second GPU and so I can use my Ubuntu laptop without it but for those with only a nVidia GPU this must be a nightmare.

---

