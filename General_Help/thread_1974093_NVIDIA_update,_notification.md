---
title: "NVIDIA update, notification?"
date: 2012-05-05
forum: General Help
---

### Post by K4NEB on 2012-05-05
hey everyone.

currently i have my nvidia drivers disabled so i run normal unity.

how will i know when nvidia release a fix for the black screen problem?

will i get an update in the update manager? 

or wont i as i have the nvidia drivers uninstalled?

am i just going to have to install the drivers every so often to see if theres updates?

any help mucho appreciated :)

---

### Post by papibe on 2012-05-05
Hi K4NEB.

You can check for available versions even if you don't have it install. For example run this:
```
apt-cache policy nvidia-current
```
This is my output (up-to-date 10.04):
```
nvidia-current:
  Installed: 195.36.24-0ubuntu1~10.04.2
  Candidate: **195.36.24-0ubuntu1~10.04.2**
  Version table:
 *** 195.36.24-0ubuntu1~10.04.2 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/restricted Packages
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-security/restricted Packages
        100 /var/lib/dpkg/status
     195.36.15-0ubuntu2 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/restricted Packages

```
Take note of the 'candidate' version, and then you can check later if a new version becomes available.

BTW, I looked in the forums to see what kind of problem are you having, and my guess is that you are booting into a black screen. Is that your problem?

Could you post the result of these commands?
```
lspci -nn | grep -i vga

sudo lshw -C display
```
Regards.

---

### Post by K4NEB on 2012-05-06
ok thanks for that

and yes i got the black screen with my nvidia drivers installed so i un installed/disabled them so i can run normal unity.

the first command came up with invalid operation policy??

kane@kane:~$ apt-get policy nvidia-current
E: Invalid operation policy
kane@kane:~$ lspci -nn | grep -i vga
00:10.0 VGA compatible controller [0300]: NVIDIA Corporation C73 [GeForce 7050 / nForce 610i] [10de:07e3] (rev a2)
kane@kane:~$ 
kane@kane:~$ sudo lshw -C display
[sudo] password for kane: 
PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: C73 [GeForce 7050 / nForce 610i]
       vendor: NVIDIA Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:20 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff memory:feac0000-feadffff
kane@kane:~$ 
kane@kane:~$

---

### Post by K4NEB on 2012-05-06
or should i re install the drivers log into 2d and run the commands again?

im not that technical with all this sort of stuff :confused:

---

### Post by bogan on 2012-05-06
Hi!, **K4NEB**,

The command you want is:```
sudo apt-cache policy nvidia-current
``` But the present candidate version [6th May] is 295.40 and that is the one with all the bugs. Dont install it!!

You Posted:> how will i know when nvidia release a fix for the black screen problem?They alreadyhave!
The newest version from NVIDIA is 295.49 and is not yet available in a Ubuntu nvidia-current form.

 You have to download the 295.49....run file, and run it from a text terminal.

Edit:
If you still have a previous version of the nvidia driver installed, but disabled, you can easily check to find out if there is a new version available: run: > sudo nvidia-installer --latestThis will tell you what version is installed and the latest available, but will not alter anything.

Chao!, **bogan**.

---

### Post by papibe on 2012-05-06
> **K4NEB said:**
> the first command came up with invalid operation policy??
Oops.

As bogan pointed it out. The correct command is apt-cache. I corrected my post above.

Regards.

---

### Post by K4NEB on 2012-05-07
ahh ;)

kane@kane:~$ sudo apt-cache policy nvidia-current
[sudo] password for kane: 
nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1
  Version table:
     295.40-0ubuntu1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
        100 /var/lib/dpkg/status


im not really sure on how to download the latest 295.49 updated version :confused:

---

### Post by bluelord_ro on 2012-05-07
I have installed 295.49 driver vesion but cmd sudo apt-cache policy nvidia-current shows:

> 
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) precise/restricted amd64 Packages
        100 /var/lib/dpkg/status
     295.33-0ubuntu1~precise~xup1 0
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) precise/main amd64 Packages

---

### Post by bogan on 2012-05-07
Hi!, **bluelord_ro**,

You Posted:>  I have installed 295.49 driver vesion but cmd sudo apt-cache policy nvidia-current shows: ....295.40 What does the following show:```
 cat /sys/module/nvidia/version 
sudo nvidia-installer --latest  # This will not alter anything
``` but you must have an internet connection for it to work.

How did you install 295.49 with 'sh' and the .run file? 

Did you get any error messages?

What video card do you have?  Is it PCI or integrated - or both ??

Chao!, **bogan**.

---

