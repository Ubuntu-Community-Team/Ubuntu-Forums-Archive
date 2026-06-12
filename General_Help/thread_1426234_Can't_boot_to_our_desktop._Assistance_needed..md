---
title: "Can't boot to our desktop. Assistance needed."
date: 2010-03-10
forum: General Help
---

### Post by Kir_B on 2010-03-10
[SIZE=1]Hey everyone. We would very much appreciate any and all guidance that anyone can offer. 

We've got an old pentium computer dual booting Ubuntu and Windows XP. We've purchased a [/SIZE] [SIZE=1][PNY GeForce FX 5200 256MB 128-bit DDR PCI Video Card]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814133233") for  it. After installing it, we had full access to the XP and installing drivers from there went without a hitch and appears to work fine. When we tried to boot into Ubuntu, all we got was the (initramfs) prompt, and we're both relatively new to the fantastic world of Linux and so we have no idea what to do with it and finding information concerning our issue has been fruitless, as we can't seem to find anyone that has had a similiar problem. 

We then uninstalled the card, booted up Ubuntu and tried to install drivers via administration>Hardware Drivers, but the computer doesn't appear to have any on board graphics, and so Ubuntu won't allow us to use any of the drivers in the hardware drivers (via administration). We then did a tonne of research and followed a few tutorials for installing Unix drivers from the Nvidia web site. [/SIZE] [SIZE=1]

One of the tutorials that we followed involved doing a Control+Alt+F1 and then shutting down the GDM to install the new drivers. After installing the new drivers, we for what ever reason, couldn't restart the GDM. After what appears to be a failed attempt at installing the driver, we cannot access the desktop and are now presented with the following message (when booting in normal kernel mode): [/SIZE] [SIZE=1]"[/SIZE][SIZE=1]Ubuntu is running in low-graphics mode.  The  following error was encountered. You may need to update your   configuration to solve this. (EE) No devices detected.[/SIZE][SIZE=1]". The only 4 options are: 

#1)Run Ubuntu in low-graphics mode for just one session. This results in a black screen without a prompt, Control+Alt+F1 gets us a prompt in the top left of the screen that isn't flashing and we can't do anything at all.[/SIZE] [SIZE=1]
 
#2)Reconfigure graphics. This gives us three options of which we have no idea what to do with: 
1) Use default (generic) configuration, 
2) Create new configuration for this hardware, 
3) Use your backed-up configuration, along with the OK and Cancel option, which, the latter option takes us back to the original 4 options. 

#3)Troubleshoot the error. There are four options here: [/SIZE] [SIZE=1]
1)Review the xserver log file (no idea what to do with this), 
2)Review the startup errors (no idea what to do with this), 
3)Edit configuration file (no idea what to do with this), 
4)Archive configuration and logs (which has been done).  

#4)Exit to console login. (gets us a prompt in the top left of the screen that isn't flashing and we can't do anything at all).[/SIZE] [SIZE=1]

We are in dire need of some guidance, before attempting any of the options in "Reconfigure graphics" , as we have no idea what to do with any of it and recovery mode doesn't get us anywhere either.[/SIZE] 

[SIZE=1]A **huge** **thank you** to everyone that looks at this for us, as we have been stuck at this point for more than a week now.[/SIZE]

[SIZE=1]Thanks again, Kirby[/SIZE] :o

---

### Post by dcstar on 2010-03-10
> **Kir_B said:**
> [SIZE=1]Hey everyone. We would very much appreciate any and all guidance that anyone can offer. 

We've got an old pentium computer dual booting Ubuntu and Windows XP. We've purchased a [/SIZE] [SIZE=1][PNY GeForce FX 5200 256MB 128-bit DDR PCI Video Card]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814133233") for  it.


Ubuntu does not support old Nvidia cards past version 8.04 - install that if you want support for that old hardware.

---

### Post by Kir_B on 2010-03-10
> **dcstar said:**
> Ubuntu does not support old Nvidia cards past version 8.04 - install that if you want support for that old hardware.

[SIZE=1]Before I purchased this card, I researched this issue for between two and three weeks, 6-18 hours a day and have continued to research this issue for the past couple of weeks also, and I have yet to stumble across any information that would indicate any such thing.

If this is truly the case, can someone please point me in the direction of this resource that has somehow eluded me thus far.

Thanks a lot. Kirby  

[/SIZE]

---

### Post by pastalavista on 2010-03-10
I suppose this is the best you'll find for support for that card now.

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1")

