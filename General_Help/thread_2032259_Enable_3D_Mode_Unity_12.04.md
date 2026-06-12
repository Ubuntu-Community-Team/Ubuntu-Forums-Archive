---
title: "Enable 3D Mode Unity 12.04"
date: 2012-07-23
forum: General Help
---

### Post by Ditchdoc7893 on 2012-07-23
Ok, guys. I thought I had this figured out, but I can't find the xorg.conf file to enable compositing on my new netbook installation. I just did this very same thing on my desktop and there were no hiccups or flaws. All I had to do was go in and edit the xorg.conf file in /etc/X11/xorg.conf. I have an NVIDIA graphics card and have installed the latest driver. Suggestions?

---

### Post by bogan on 2012-07-23
Hi!, **ditchdoc7893**,

From a Terminal run: ```
sudo apt-get update
sudo update-grub
``` And watch for any errors.

Have you run Nvidia Xserver settings? or:```
sudo nvidia-settings
``` ?? You may need to install the later, depending on how you installed the "latest"driver version.

BTW, What version is it?. nvidia-current or downloaded .run file.?

Chao!,** bogan**.

---

### Post by Ditchdoc7893 on 2012-07-24
I ran both the sudo apt-get and sudo update grub. No error messages were generated. When I run the command sudo nvidia-settings, it returns the following error statement:

You do not appear to be using the NVIDIA X driver. Pease edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server. Any ideas?

---

### Post by NikTh on 2012-07-24
Hi , 
you can follow the recommendation .. 
```
sudo nvidia-xconfig
```and reboot the pc. 

and give the result of these commands
```
cat /etc/lsb-release && uname -r
apt-cache policy nvidia-current
lspci -nnk | grep -iA2 vga
```Thanks

---

### Post by Ditchdoc7893 on 2012-07-24
I may have screwed up. I went back and double checked the specs of this netbook. Seems that it may have Intel GMA 950 graphics. I'm far from familiar with this. It is an Asus Eee PC 1005 HAB. This has been my utility book that worked fine with 10.10 without any modifications to anything. Any ideas?

---

### Post by NikTh on 2012-07-25
Hi , 
please give the result of this command 
```
lspci -nnk | grep -iA2 vga
``` so we can see for sure what is your graphics card and what driver you use. 
Then we can guide you . 

Thanks

---

### Post by Ditchdoc7893 on 2012-07-25
Results are as follows:

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Intregrated Graphics Controller [8086:27ae] (rev 03)
            Subystem: ASUSTeK Computer Inc. Device [1043:8340]
            Kernel driver in use: i915

---

### Post by deadflowr on 2012-07-25
Your running intel drivers, there will be no need for an xorg.conf file. The drivers are built into the kernel. If it seems like the system isn't recognizing it follow this link:

