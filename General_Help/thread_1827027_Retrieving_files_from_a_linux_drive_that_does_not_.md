---
title: "Retrieving files from a linux drive that does not boot, access denied."
date: 2011-08-17
forum: General Help
---

### Post by Reichtor on 2011-08-17
I have a linux drive that I can no longer boot up. Before it comes up to the login screen, it gives me the following error and does not take keyboard/mouse on ps/2 input. To the best of my knowledge, I'm using ubuntu 10.4, thats the version that I installed off the cd. Its possible it might have updated itself to 10.8. I could be wrong about that.

"Ubuntu is running in low graphics mode: The following error was encountered. You may need to update your configuration to solve this.

(EE)Nvidia(0):Failed to load nvidia kernel
(EE)Nvidia(0):***aborting***
(EE) No devices detected

I thought it might be the video card/drivers that was causing this so I removed my nvidia altogether and tried using on board video, and its the same story with just the third error instead.

I've also tried booting in recovery mode, and it gets to a page where it says its changing the video...ratio, I think.(I can get the exact message if neccessary)

If anyone knows a simple fix for this, great, I would be deeply appreciative.  But I'm more interested in getting the data thats off the drive itself. I've tried booting from the install cd but it says that I don't have the necessary permissions to view the folder. I've tried installing a utility on a windows partition on a seperate hard drive that allows me to view the linux partitions and it still gives me access restrictions and wont pull it up. 

I have the administrative username/password, but I just can't seem to get to a place where it will allow me to log in to that user. Any tips or advice would be a huge help. Thank you in advance for your time.

---

### Post by sffvba[e0rt on 2011-08-17
> **Reichtor said:**
> I have a linux drive that I can no longer boot up. Before it comes up to the login screen, it gives me the following error and does not take keyboard/mouse on ps/2 input. To the best of my knowledge, I'm using ubuntu 10.4, thats the version that I installed off the cd. Its possible it might have updated itself to 10.8. I could be wrong about that.

"Ubuntu is running in low graphics mode: The following error was encountered. You may need to update your configuration to solve this.

(EE)Nvidia(0):Failed to load nvidia kernel
(EE)Nvidia(0):***aborting***
(EE) No devices detected

I thought it might be the video card/drivers that was causing this so I removed my nvidia altogether and tried using on board video, and its the same story with just the third error instead.

I've also tried booting in recovery mode, and it gets to a page where it says its changing the video...ratio, I think.(I can get the exact message if neccessary)

If anyone knows a simple fix for this, great, I would be deeply appreciative.  But I'm more interested in getting the data thats off the drive itself. I've tried booting from the install cd but it says that I don't have the necessary permissions to view the folder. I've tried installing a utility on a windows partition on a seperate hard drive that allows me to view the linux partitions and it still gives me access restrictions and wont pull it up. 

I have the administrative username/password, but I just can't seem to get to a place where it will allow me to log in to that user. Any tips or advice would be a huge help. Thank you in advance for your time.

What may help is giving the **nomodeset **parameter to the kernel at boot-time (normally spamming F8 repeatedly at boot-time will bring you to the GRUB menu and you can do that)...


Good luck
404

---