You could try installing 'envy-ng' which will sometimes helps a lot finding the right Nvidia (and ATI) drivers.

---

### Post by Kir_B on 2010-03-10
[SIZE=1]> **pastalavista said:**
> I suppose this is the best you'll find for support for that card now.

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1)[/SIZE]> **pastalavista said:**
>   

[SIZE=1]You could try installing 'envy-ng' which will sometimes helps a lot finding the right Nvidia (and ATI) drivers.[/SIZE][SIZE=1]

Thanks for the information, but we found out about that right after we lost access to our desktop and will definitely be taking that route either after we regain access to our desktop or have given up and reinstalled.  :o

     Thanks again. Kirby[/SIZE]

---

### Post by Kir_B on 2010-03-10
[SIZE=1]A huge Thanks to everyone that took the time to  look at our problem.
  
We got extremely frustrated with this issue and decided to step out on  the limb and try a few of the options listed above. We got very fortunate in that the first thing we tried worked.

First thing that we did was option #3's third option, "[/SIZE][SIZE=1]Edit configuration file[/SIZE][SIZE=1]". We looked at the configuration file before we messed everything up and we happened to remember that it was completely blank, so we deleted the contents. We then selected the fourth option ([/SIZE][SIZE=1]Exit to console login[/SIZE][SIZE=1]) and low and behold it booted to the desktop. Unbelievable.

All the kernels work now, but we still don't have access to the new card. At least everything seems to be working fine. Now all we have to do is remove the new driver and find a better resource for a tutorial on installing video cards and their drivers. The big problem being that this computer doesn't have any on board graphics and so it won't allow us to install any drivers via Administration>Hardware Drivers. I guess the bigger problem being that, with the card installed, we really get stuck at the "(initramfs)" prompt and have absolutely no access to our desktop.

If anyone knows any tricks, please don't hesitate to post them, as we are keeping an eye on this thread via instant Email notification.
[/SIZE] 
[SIZE=1]Thanks so much everyone. Kirby[/SIZE]

---

### Post by 2hot6ft2 on 2010-03-10
What am I missing?

The OP has a GeForce FX 5200
[NVIDIA shows a driver for it here]("http://www.nvidia.com/object/linux_display_ia32_173.14.25.html")

> Version: 173.14.25
Release Date: 2010.02.11

Release highlights
    * Added support for X.Org xserver 1.7
    * Improved compatibility with recent Linux kernels
    * Updated nvidia-installer to detect newer Debian distributions that use /usr/lib32 instead of /emul/ia32-linux as the 32-bit library path

I have a GeForce MX 440
[NVIDIA shows a driver for it here]("http://www.nvidia.com/object/linux_display_ia32_96.43.16.html")

> Version: 96.43.16
Release Date: 2010.02.11

Release highlights
    * Added support for X.Org xserver 1.7.
    * Improved compatibility with recent Linux kernels.
    * Updated nvidia-installer to detect newer Debian distributions that use /usr/lib32 instead of /emul/ia32-linux as the 32-bit library path.

For mine drivers are available in System > Administration > Hardware Drivers. And it works just fine.
They are both listed on the page that was linked to earlier (screenshot below):
> **pastalavista said:**
> I suppose this is the best you'll find for support for that card now.

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1")

You could try installing 'envy-ng' which will sometimes helps a lot finding the right Nvidia (and ATI) drivers.
I'm seriously confused as to why one is supported by 9.10 and the other is not. I know X.Org has changed and we're up to 2.6 or something now, but I'm still not getting this. One but not the other.

Other than the drivers version numbers, I'm not seeing a difference.

Enlighten me.

Time to eat I'll be back in a while, thanks

---

### Post by Kir_B on 2010-03-10
[SIZE=1]Thanks for the response 2hot6ft2. I'll try to sum this up for you in the least amout of time possible.

[/SIZE]  [SIZE=1]We can't boot into Ubuntu with the new card installed. It boots into the grub sceen just fine, but when we select a kernel it goes to the "(initramfs)" prompt, from which we have no idea how to proceed. 

If we try to install a driver without the card installed (via Anministration>Hardware Drivers), Ubuntu tells us "there are no proprietry drivers in use", and then, won't allow us to select one.

We really are baffled as to how to proceed.

Thanks. Kirby  :-k
[/SIZE]

---

### Post by 2hot6ft2 on 2010-03-10
> **Kir_B said:**
> [SIZE=1]Thanks for the response 2hot6ft2. I'll try to sum this up for you in the least amout of time possible.

