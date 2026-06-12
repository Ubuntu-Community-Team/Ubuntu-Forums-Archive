---
title: "DifficultyInstalling Sound Drivers"
date: 2011-04-25
forum: General Help
---

### Post by Zocco on 2011-04-25
Hi
Following the sound problems I had some months ago I have decided to have one more try at sorting things out. I am still having problems getting sound from my system but I have now found linux drivers on the CD that came with the computer mother board. However when I try to extract the tar ball as in step 1 of the installation instructions listed at the end of this post I get the message that I do not have the right permissions "to extract archives in the folder - file:///media/G71-MV31010/Sound/Realtek/Linux" Which resides in the folder -  alsa-driver-0.9.2.

Additionally If and when I manage to extract the files I will need to follow the instructions from 2 to 5 below. Because I am a total Numpty the only instruction that seems clear to me is step 5, reboot the machine.

Could anyone please explain in words of one syllable how to extract and install these drivers.

The Following is the Readme Text that comes with the driver installation.

**************************************************
The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:A1.8 
Linux Source Code for ALC audio codec 
 
Installation: 
This Source Code is from [www.alsa-project.org](www.alsa-project.org). 
For driver installation, please follow below steps.  
 
Step 1. Unzip source code 
        tar xfvj alcsound.tar.bz2 
 
Step 2. Turn on sound support (soundcore module) 
 
Step 3. Complied source code 
    a. ./Configure 
    b. make install 
    c. ./snddevices 
 
Step 4. Edit your /etc/modules.conf or conf.modules depending on the Distribution 
     (Please refer to the attached modules.conf) 
 
Step 5. reboot your machine 
 
Note:     1. The most detail information, can refer the INSTALL file in the alcsound.tar.bz2. 
    2. Kernel Version must be 2.2.14 or later. 
    3. All mixer channels are muted by default. You must use a native 
        or OSS mixer program to unmute appropriate channels. 
    4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux. 
    5. The driver added to support the SPDIF functoin. 
    *******************************************************

Any assistance will be gratefully appreciated

Dave

---