### Post by bluelord_ro on 2012-05-07
For "cat /sys/module/nvidia/version" i have "295.49"
Lately i have experimented with my drivers. I have installed the beta version 302.. after that i have downgraded to 295.49 throw .run file.
I have a Gigabyte Geforce 560Ti graphic card. I have fresh installed Ubuntu 12.04 and i had problem with Plymouth resolution ... but i have manage that.

---

### Post by bogan on 2012-05-07
Hi!, **bluelord_ro**,

If ```
sudo nvidia-installer --latest
``` also shows 295.49 as installed, I would run ```
sudo apt-get remove --purge nvidia-current
``` as you certainly do not want both installed, and 295.40 is the bugged version.

It is just possible that you might have to re-install 295.49 again afterwards with ```
sudo nvidia-installer -f
```, but if everything seems to be OK I would forget about it.

Edit, afterthought, it might be a good idea to purge the cache.

Chao!,** bogan**.

---

### Post by ubuntu27 on 2012-05-09
Quoting fro another thread.

> **ubuntu27 said:**
> Currently, the [nVidia regression bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485") has been fixed for Ubuntu Quantal Quetzal. The bug fix for Ubuntu Precise Pangolin is in [precise-proposed]("https://wiki.ubuntu.com/Testing/EnableProposed"). So, we will appreciate if the affected users could test it and tell us about their experience.

Good luck everyone!
**Fingers Crossed**


We can provide feedback by posting a comment on [bug#982485]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485")

---

### Post by bogan on 2012-05-12
Hi!, **All**,

[COLOR=RoyalBlue]**New Ubuntu Nvidia 295 driver for 12.04 available.**[/COLOR]

 Here is a Link for instructions to get the 295.49 xswat updates Ubuntu nvidia driver:

[http://www.noobslab.com/2011/09/nvid...0-oneiric.html]("http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html")

It successfully installed nvidia-current version " 295.49-0ubuntu1~precise~xup1".

Chao!, **bogan**.

---

### Post by stoneage on 2012-05-12
I have a problem with that:-
The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-10 but it is not installable

I'm now stuck with the 295.40 until the driver is updated ?

---

### Post by ubuntu27 on 2012-05-13
I recently (few hours ago) got notified that the nVidia drivers has been officially fixed for Ubuntu 12.04 and has been uploaded to the main repos.

Can you guys confirm?
And does it work?

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485)

---

### Post by bogan on 2012-05-13
Hi!, **stoneage**,

You Posted: > I have a problem with that:-Assuming by that you meant using the Link in my Post #13:
 then try uninstalling and purging nvidia*, installing 'build-essentials' for your kernal version, and reinstalling 295.45 as 'nvidia-current'.

For detailed instructions see Post #280 of MAFoElffen's Blank Screen Sticky in the Installations & Upgrades Forum:
[http://ubuntuforums.org/showthread.php?t=1743535&page=73](http://ubuntuforums.org/showthread.php?t=1743535&page=73)

Chao!, **bogan**.

---

### Post by stoneage on 2012-05-13
> **bogan said:**
> 
You Posted: Assuming by that you meant using the Link in my Post #13:
 
Yes, I did mean that.

It was my fault too, I neglected to purge before upgrading. I purged the ppa, then re-enabled it and all is now well again.

Thanks.

---

### Post by K4NEB on 2012-05-14
so the current version has been updated now??

it still says it 295.40 in the software centre in the current version. cmon ubuntu chop chop!

---

### Post by K4NEB on 2012-05-14
> **bogan said:**
> Hi!, **All**,

[COLOR=RoyalBlue]**New Ubuntu Nvidia 295 driver for 12.04 available.**[/COLOR]

 Here is a Link for instructions to get the 295.49 xswat updates Ubuntu nvidia driver:

[http://www.noobslab.com/2011/09/nvid...0-oneiric.html]("http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html")

It successfully installed nvidia-current version " 295.49-0ubuntu1~precise~xup1".

Chao!, **bogan**.


ARGH! it wont let me type my password in the terminal! why is it doing this! stupid thing! :@

---

### Post by Cavsfan on 2012-05-14
Here is how I always upgrade my nVidia driver for my Geforce 9800 GT.
I am on 245.49. Which came out on 2012.05.03.  It works for 10.04, 12.04 and anything in between.

It only takes me about 15 minutes to upgrade my driver but, I have done it a few times.

Once you do it this manual way, you will have to manually update with the next version if so desired.

There is a How to (from this forum) at the bottom that is an easy way to update newly installed kernels with the driver.

You will need to perform that How to after you upgrade your driver or else the next kernel installed will not get the driver.
But, it is pretty simple.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?p=11798460#post11798460_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=11798460#post11798460")

---

### Post by K4NEB on 2012-05-15
> **Cavsfan said:**
> Here is how I always upgrade my nVidia driver for my Geforce 9800 GT.
I am on 245.49. Which came out on 2012.05.03.  It works for 10.04, 12.04 and anything in between.

It only takes me about 15 minutes to upgrade my driver but, I have done it a few times.

Once you do it this manual way, you will have to manually update with the next version if so desired.

There is a How to (from this forum) at the bottom that is an easy way to update newly installed kernels with the driver.

You will need to perform that How to after you upgrade your driver or else the next kernel installed will not get the driver.
But, it is pretty simple.

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?p=11798460#post11798460_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=11798460#post11798460")

ok thanks i might give it a whirl then.

anyone know when they are actually going to update the current version???

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html)

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

     ```
nvidia-installer --latest
``` now returns: v295.53 and the currently installed version, without altering anything.
     

     ```
nvidia-installer -f
``` will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

### Post by Cavsfan on 2012-05-17
> **bogan said:**
> Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html)

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

     ```
nvidia-installer --latest
``` now returns: v295.53 and the currently installed version, without altering anything.
     

     ```
nvidia-installer -f
``` will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]


Cool! It just came out yesterday. Thanks! :)