[/SIZE]  [SIZE=1]We can't boot into Ubuntu with the new card installed. It boots into the grub sceen just fine, but when we select a kernel it goes to the "(initramfs)" prompt, from which we have no idea how to proceed. 

If we try to install a driver without the card installed (via Anministration>Hardware Drivers), Ubuntu tells us "there are no proprietry drivers in use", and then, won't allow us to select one.

We really are baffled as to how to proceed.

Thanks. Kirby  :-k
[/SIZE]
You're welcome. I don't have a solution for what to do at the initramfs prompt there seems to be little information on the topic that looks like it will be much help. But I do have some ideas you can try.

I didn't mean for you to explain your situation again I was hoping that one of those that said your new card is no longer supported as to why if it falls in the same category as mine which is supported and works and mine is probably 5+ years old. So once you get into ubuntu you might be able to load a driver for your card.

Now I have seen some info on the initramfs prompt when trying to fix a problem I had with a usb install and here are some things you can try but I don't know if they will be any help since your problem is not the same. Besides they didn't work for me but like I said mine was another issue.

I've got a question first. Before you got your new card, did you install a graphics driver for the other card/chip?
If so perhaps booting with the new card out and removing the other driver will help.

Here's some other ideas you might try:

Changing the kernel boot options by removing "quiet splash" and adding "debug break=mount".

Typing exit at the initramfs prompt, sometimes more than once worked for some people.

You could also try the graphics card in different pci slots, there may be an IRQ conflict in ubuntu that's not there in windows since windows may handle it differently.

EDIT: I just came accross your other thread while looking for a solution and am I to understand there's no built in graphics chip or another card?
> **Kir_B said:**
> [SIZE=1][/SIZE][SIZE=1]without the card installed,[/SIZE][SIZE=1] is that this computer doesn't have any on board graphics[/SIZE]

Guess you're done trying to fix it and on to shopping for a new graphics card.

---

### Post by Kir_B on 2010-03-10
[SIZE=1]Thanks so much for your input 2hot6ft2. Whether or not there is any on board graphics chip is not confirmed either way, as both of us are relatively new to the internals of computers. All we know for sure, is that Ubuntu doesn't recognize anything needing a proprietary driver. Having said that, if there is something in the bios that has been or needs to be changed, we don't know about it. I'm pretty sure that we've reset the bios to it's defaults at some point, but it might be worth another go.

Thanks for the suggestions. We are far from giving up at this point, as there must be a way to introduce new hardware where there was none previously, besides, we're on fixed incomes and more shopping is out of the question, at least for a few more months.[/SIZE] [SIZE=1]

Again, thanks so much for taking the time to look into this for us. sometimes it just takes a different approach to finding answers in the Linux world.[/SIZE] [SIZE=1]

[/SIZE] [SIZE=1]              Kirby[/SIZE]  ](*,)

---

### Post by 2hot6ft2 on 2010-03-11
> **Kir_B said:**
> [SIZE=1]Thanks so much for your input 2hot6ft2. Whether or not there is any on board graphics chip is not confirmed either way, as both of us are relatively new to the internals of computers. All we know for sure, is that Ubuntu doesn't recognize anything needing a proprietary driver. Having said that, if there is something in the bios that has been or needs to be changed, we don't know about it. I'm pretty sure that we've reset the bios to it's defaults at some point, but it might be worth another go.

Thanks for the suggestions. We are far from giving up at this point, as there must be a way to introduce new hardware where there was none previously, besides, we're on fixed incomes and more shopping is out of the question, at least for a few more months.[/SIZE] [SIZE=1]

Again, thanks so much for taking the time to look into this for us. sometimes it just takes a different approach to finding answers in the Linux world.[/SIZE] [SIZE=1]

[/SIZE] [SIZE=1]              Kirby[/SIZE]  ](*,)
You're welcome. Let's see, if you look at the back of the computer case your cable from your monitor is either plugged into the new graphics card or there "may" be another connector of the same type on the computer which would be the built in graphics chip. The connector has a thumb screw on each side which you have to unscrew to unplug and screw in to secure it to the connector.

Most modern computers have a built in graphics chip which is what the other connector would be for. Just make sure it looks the same 3 rows of holes to match the connection on the cable from the monitor.
Graphics connections have 3 rows while serial only has 2 rows other than that they are pretty close to the same size.

Windows usually requires that you disable the on-board graphics in device manager when installing another graphics card like a PCI or AGP card. It would have been part of the instructions that came with the card.

Here's an idea. If you just put the card in and started it up. Did you change where the monitor was plugged into the computer to the new graphics card?

