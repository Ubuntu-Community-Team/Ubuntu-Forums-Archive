---
title: "Updating and problems after it"
date: 2011-04-04
forum: General Help
---

### Post by Tom4z on 2011-04-04
Hello everyone! 

I decidet to update my computer with update manager. After installing all updates (took a while) i restarted my system.

- The First thing that i dont like is that there are more options to choose in the grub now. Can this be fixed somehow so i could have only 1 option?

- I am updating once every month only. And is it only me experiencing this or is the sistem getting slower and more laggy after every update? Also some games stoped to work.


**SO THE QUESTION IS** : Update the sistem or dont update the sistem? I need help with this one :S

---

### Post by Kirboosy on 2011-04-04
I would highly recommend updating the system. Some of those updates are security updates that will increase your system protection. Also some are stability updates or general feature enhancements for programs are also in some of the updates. 

Updating once a month would work just don't neglect to update your system at all.


For removing those extra GRUB entries you can use [Ubuntu Tweak]("http://ubuntu-tweak.com/") you can also clean up the package cache with this tool as well. 


Good Luck!
~Caboose

---

### Post by snowpine on 2011-04-04
Welcome to the forums Tom!

The options in your GRUB menu are called "kernels." Sometimes when you update, you get a new version of the kernel. This includes bug fixes, security patches, support for new hardware, etc. But sometimes new kernels cause problems--for example your computer might run slower. So it is **a good thing** that you have multiple kernels to choose from in GRUB. Try choosing your older kernel and see if it solves your problem (because it is not normal for your install to slow down over time). Good luck!

ps I personally update my system at least once a week. It is good to have bug fixes and security patches, I think. :)

---

### Post by ajgreeny on 2011-04-04
> **snowpine said:**
> Welcome to the forums Tom!

The options in your GRUB menu are called "kernels." Sometimes when you update, you get a new version of the kernel. This includes bug fixes, security patches, support for new hardware, etc. But sometimes new kernels cause problems--for example your computer might run slower. So it is **a good thing** that you have multiple kernels to choose from in GRUB. Try choosing your older kernel and see if it solves your problem (because it is not normal for your install to slow down over time). Good luck!

ps I personally update my system at least once a week. It is good to have bug fixes and security patches, I think. :)
It is also possible that you may need to reinstall any graphic card driver that you already installed for the original kernel, as they are not updated automatically and do not carry over from kernel to kernel.

My system is set to daily updates, which I think is the default, as I have not changed things for that part of the system.  I install updates immediately when they become available, and I certainly don't see my system getting slower.

---

### Post by Tom4z on 2011-04-06
Thanks for the answers :) i appreciate your help ;)

---

### Post by techunit on 2011-04-06
If the solution is solved please mark the thread as solved. It makes it easier for all of us to move on and help others.

---

### Post by DogMatix on 2011-04-06
Computer Janitor will remove the old kernels I believe

System>Administration>Computer Janitor

(personally I don't remove them)

This wouldn't explain why your system has become sluggish though. :confused:

---

### Post by techunit on 2011-04-06
It doesn't really the kernels only take up about 40MB each and are automatically removed after a certain amount of time. I would leave them alone especially if you use grub.

---

