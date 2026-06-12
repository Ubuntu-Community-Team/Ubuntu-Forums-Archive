---
title: "Ubuntu 9.04 / 2.6.28.13 problems"
date: 2009-07-04
forum: General Help
---

### Post by evillmonkey on 2009-07-04
I updated to the new kernel yesterday, rebooted and found my machine in serious trouble.

I get the following error when it starts up:
Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to slve this.

(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
((EE) Screen(s) found, but none have a usable configuration.

Hitting Ok, I can enter the low-graphics mode, however my networking is now disabled.

If I boot into the previous kernel, I get the same error message, but I have networking.


I've tried several steps that I've found through a search, but nothing seems to have any effect:
*nvidia-xconfig
*reinstall kernel and restricted modules


Any help would be greatly appreciated!

---

### Post by PmDematagoda on 2009-07-04
How did you install your Nvidia driver at first? 

Also, how do you connect to the internet?

---

### Post by evillmonkey on 2009-07-04
> **PmDematagoda said:**
> How did you install your Nvidia driver at first? 

Also, how do you connect to the internet?

I meant to mention that. The internet is wired.

The Nvidia driver (I think) was installed through the Hardware Drivers package. If that makes sense?

---

### Post by PmDematagoda on 2009-07-04
> **evillmonkey said:**
> I meant to mention that. The internet is wired.

The Nvidia driver (I think) was installed through the Hardware Drivers package. If that makes sense?

Ok, booting up Ubuntu in the new kernel, can you execute the following commands:-
```
cat /var/log/Xorg.0.log > ~/xorg.log
```
and 
```
dmesg > ~/dmesg.log
```
and attach the created files here?

---

### Post by evillmonkey on 2009-07-04
The dmesg log was too large to attach, so I threw them up on my site:

[http://evillmonkey.com/ubuntu/dmesg.log](http://evillmonkey.com/ubuntu/dmesg.log)

[http://evillmonkey.com/ubuntu/xorg/log](http://evillmonkey.com/ubuntu/xorg/log)


Thanks.

---

### Post by PmDematagoda on 2009-07-04
dmesg doesn't seem to have anything out of the ordinary, so I cannot be sure about the networking problem.

About the Nvidia problem, try reinstalling the Nvidia driver using:-
```
sudo apt-get remove nvidia-glx-180 && sudo apt-get install nvidia-glx-180
```
after which you reboot the system and see if there is any improvement.

---

### Post by evillmonkey on 2009-07-04
Thanks for the advice. I tried as you suggested, but I'm still getting the same error message.

I'd rather not reformat, as I'd like to actually learn how to deal with this issue, but I'm at a loss really.

Again, thanks for the suggestions!

---

### Post by s1300045 on 2009-07-05
I am unfortunately another victim of this kernel update. My way of getting around it is hitting ESC when grub comes up and switch to older kernel. I will try to install the latest nvidia driver and see how it goes.

---

### Post by cwhisperer on 2009-07-06
> **PmDematagoda said:**
> dmesg doesn't seem to have anything out of the ordinary, so I cannot be sure about the networking problem.

About the Nvidia problem, try reinstalling the Nvidia driver using:-
```
sudo apt-get remove nvidia-glx-180 && sudo apt-get install nvidia-glx-180
```
after which you reboot the system and see if there is any improvement.

This solved my problem, great job ;)

---