If not then windows is still using the built in graphics but when you boot ubuntu it's trying to use the new card but no monitor is connected to it.

So you need to make sure of just what the monitor is connected to. The new card or the built in chip.

There may be a conflicting driver, like an ATI driver for the on-board chip but you installed a NVIDIA card.
If you used ubuntu on the computer before adding the new card try taking the new card out and connecting the monitors cable to the other connector and booting up.

If that works then go to System > Administration > Hardware Drivers
Select the driver that shows as "Active" and select "Disable".
Once it finishes it will want you to reboot. Choose not now, then shut the computer down.

Now reinstall the graphics card and connect the monitors cable to it then boot up the computer and see if that works.
If it does then go to Applications > Accessories > Terminal
and use this in it
```
sudo apt-get update
```
when that finishes close the terminal and go back to System > Administration > Hardware Drivers and see if it has a driver for your new card.

If it does then select it in the top section and click "Activate", it will download and install the driver then it will want you to reboot. Go ahead and reboot and you should be set on the ubuntu side.

Hope that helps.

P.S. I don't think the issue is in the BIOS.

---

### Post by Kir_B on 2010-03-12
[SIZE=1]Thanks again for the response[/SIZE] [SIZE=1]2hot6ft2. 

We have only one connector on the back of the computer that the monitor can be plugged into when the card isn't plugged in. When the card is installed, there are three connections for a monitor, the original outlet and two outlets from the card. The answer to your question as to which outlet we plugged the monitor into, once the card was installed, is into the card, and yes we've tried both of the cards outlets.

As to disabling the current driver for the on board graphics chip-set, the hardware driver manager says that there are no proprietary drivers in use on this system and furthermore it doesn't show any available drivers, so installing the card and hooking the monitor to it still results in us getting stuck at the "(initramfs)" prompt.

We are going to try installing the card again and at the [/SIZE][SIZE=1]"(initramfs)" prompt we're going to try typing exit a few times, just to see if we can get past this point. We'll let you know if it works.

Thanks again. Kirby  ](*,)

P.S. if anyone knows how we can force a driver install from the command line in recovery mode, please don't hesitate to suggest it.  [-o<[/SIZE]

---

### Post by pastalavista on 2010-03-12
I've been thinking about your problem, Kir_B, and I remember a similar problem with my ATI graphics back with Feisty or Gutsy, where I had to blacklist the preferred driver so, first find out your driver
```
sudo lshw -C video
```
then blacklist it by editing
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
just add the line 'blacklist 'driver-module-name' (no quotes)

then reboot and see what it does without the driver. if you installed it correctly and it was the right one, it should kick in. It did for my fglrx module. Worth a try? Just comment your added line out or delete it if it doen't work.

---

### Post by Kir_B on 2010-03-12
[SIZE=1]Thanks pastalavista. We're working on that right now. Here's the terminal output of the first command.

stphill@stphill-desktop:~$ sudo lshw -C video
[sudo] password for  stphill: 
  *-display               
       description: VGA  compatible controller
       product: 82845G/GL[Brookdale-G]/GE  Chipset Integrated Graphics Device
       vendor: Intel Corporation
        physical id: 2
       bus info: pci@0000:00:02.0
       version:  03
       width: 32 bits
       clock: 33MHz
        capabilities: pm bus_master cap_list rom
       configuration:  driver=i915 latency=0
       resources: irq:16  memory:d0000000-d7ffffff(prefetchable) memory:dff80000-dfffffff[/SIZE][SIZE=1]


Are we right in assuming that the blacklisted device driver should be the "[/SIZE][SIZE=1]driver=i915[/SIZE][SIZE=1]" [/SIZE][SIZE=1]entry.

Thanks again. Kirby[/SIZE]

---

### Post by pastalavista on 2010-03-12
Yes, and the blacklist.conf entry should be 

blacklist i915

experimentally speaking.. good luck

---

### Post by Kir_B on 2010-03-12
[SIZE=1]> **pastalavista said:**
> Yes, and the blacklist.conf entry should be 

blacklist i915[/SIZE] [SIZE=1]

experimentally speaking.. good luck[/SIZE] [SIZE=1]

Thanks a lot pastalavista. We're giving it a go right now. I'll post the results soon as I can.[/SIZE] [SIZE=1]

