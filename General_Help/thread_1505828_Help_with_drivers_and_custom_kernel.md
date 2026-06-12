---
title: "Help with drivers and custom kernel"
date: 2010-06-09
forum: General Help
---

### Post by rampage355 on 2010-06-09
I have been using linux for a long time but have never really gotten into the nuts and bolts of it. I got a new laptop and have had a lot of issues with all distros of linux. So I found a post that showed me how to compile a custom kernel ([http://ubuntuforums.org/showthread.php?p=9419063#post9419063](http://ubuntuforums.org/showthread.php?p=9419063#post9419063)) post #11. All but one thing works well and that is the wireless. I have a realtek r8192se and there has been is issues with it being buggy, not working, locking up the computer. Well a few days ago realtek released new drivers and firmware. I tried to install and I get 
```
greg@my-desktop:~/Downloads/New Laptop Drivers/rtl8192se_linux_2.6.0017.0507.2010$ make
make[1]: Entering directory `/usr/src/linux-source-2.6.32'
make[1]: *** No rule to make target `Laptop'.  Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.32'
make: *** [all] Error 2

```
I have all the sources are installed.
```
greg@my-desktop:/usr/src$ ls
linux-ec2-source-2.6.32.tar.bz2
linux-headers-2.6.32.11+drm33.2-a505
linux-headers-2.6.32.11+drm33.2-a505_2.6.32.11+drm33.2-a505-10.00.Custom_amd64.deb
linux-headers-2.6.32-22
linux-headers-2.6.32-22-generic
linux-image-2.6.32.11+drm33.2-a505_2.6.32.11+drm33.2-a505-10.00.Custom_amd64.deb
linux-source-2.6.32
linux-source-2.6.32.tar.bz2
greg@my-desktop:/usr/src$ 

```
Could some please show me what i need to do or what i am doing wrong.

---

### Post by dcstar on 2010-06-10
> **rampage355 said:**
> I have been using linux for a long time but have never really gotten into the nuts and bolts of it. I got a new laptop and have had a lot of issues with all distros of linux. So I found a post that showed me how to compile a custom kernel ([http://ubuntuforums.org/showthread.php?p=9419063#post9419063](http://ubuntuforums.org/showthread.php?p=9419063#post9419063)) post #11. All but one thing works well and that is the wireless. I have a realtek r8192se and there has been is issues with it being buggy, not working, locking up the computer. Well a few days ago realtek released new drivers and firmware. I tried to install and I get 
```
greg@my-desktop:~/Downloads/**New Laptop Drivers**/rtl8192se_linux_2.6.0017.0507.2010$ make
make[1]: Entering directory `/usr/src/linux-source-2.6.32'
make[1]: *** No rule to make target `Laptop'.  Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.32'
make: *** [all] Error 2

```
I have all the sources are installed.
```
greg@my-desktop:/usr/src$ ls
linux-ec2-source-2.6.32.tar.bz2
linux-headers-2.6.32.11+drm33.2-a505
linux-headers-2.6.32.11+drm33.2-a505_2.6.32.11+drm33.2-a505-10.00.Custom_amd64.deb
linux-headers-2.6.32-22
linux-headers-2.6.32-22-generic
linux-image-2.6.32.11+drm33.2-a505_2.6.32.11+drm33.2-a505-10.00.Custom_amd64.deb
linux-source-2.6.32
linux-source-2.6.32.tar.bz2
greg@my-desktop:/usr/src$ 

```
Could some please show me what i need to do or what i am doing wrong.

Put the source in a path **without** any spaces and see what happens.

---

### Post by rampage355 on 2010-06-10
Thanks David, that did the trick. Did not know it was so picky.

---