---

### Post by K4NEB on 2012-05-19
can you please explain step by step how i install the lastest driver?

i downloaded it from the link you posted from the nvidia website.

now how do i install it?????

---

### Post by bogan on 2012-05-19
Hi! K4NEB,

You Posted:```
can you please explain step by step how i install the lastest driver?
```If you have a version of the nvidia driver already installed you can use the commands in my Post #22 from a text terminal.

If 'nvidia-installer --latest' returns 'command not known', then see 'Alternatively' below, or use the link provided by Cavsfan's Post #20.

To get a text terminal either boot to recovery mode and select the 'drop to root terminal option', or from a GUI screen open a terminal and run ```
sudo service lightdm stop
```If that does not give you a log-in prompt, press 'Ctrl_Alt+F1' to get one, log-in, type your password + 'Enter' and then the commands. 
If your Internet connection is OK then ```
nvidia-installer --latest
``` will tell you what is installed and what available, without altering anything.```
nvidia-installer -f
``` will download & install 295.53 after un-installing the previous version.

Alternatively: If you do not have an installed version of the nvidia driver or
If you do not have a working Internet connection then cd to the folder where the nvidia .run file is, enter 'ls' - that is small 'L' - to confirm you are in the right place and enable you to check the exact spelling.
```
sudo chmod a+x NV  # press 'Tab' to complete
sudo sh NV                   # ditto
``` In either case follow the on screen prompts using 'Tab' to navigate and ignore error messages, then reboot.

Chao!, **bogan**.

---

### Post by efflandt on 2012-05-19
You did not say which Ubuntu version you are running, but for nvidia in 11.10 I had to use **nomodeset** kernel boot parameter, but in 10.10 or 12.04 I did not need to use that.

I am not sure which version is nvidia-current.  But if you add the x-swat ppa repository current version is 295.53.

```
**dpkg-query -l nvidia***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  nvidia-173                  <none>                      (no description available)
un  nvidia-180-modaliases       <none>                      (no description available)
un  nvidia-185-modaliases       <none>                      (no description available)
un  nvidia-96                   <none>                      (no description available)
ii  nvidia-common               1:0.2.35                    Find obsolete NVIDIA drivers
ii  nvidia-current              295.53-0ubuntu1~oneiric~xup NVIDIA binary Xorg driver, kernel module and VDPAU library
un  nvidia-current-modaliases   <none>                      (no description available)
un  nvidia-libvdpau             <none>                      (no description available)
un  nvidia-libvdpau-ia32        <none>                      (no description available)
un  nvidia-libvdpau1            <none>                      (no description available)
un  nvidia-libvdpau1-ia32       <none>                      (no description available)
ii  nvidia-settings             295.53-0ubuntu1~oneiric~xup Tool of configuring the NVIDIA graphics driver
un  nvidia-va-driver            <none>                      (no description available)
un  nvidia-vdpau-driver         <none>                      (no description available)
un  nvidia-vdpau-driver-ia32    <none>                      (no description available)
```If you have only used Ubuntu packages to install nvidia drivers, x-swat can be added with:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```If you have current nvidia drivers installed, use Additional Drivers to Deactivate those, reboot, then Activate nvidia-current (only last step if not using nvidia drivers at this time).

If you manually installed nvidia drivers using a script or something other than Ubuntu packages, not sure how you would clear that out.

PS: I guess I should have read the other pages of this post.  In the past when I tried to use apt-get to remove and install different nvidia versions (in an effort to get my failing GT 430 working), I did something wrong, ended up with remnants of both versions that I could not seem to fix, and had to reinstall Ubuntu.

---