[http://askubuntu.com/questions/129227/how-do-i-install-intel-hd-graphics-driver-on-ubuntu-12-04]("http://askubuntu.com/questions/129227/how-do-i-install-intel-hd-graphics-driver-on-ubuntu-12-04")

If your not sure whether or not your system is running Unity-3d, try this:
Terminal
```
/usr/lib/nux/unity_support_test -p
```

If any of the responses are returned no, then your system cannot run in Unity-3d mode.

---

### Post by NikTh on 2012-07-25
Hi , 
it seems that you are running Intel driver , and your card Must have unity 3D support. 

Give the results of deadflowr's command . 

Purge nvidia drivers.. it not needed
```
sudo apt-get purge nvidia-current nvidia-settings 
sudo rm /etc/X11/xorg.conf
``` 
reboot your pc. 

Thanks

---

### Post by TheRealEdwin on 2012-07-25
I don't mean to hijack the thread but what about those of us with hybrid video cards? I have one of the Optimus that uses the Intel for most things but can switch tot he Nvidia when needed (420M) but I can't seem to get Ubuntu setup to do so.

```
edwin@Dreadmaul:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
	Subsystem: Dell Device [1028:046e]
	Kernel driver in use: i915
--
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0df1] (rev a1)
	Subsystem: Dell Device [1028:046e]
	Kernel driver in use: nvidia
edwin@Dreadmaul:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Error: GLX is not available on the system

```

---

### Post by NikTh on 2012-07-25
> **TheRealEdwin said:**
> I don't mean to hijack the thread but what about those of us with hybrid video cards? I have one of the Optimus that uses the Intel for most things but can switch tot he Nvidia when needed (420M) but I can't seem to get Ubuntu setup to do so.

Hi , 
try to use [_**Bumblebee project**_](http://bumblebee-project.org/)

further problems will be best to post to a new thread . 

Thanks

---

### Post by poetgrant7 on 2012-09-23
I'm with the last guy. I have a Geforce GT 520M and get the exact same error message as he does. I also haven't found any thread close to solving this problem yet.

---

### Post by Peter K Nicol on 2012-11-18
Hello.

I have a new install of 12.04 but, apart from one a few hours, I only have Unity 2d. Nvidia current and nvidia settings have been purged and I have the output below.
Any suggestions about where I should go next would be gratefully received.

peter@pterpc:~$  /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD SUMO2
OpenGL version string:  2.1 Mesa 9.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by bogan on 2012-11-19
Hi!, **Peter K Nicho**l,

Have you run: ```
unity # or:
unity --reset # or try:
sudo apt-get install --reinstall ubuntu-desktop
```If so, with what results? [ Re-boot after each]

Please Post:```
 uname -r
cat /etc/lsb-release 
lspci -nnk | grep -iA3 vga
ps ax | grep unity
```Chao!,** bogan.**

---

### Post by Peter K Nicol on 2012-11-19
Thanks for the reply. It will be a couple of days until I get back to the machine but I will let you know how I get on.

---

### Post by Peter K Nicol on 2012-11-20
Rather inconclusive results. A few warnings including "this shouldn't happen" and it is still in 2d.
Ouput requested below

peter@pterpc:~$  uname -r
3.2.0-33-generic
peter@pterpc:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
peter@pterpc:~$ lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9644]
	Subsystem: ASUSTeK Computer Inc. Device [1043:84c8]
	Kernel driver in use: radeon
	Kernel modules: radeon
peter@pterpc:~$ ps ax | grep unity
 1745 ?        Sl     0:06 unity-2d-panel
 1746 ?        Sl     0:51 unity-2d-shell
 1832 ?        Sl     0:05 /usr/lib/unity/unity-panel-service
 1902 ?        Sl     0:00 /usr/bin/python /usr/lib/unity-lens-video/unity-lens-video
 1903 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-music-daemon
 1904 ?        Sl     0:00 /usr/lib/unity-lens-files/unity-files-daemon
 1905 ?        Sl     0:01 /usr/lib/unity-lens-applications/unity-applications-daemon
 1973 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
 1983 ?        Sl     0:00 /usr/bin/python /usr/lib/unity-scope-video-remote/unity-scope-video-remote
 3524 pts/1    S+     0:00 grep --color=auto unity
peter@pterpc:~$

---

### Post by bogan on 2012-11-20
Hi!, **Peter K Nico**l,

Your Post shows 'unity-2d-shell' running, which is the 2d launcher, and in 12.04 that is not a default, and the unity-3d programs all look normal.

Furthermore the 'unity_support_test' shows 3d supported, but the OpenGL using Gallium/mesa, which implies Nouveau.

Have you got 'nomodeset' in as a boot option?, that could force 'mesa' and degrade graphics.

You also Posted that the nvidia drivers had been purged - they should not have been there in the first place.

So I am thoroughly confused. Did you check that any Nouveau blacklist entry, made for the nvidia driver install, has been removed from /etc/module.d??

I do not know a lot about ATI Radeon video cards & GPU's, but i am surprised to see it using thje 'radeon' kernel module, and not 'fgrlx'.

Googling: "ATI [1002:9644]" & "*1043*:*84c8*. AMD Radeon HD 6410D" did not produce anything of obvious significance to me; perhaps it might help you.

Hopefully, someone more knowledgeable in AMd/ATI/Radeon matters will come forward to help.

Chao!,** bogan**.

---

### Post by bogan on 2012-11-21
Hi!, **Peter K Nicol**,

Second thoughts:

Where did you get the " this should not happen" messages? and what was 'this' ??

Have you checked if there are other drivers available in 'Additional drivers' ??

Chao!, **bogan.**

---

### Post by Peter K Nicol on 2012-11-23
Thanks for the help. Again it might be a few days until I can get anything done.
The messages were part of the output from 
unity # or:
and
unity --reset # or try:
which, incedentally, both hung.
I will report back next week.

---

### Post by Peter K Nicol on 2012-12-09
Is the answer in here somewhere or is it part of the same problem?

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485)

---

### Post by bogan on 2012-12-10
> **Peter K Nicol said:**
> Is the answer in here somewhere or is it part of the same problem?

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485)HI!, Peter K Nicol, That Link refers to the notorious nvidia 295.40 driver, which was bug ridden.

There is no connection with the ATI/AMD Gpu and the Radeon driver.

Chao!, **bogan.**

---

### Post by Peter K Nicol on 2012-12-11
Ok I understand. Thanks for yout patience but what about this - especially some of the links at the RHS.
 
[http://askubuntu.com/questions/122339/how-to-enable-unity-3d-support-in-12-04-using-open-source-drivers-for-radeonhd-c](http://askubuntu.com/questions/122339/how-to-enable-unity-3d-support-in-12-04-using-open-source-drivers-for-radeonhd-c)

I tried one of the suggestions:
peter@pterpc:~$ sudo apt-get install xserver-xorg-video-ati
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-ati is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
peter@pterpc:~$ lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9644]

---

### Post by bogan on 2012-12-11
Hi!,** Peter K Nicol**,

What are the "7 not updated" there is an updated Kernel being offered which might alter things.

The 'xserver-xorg-video-ati' is installed by default with the kernel, regardless of what video card you have.

Chao!, **bogan.**

---

