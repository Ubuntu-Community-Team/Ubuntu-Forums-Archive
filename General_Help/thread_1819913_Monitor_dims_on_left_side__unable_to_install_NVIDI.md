---
title: "Monitor dims on left side / unable to install NVIDIA driver"
date: 2011-08-06
forum: General Help
---

### Post by Eleos on 2011-08-06
Hello all,

I had installed Ubuntu 10.10 and there was a dim spot on the left side of the monitor.  I could move the window to the right, but anything on the left was dim, and if I set the window to full screen, the whole screen went dim.  I was able to find a fix online, I followed the instructions, and Voila! It was fixed, so I knew it was not a hardware issue.

I installed 11.04, and have the same dim screen issue, but I can't find the instructions that fixed it last time.

I tried to download and install the latest driver from NVIDIA, and I get this error:

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com]("http://www.nvidia.com").

If anyone has any fix for the dim screen, or can help me run the driver, I would appreciate it.

Thank you,

-Eleos

---

### Post by bruno9779 on 2011-08-06
The official Nvidia drivers need X to be shut off.

The fasted way to do this is in a tty session:

press ctrl+alt+F1

log in and run:

```
sudo service gdm stop
```

Now you are ready to install the drivers.

If I remember correctly, your computer will reboot on its own after install, otherwise run:

```
sudo service gdm start
```

---

### Post by Eleos on 2011-08-07
[FONT=Verdana][SIZE=2]Thanks for the reply.  I took your suggestion, and it is telling me NVIDIA is incompatible with nouveau.  I tried this command from the docs:

sudo apt-get --purge remove xserver-xorg-video-nouveau
[/SIZE][/FONT][FONT=Verdana][SIZE=2]However, when I tried to install the NVIDIA driver again, it again told me
NVIDIA is incompatible with nouveau.  Is there a different way to disable
nouveau?[/SIZE][/FONT]

-Eleos

---

### Post by Eleos on 2011-08-07
bruno9779's solution worked, thank you bruno9779 for the help.  

If you are having the same problem as I did, you just have to reboot after removing the Nouveau driver and before installing the NVIDIA driver.

In fact, the problem seemed to be fixed after the reboot and before I installed the NVIDIA driver, but I am having more problems after I installed the NVIDIA driver.  Now it hangs at "Stopping User Bootsplash".

I was going to tag this solved, but it is looking like I need to reinstall 11.04 and start over again.  Any ideas or suggestions would be appreciated.

Thanks,

-Eleos

---

### Post by Eleos on 2011-08-07
Ok, I reinstalled 11.04.  Here is what I did:

Opened a terminal, typed:

sudo apt-get install startupmanager 

In startup manager, I set the resolution to 1024x768 and color to 24 bits.

Then:

pressed ctrl+alt+F1

sudo service gdm stop

sudo apt-get --purge remove xserver-xorg-video-nouveau

sudo sh NV*

The installation told me that nouveau was still there, and created some kind of config file (it was too fast for me to copy), and the installation failed.  I then typed:

sudo service gdm start

Then I rebooted, and the dim screen is gone, at higher resolution.

I don't know why, but the last time, I rebooted, and was able to complete the installation of the NVIDIA driver, but then it hung at "Stopping User Bootsplash", so I am leaving well enough alone and not going to try and complete the installation.

I hope this is helpful for someone.

-Eleos

---

