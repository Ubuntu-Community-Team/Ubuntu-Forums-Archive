---
title: "No Plymouth Splash Screen on 10.04"
date: 2010-07-01
forum: General Help
---

### Post by irrdev on 2010-07-01
I just installed Kubuntu 10.04 on my Desktop computer. Prior to KDM loading, all I get is a blank, black screen with no Plymouth splash screen. I'm confident that this issue is not related to KDE but would apply to all Ubuntu variants. Here are my computer specs:
Kubuntu 10.04 x64 running with all updates
Dell Studio Desktop
Intel Quad-Core Processor 2.66Ghz 
8GB ram
Intel Integrated Graphics

I should note that I have full desktop effects running smoothly under KDE with compositing enabled, so my integrated graphics is not necessarily the problem unless Plymouth is not loading the graphics drivers successfully. 
Any suggestions and/or ideas on how to fix this problem? Any advice would be greatly appreciated! ;)

---

### Post by dino99 on 2010-07-01
remove/purge then reinstall plymouth

---

### Post by garvinrick4 on 2010-07-01
Start graphic drivers first in boot #540801 launchpad
```
sudo -i
```
```
echo FRAMEBUFFER=y > [/etc/initramfs-tools/conf.d/splash]("file:///etc/initramfs-tools/conf.d/splash")
```
```
update-initramfs -u
```
ctrl/d
```
exit
```

---

### Post by irrdev on 2010-07-01
> **garvinrick4 said:**
> Start graphic drivers first in boot #540801 launchpad
```
sudo -i
```
```
echo FRAMEBUFFER=y > [/etc/initramfs-tools/conf.d/splash]("file:///etc/initramfs-tools/conf.d/splash")
```
```
update-initramfs -u
```
ctrl/d
```
exit
```
Thank you - that solved the "problem." I'm not sure if this can be really classified as a bug, however, since it only happens on fast computers which can really quickly check the file system before booting directly to X. I personally like seeing a splash screen, but technically it actually slows down the booting time. The only way to truly work around this would be to preload the graphic drivers... I don't think Plymouth is ready for prime-time yet, and would have liked to have seen Ubuntu stick with USplash for 1-2 more releases.

---

### Post by garvinrick4 on 2010-07-02
I believe that is about right irrdev.


[Scott James  Remnant]("https://launchpad.net/%7Escott")             wrote             on 2010-03-18:               [                 **Re: X server starts before Plymouth**               ]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2")                                              [  #2]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2")                                                        The problem here is the graphics  drivers; on your system they're taking longer to load than it takes to  check and mount the filesystem - so there's no reason to start the  splash screen, since we can already start X.
 On HDD-based systems this is worse because we do the ureadahead phase  before loading drivers; thus it can take a long time for a splash to  appear.
 One "solution" is to use the initramfs and start plymouth as a  critical step:
   echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
  update-initramfs -u
 But that introduces a significant delay into boot just to get the  splash screen up for the rest of it

---

### Post by philinux on 2010-07-02
> **garvinrick4 said:**
> I believe that is about right irrdev.


[Scott James  Remnant]("https://launchpad.net/%7Escott")             wrote             on 2010-03-18:               [                 **Re: X server starts before Plymouth**               ]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2")                                              [  #2]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2")                                                        The problem here is the graphics  drivers; on your system they're taking longer to load than it takes to  check and mount the filesystem - so there's no reason to start the  splash screen, since we can already start X.
 On HDD-based systems this is worse because we do the ureadahead phase  before loading drivers; thus it can take a long time for a splash to  appear.
 One "solution" is to use the initramfs and start plymouth as a  critical step:
   echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
  update-initramfs -u
 But that introduces a significant delay into boot just to get the  splash screen up for the rest of it

I've got this "fix" in lucid and I did a before and after test with bootchart and the boot times did not change for me. nVidia 8600GT.

---