Kirby[/SIZE]   [-o<

---

### Post by Kir_B on 2010-03-12
[SIZE=1]A quick question Pastalavista.

After blacklisting the i915 driver, should we go ahead and restart with the new card installed or without.

thanks. Kirby
[/SIZE]

---

### Post by pastalavista on 2010-03-12
> **Kir_B said:**
> [SIZE=1]A quick question Pastalavista.

After blacklisting the i915 driver, should we go ahead and restart with the new card installed or without.

thanks. Kirby
[/SIZE]

Yes, I should have said so. Plug the card in. The driver you installed will probably be useless for the onboard graphics chip.

---

### Post by Kir_B on 2010-03-12
[SIZE=1]The result is basically the same. Just a black screen, then after a Control+Alt, we end up right back at the "(initramfs)" prompt. using the exit command at the (initramfs) prompt gets us this: here are the first three lines: /init: line 259: can't open /root/dev/console: no such file, [  185.782596] Kernel panic - not syncing: Attempted to kill init! and [  185.782674] Pid: 1, comm: init Not tainted 2.6.31-17-generic #54-Ubuntu

Thanks, it was worth the try. Kirby[/SIZE]

---

### Post by pastalavista on 2010-03-12
OK.. you didn't get it installed right. Download these two packages

[URL="https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249/+files/nvidia-71-kernel-source_71.86.08-0ubuntu1_i386.deb"]https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249/+files
/nvidia-71-kernel-source_71.86.08-0ubuntu1_i386.deb[/URL]

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249/+files/nvidia-71-modaliases_71.86.08-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249/+files/nvidia-71-modaliases_71.86.08-0ubuntu1_i386.deb")

Just double-click both to open and install... reboot with the new card and try again. After this, I'd say, get another card :) 

PS - those drivers came from the bottom of this page

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249)

---

### Post by Kir_B on 2010-03-12
> **pastalavista said:**
> OK.. you didn't get it installed right. Download these two packages

[URL="https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249/+files/nvidia-71-kernel-source_71.86.08-0ubuntu1_i386.deb"]https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249/+files
/nvidia-71-kernel-source_71.86.08-0ubuntu1_i386.deb[/URL]

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249/+files/nvidia-71-modaliases_71.86.08-0ubuntu1_i386.deb](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249/+files/nvidia-71-modaliases_71.86.08-0ubuntu1_i386.deb)

Just double-click both to open and install... reboot with the new card and try again. After this, I'd say, get another card :) 

PS - those drivers came from the bottom of this page

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1/+build/855249)


Thanks Pastalavista, we'll give it a go. Does it matter which one first?

Kirby

---

### Post by Kir_B on 2010-03-12
[SIZE=1]We removed the failed attempted driver creation that locked us out of our system and then attempted to install the the first of the driver packages that we're suggested earlier on. No joy!

I'm not positive as to why, but I'll attach a screen shot of the terminal output. Maybe someone can give us a translation.



Thanks everyone. Kirby  
[/SIZE]

---

### Post by Kir_B on 2010-03-12
[SIZE=1]Hey all. I think we've deciphered the result of the failed installation of the aforementioned driver. We apparently need to do either a Make or a build on something else. I guess it's back to school time. We'll get to that after a well deserved nap. :-k

Thanks all. Kirby  #-o
[/SIZE]

---

### Post by Kir_B on 2010-03-12
[SIZE=1]I'm going to post the contents of the make.log document that describes the error. Hopefully while we go for a nap someone can decipher exactly what the next steps are.

[HTML]DKMS make.log for nvidia-71.86.08 for kernel 2.6.31-14-generic (i686)
Fri Mar 12 07:42:16 PST 2010
NVIDIA: calling KBUILD...
make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-14-generic/build  SUBDIRS=/var/lib/dkms/nvidia/71.86.08/build modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (         \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf  are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on  kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /var/lib/dkms/nvidia/71.86.08/build/.tmp_versions ; rm -f  /var/lib/dkms/nvidia/71.86.08/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/71.86.08/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/71.86.08/build/.nv.o.d  -nostdinc  -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude   -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include  include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef  -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common  -Werror-implicit-function-declaration -Wno-format-security  -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3  -freg-struct-return -mpreferred-stack-boundary=2 -march=i586  -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector  -fstack-protector-all -pipe -Wno-sign-compare  -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow  -Wframe-larger-than=1024 -fno-omit-frame-pointer  -fno-optimize-sibling-calls -Wdeclaration-after-statement  -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm  -I/var/lib/dkms/nvidia/71.86.08/build -Wall -Wimplicit -Wreturn-type  -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error  -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE  -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE [/HTML]Thanks and have a nice day. Kirby[/SIZE]

---

