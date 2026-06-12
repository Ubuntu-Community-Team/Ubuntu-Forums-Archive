---
title: "Update killed nvidia!!!"
date: 2010-01-11
forum: General Help
---

### Post by llawwehttam on 2010-01-11
Just ran updates on my laptop.

Yesterday the nvidia drivers were working fine but after todays update to the kernel when I reboot I get the 'Ubuntu is running in low graphics mode' warning.

The message is 

(EE) NVIDIA: Failed to load the NVIDIA kernel module.
Please Check you
(EE) NVIDIA: system's kernel log for additional messages.
(EE)Failed to load module"nvidia"(module specific error, 0)
(EE) No drivers available.



I tried ```
sudo nvidia-xconfig
```but it did nothing.

I'm not a noob but I'm no good with graphics.
Any help appreciated.

EDIT: im the past I have seen this and to fix I have had to rebuild the kernel module.

Is there a shorter way?

EDIT:
I have fixed it by re-installing the nvidia drivers but I don't want to be doing this every time I get a kernel update!!!
I thought it should re-compile itself when It updates.
Unless I did somthing stupid.

---

### Post by atropa on 2010-01-11
How exactly did you install your Nvidia driver?

Via System/Hardware drivers (+ synaptic)

or with a driver installer obtained from nvidia's website?

I do it the latter way and after a kernel update I usually have to reinstall the invidia driver

---

### Post by WildeBeest on 2010-01-11
Any time I have an issue with NVidia drivers such as the low resolution problem, this thread has always worked for me.
 
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
 
It'll work with whichever version you plan to use.

---

### Post by llawwehttam on 2010-01-11
> **WildeBeest said:**
> Any time I have an issue with NVidia drivers such as the low resolution problem, this thread has always worked for me.
 
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
 
It'll work with whichever version you plan to use.

I do it the latter way so thanks for this.

---

### Post by llawwehttam on 2010-01-11
Is it possible to run the script manually? If so how?

---

### Post by llawwehttam on 2010-01-11
I tried to run it manually but it just puts a new file called 1 in the/lib/modules/ folder. I have a vague idea what's causing the problem. The driver exists in my latest two kernel's but not in an older one.
 
Would the script check all the folders and as it finds a missing nvidia.ko in the older kernel folder install any way?
 
If so how can I prevent this?

---

### Post by llawwehttam on 2010-01-11
If I want to run the script manually could I replace $1 with $KERNEL

and put somthing like 

KERNEL='uname -r'

at the beginning?
I'm not sure exactly how to put it.
Any help appreciated.

---

### Post by llawwehttam on 2010-01-11
woop woop I managed to do it all by myself.
I fell so accomplished..... a script I fiddled with that works.... and doesn't break things!!!

My version ( for running manually if the driver doesn't install in the update) is 

```
#!/bin/bash
#

# Set this to the exact path of the nvidia driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
DRIVER=/usr/src/nvidia-driver
KERNEL=`uname -r`

# Build new driver if it doesn't exist
if [ -e /lib/modules/$KERNEL/kernel/drivers/video/nvidia.ko ] ; then
    echo "NVIDIA driver already exists for this kernel." >&2
else
    echo "Building NVIDIA driver for kernel $KERNEL" >&2
    sh $DRIVER -K -k $KERNEL -s -n 2>1 > /dev/null

    if [ -e /lib/modules/$KERNEL/kernel/drivers/video/nvidia.ko ] ; then
        echo "   SUCCESS: Driver installed for kernel $KERNEL" >&2
    else
        echo "   FAILURE: See /var/log/nvidia-installer.log" >&2
    fi
fi

exit 0
```It appears to be working.

---

### Post by pbrane on 2010-01-11
That script is supposed to be run by dpkg. Thats's why it is installed to /etc/kernel/postinst.d/

You really have to follow that thread from the beginning. Next time you update your kernel, you can manually re-install the nvidia driver. That's all you have to do. But if you follow the thread that WildeBeest posted from the beginning you won't have that issue anymore.

---

### Post by llawwehttam on 2010-01-12
> **pbrane said:**
> That script is supposed to be run by dpkg. Thats's why it is installed to /etc/kernel/postinst.d/

You really have to follow that thread from the beginning. Next time you update your kernel, you can manually re-install the nvidia driver. That's all you have to do. But if you follow the thread that WildeBeest posted from the beginning you won't have that issue anymore.

As I had already installed the drivers before I found the script will my edited script run ok ( for running manually after an update if the other script doesn't work)  or will I have more problems?

I read through the guide from the beginning to see how it worked and $1 means the current kernel when run by dpkg but not when manually run by me?
Could someone please explain this for me.

Also could someone clarify what

```
sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null

```does as I don't understand it and I have seen on other threads that extra arguments are added for similar things.

> **amesdaq said:**
> Is it just me or did anyone else have errors with the script because of the license agreement not being accepted? I think the link in the script that reads

```
sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null
```should maybe be modified to look like

```
sh $DRIVER -K -k -a $1 -s -n 2>1 > /dev/null
```But I am no pro at all so maybe I am just doing something wrong but that change worked for me


I would like to improve my scripting but I'm not that confident.
Thanks

EDIT: 
If the instructions worked here : [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

I don't see why I have to follow all the instructions in the thread WildeBeest posted.

Just to clarify I DID follow this step :

```
sudo mv NVIDIA-Linux-x86-173.14.05-pkg1.run /usr/src
sudo ln -s /usr/src/NVIDIA-Linux-x86-173.14.05-pkg1.run /usr/src/nvidia-driver
```which is the driver the script depends on.

---

### Post by pbrane on 2010-01-12
If you run the nvidia script with the *--advanced-options* arg it will print the options and quit. That will explain the options. The end of the line is just redirecting the output to /dev/null. Basically what this line does is re-compile the driver for the new kernel without reconfiguring X and without removing the old module.

The $1 is the first argument to the script. You maybe can run it as is by typing something like *update-nvidia `uname -r`*. Not sure though, never tried it.

And you are right, you do not have to do all of the steps in that thread. I only do the relevant steps in a new install. As long as you have the driver source installed to /usr/src and a link to the driver you can install the update-nvidia script to /etc/kernel/postinst.d and it will take care of creating a kernel module for the new kernel.

Have a look at this nvidia site for some details on the driver installation for linux. [http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/README/chapter-04.html]("http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/README/chapter-04.html") This will help to understand what the driver source is capable of. Lots of neat features.

---

### Post by beezwings on 2010-03-15
Hi there, I'm a noob so I wasn't able to follow all of that, but I'm having the same problem as the original poster. I tried following the steps on [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) but that didn't work. The drivers aren't even listed anymore in the "Hardware Manager" so I tried reinstalling a NVIDIA driver using ENVY, but that didn't work. I'm still running low-graphics mode (and running videos are choppy). Please help!

---

