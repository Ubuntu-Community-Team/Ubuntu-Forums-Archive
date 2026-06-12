---
title: "Ubuntu won't boot every second time"
date: 2011-05-07
forum: General Help
---

### Post by vangop on 2011-05-07
Hi!
After upgrading to 11.04 I've started to experience the following:
upon selecting a grub entry from the list ubuntu starts ok only every second time. On other occasions it won't boot without any error messages on screen or in syslog. I have to ctrl+alt+del to reboot and then it starts fine.
This happens strictly every other time.
Can anybody suggest on this?

---

### Post by dino99 on 2011-05-07
same issue on my system: first boot fail most of the time, reboot never work. Its a known issue since ages for some chipsets/configs, and not fixed yet (mostly a acpi trouble, i've added acpi=nobios and it help a litlle)

---

### Post by vangop on 2011-05-07
But it was totally fine on 10.10, started only after upgrade. Do you experience it on all versions?

---

### Post by Rubi1200 on 2011-05-07
Hi,
please post the full specifications for the computer, especially graphics card.

Thanks.

---

### Post by vangop on 2011-05-07
This is hp 8440p laptop, ubuntu 11.04 x64
The system is dualboot with win7
$ [lshw]("http://pastebin.com/1qUrz2sc")
$ [cat /etc/default/grub]("http://pastebin.com/xrFhE2PN")
[BootDmesg]("http://pastebin.com/zemTEnmM")
$ [lspci -v]("http://pastebin.com/u62i7Rrt")

plz let me know if I should post anything else.
Ubuntu is in lvm partitions, which are created in cryptsetup volume.
```
$ mount
/dev/mapper/vg1-root on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda3 on /boot type ext4 (rw,commit=0)
/dev/mapper/vg1-data on /mnt/wind type ext4 (rw,commit=0)
/dev/mapper/vg1-home on /home type ext4 (rw,commit=0)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/akm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=akama)

```

---

### Post by Rubi1200 on 2011-05-07
I'm wondering if this is a graphics issue. I see you have modified the grub file to add nomodeset as a boot parameter.

Perhaps, as a result of the upgrade you need to reconfigure the graphics.

So, let's try this either from a root prompt in recovery mode or a tty in normal mode:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by vangop on 2011-05-08
Hi,
Tried, but this didn't seem to help :(

---

### Post by Rubi1200 on 2011-05-08
Hi,

okay, next thing to look at is the boot info script. Perhaps it will give us some clues.

So, from either the Ubuntu install or a LiveCD, post the results of the boot script. There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by antu456 on 2011-05-09
I have this problem too on my computer and my laptop since i've updated to Natty. Both my computer and my laptop are encrypted using lvm2 and cryptsetup (i've used this tutorial: [http://wiki.ubuntuusers.de/system_verschl%C3%BCsseln](http://wiki.ubuntuusers.de/system_verschl%C3%BCsseln) (german)). Another user in a german Ubuntu forum also has this problem since the update, and his system is also encrypted. So I'm guessing it maybe has to do with the encryption/lvm?

I don't think this is a graphics issue because the system freezes right after I select Ubuntu in the GRUB menu. The screens becomes purple and then the system does not react anymore to keyboard input. There is no splash screen/loading screen, just everything is purple. ;) 
Then I press the reset button on my computer and select Ubuntu again in the GRUB menu, and it boots without any problems. I've looked in /var/log/messages but there are no messages for the first boot (looks like Linux doesn't even get started, so I think it has nothing to do with graphics).

@Rubi: I will try your script later/tomorrow and post the results here if I find the time. :)

---

### Post by vangop on 2011-05-09
Ok, here's the results.
1st: this is without opening the crypted volume.[click]("http://pastebin.com/sExnLjri")

2nd: this is after cryptsetup luksOpen [click]("http://pastebin.com/YXtcpEkH")

---

### Post by vangop on 2011-05-09
antu456, same symptoms here.
One more thing, during the shutdown it prints on the screen some info like what it does and status: 
```
killing processes      [ok]
crypt something      [failed]
```
I wasn't able to find anything like this in the logs afterwards so I ignored it..

---

### Post by Rubi1200 on 2011-05-10
Okay, vangop and antu456; here is something you could both consider trying as a one-off solution (only good for the current boot).

When the computer starts and you see the entry for Ubuntu highlighted press "e" to edit. Navigate using the arrow keys to the line that ends with quiet splash (or similar).

Type the following after quiet splash, rootdelay=90 so the line looks like this:

> quiet splash rootdelay=90

Notice the space after splash and before the next parameter. Then "Ctrl" + "x" to continue booting.

If this works, we can make it more permanent.

---

### Post by vangop on 2011-05-10
> **Rubi1200 said:**
> Okay, vangop and antu456; here is something you could both consider trying as a one-off solution (only good for the current boot).


Thanks for suggestion, but didn't help me.

---

### Post by Rubi1200 on 2011-05-10
Since I have not been able to find anything specific about this issue, I suggest you file a bug report and see if anything comes of it.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I did find some information which *may* have to do with this on a 10.10 install, but both you and antu456 appear to be experiencing this after an upgrade and I assume everything was okay before that.

I will try and keep looking for information, but meantime I suggest you start a bug report on Launchpad.

Feel free to PM me with a link to the report after filing it.

Sorry I don't have more to tell you right now.

---

### Post by svenakela on 2011-05-13
Hi all,

I have a new system (brand new hardware and fresh install) and I experience the same thing.
I cannot see a pattern, it happens *somewhere* in the boot phase. I first suspected a faulty mount point but that was not the case, usually it stops after Apparmor and then there's silence.
Hard reset and reboot always boot up normally, next boot will of course fail...

If I find anything I'll post it here.

---

### Post by svenakela on 2011-05-14
Ok, I think I found the problem on my machine. I removed the prop. Nvidia driver and rebooted. All went fine. I reinstalled the prop. driver and rebooted. All went fine...

I reminded myself I had a similar problem on another workstation with the same driver, it was lost every time I did a system upgrade. The new machine works perfect now after the reinstall.

Hope it helps.

Regards,
Sven

---

### Post by svenakela on 2011-05-19
Ok, this is what I came up with finally. After every update or install of software the boot failed and I had to reinstall the driver, and to get to the bottom of the problem I did the four steps in the first reply of this thread:
[http://askubuntu.com/questions/4954/how-to-get-nvidia-geforce-gt-210-drivers-working-on-lucid-lynx](http://askubuntu.com/questions/4954/how-to-get-nvidia-geforce-gt-210-drivers-working-on-lucid-lynx)

[LIST=1]
[*]apt-get --purge remove xserver-xorg-video-nouveau
[*]Edit /etc/default/grub and add the line GRUB_CMDLINE_LINUX="nouveau.modeset=0"
[*]sudo update-grub
[*]Reboot
[/LIST]
After that, you should be able to install NVIDIA drivers without conflicts with Nouveau.

Now it seems that my Nvidia driver keeps stable and I have no single reboot fail since.

For your information, my machine is fitted with a Geforce 210 card (1GB RAM) and I'm running Ubuntu 11.04.


EDIT: Turned out that the real problem is X that failed loading the driver. This was found in the X log. I recreated the X-server settings with the nvidia-xconfig command and violá everything's running smooth.

---

### Post by vangop on 2011-06-01
> **svenakela said:**
> 

[LIST=1]
[*]apt-get --purge remove xserver-xorg-video-nouveau
[*]Edit /etc/default/grub and add the line GRUB_CMDLINE_LINUX="nouveau.modeset=0"
[*]sudo update-grub
[*]Reboot
[/LIST]
After that, you should be able to install NVIDIA drivers without conflicts with Nouveau.


Hi!
I followed the steps, but right after the reboot I had the issue (had to reset). So it didn't seem to help, maybe I'm not fully following?
```
$ sudo dpkg -l |grep -i nouveau
[sudo] password for akm: 
rc  libdrm-nouveau1                           2.4.22-2ubuntu1                            Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a                          2.4.23-1ubuntu6                            Userspace interface to nouveau-specific kernel DRM services -- runtime

```
```
$ sudo dpkg -l |grep -i nvidi
ii  nvidia-common                             0.2.30                                     Find obsolete NVIDIA drivers
ii  nvidia-current                            270.41.06-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           270.41.03-0ubuntu1~xup~maverick            Tool of configuring the NVIDIA graphics driver

```
Also I noticed that my nvidia drv are installed but not used, do you know if that's related?
[IMG]http://i22.fastpic.ru/big/2011/0601/0f/f6259f216d33166f2cc5c9e36187a90f.jpeg[/IMG]

---

### Post by svenakela on 2011-06-07
It came back for me. The problem was randomly showing up, there's no indication what the reason is but I've got "Cannot find monitor" errors in the X log every time it happened.
So my theory is that something is starting up before depending stuff is ready, hardware or software. Reboot from scratch caused the problem, hot reboot did not. Is the init of the graphics card too slow maybe? 
What I did recently was to add a sleep in the grub.cfg file:

```

...
export linux_gfx_mode
sleep 5
if [ "$linux_gfx_mode" != "text" ]; then ...

```

Well, ugly as grandma. The error hasn't been back though.

---

### Post by svenakela on 2011-06-13
Finally had them time and I went to the bottom with this to find out what was going on.
The apt-available driver is not working properly, and after a manual reinstall (not apt) everything is running fine again without ugly delays etc. Download the driver from Nvidia's site, execute it in a text console. 

I'm not sure it's needed, but I disabled Nouveau as well
```
echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
```

I've been shutting the computer down every day since and no problem at all.

---

### Post by vangop on 2011-06-14
I'm not sure if I have the same cause as you. I have restored a backup of / which had 10.10 system and an older kernel. I have a separate /boot so it still contained 11.04 2.66.38-8 vmlinuz and initrd.
In this case kernel is not able to find any modules (including nvidia), and still I had this issue reproduced when booting from this 11.04 kernel!
After bringing /boot to 10.10 the problem is gone. I think it is about 11.04 initrd or kernel in my case.
I also noticed that when booting from a sysresccd and opening my crypted drive I received messages like "device busy ioc... something".
Although it was properly opened. My thought is that something is wrong in 11.04 which prevents it from properly shutting down crypted volumes and they appear "busy" after reboot, causing something to break during the grub sequence.

---

### Post by svenakela on 2011-06-15
I do have 11.04, try a manual install of the driver. Download the package directly from nvidia and install as described. 
I did it all in a runlevel without X, and it all went fine.

---

### Post by Ross Gayler on 2011-06-17
I have exactly the same problem on an HP EliteBook8540w with an encrypted disk.  Everything was working fine on 10.10.  I upgraded to 11.04 and got the "first boot fails" problem.  I will try replacing the Nvidia driver later today.  I the mean time - I got two other problems when I upgraded.  I thought they were unconnected, but now I don't know:

(1)  When the system is up and running (in Unity) I randomly get a red screen.  Pressing the <super> key (Windows logo) gets the display back OK.  Do you think the problems are related?  It would seem possible if the cause was a broken Nvidia driver.

(2) The system randomly loses power.  This isn't a proper shut-down.  The laptop just goes "clunk" and all the lights are off.  This sounds less related to a broken Nvida driver, but maybe the driver talks to the power management driver and persuades it to kill the power.  Any suggestions?

Also - did anybody raise this "every second boot" issue as a bug?  It would be nice for it not to re-appear every upgrade.

---

### Post by wildmanne39 on 2011-06-17
> **Ross Gayler said:**
> I have exactly the same problem on an HP EliteBook8540w with an encrypted disk.  Everything was working fine on 10.10.  I upgraded to 11.04 and got the "first boot fails" problem.  I will try replacing the Nvidia driver later today.  I the mean time - I got two other problems when I upgraded.  I thought they were unconnected, but now I don't know:

(1)  When the system is up and running (in Unity) I randomly get a red screen.  Pressing the <super> key (Windows logo) gets the display back OK.  Do you think the problems are related?  It would seem possible if the cause was a broken Nvidia driver.

(2) The system randomly loses power.  This isn't a proper shut-down.  The laptop just goes "clunk" and all the lights are off.  This sounds less related to a broken Nvida driver, but maybe the driver talks to the power management driver and persuades it to kill the power.  Any suggestions?

Also - did anybody raise this "every second boot" issue as a bug?  It would be nice for it not to re-appear every upgrade.
Hi, the issue of your system just going blank if that is when you are not using it, it probably is from the screensaver settings and power management settings, you can go into screensaver and the setting are there for both and set screensaver and power management to not let the screen saver come on and do not power down your system.

---

### Post by Ross Gayler on 2011-06-17
Hi Wildmanne39,

>  the issue of your system just going blank if that is when you are not  using it, it probably is from the screensaver settings and power  management settings
I started separate threads for the red screen  and power-off issues and should have included the links: [http://ubuntuforums.org/showthread.php?t=1785117](http://ubuntuforums.org/showthread.php?t=1785117)
[http://ubuntuforums.org/showthread.php?t=1785133](http://ubuntuforums.org/showthread.php?t=1785133)

I think it's unlikely that these are due to screen-saver and power management settings.
They occur when I am busy using the system.
The screen goes to uniform red, not my selected screen-saver.
The red screen does not go away when I type or move the mouse (only when I hit <super>).
There is no sign of suspend or hibernate activity when I lose power - the system goes instantaneously from running normally to completely dead and you can hear a clunk somewhere (like a relay tripping).

---

### Post by Ross Gayler on 2011-06-17
Antu456 wrote:
> I don't think this is a graphics issue because the system freezes right  after I select Ubuntu in the GRUB menu. The screens becomes purple and  then the system does not react anymore to keyboard input. There is no  splash screen/loading screen, just everything is purple. :wink: 
Then I press the reset button on my computer and select Ubuntu again in  the GRUB menu, and it boots without any problems. I've looked in  /var/log/messages but there are no messages for the first boot (looks  like Linux doesn't even get started, so I think it has nothing to do  with graphics).and vangop wrote:
> One more thing, during the shutdown it prints on the screen some info like what it does and status: 
     Code:
     killing processes      [ok] crypt something      [failed] 
My symptoms are exactly the same.  When the boot does not hang it goes from selecting Ubuntu in Grub to the purple screen antu456 describes with a Ubuntu logo, 4 progress dots and a prompt for the encrypted disk password.  So when it hangs, it does so before being able to prompt for the encrypted disk password.  Given that there is an encryption related failure message at shutdown, vangop's suggestion that the encrypted drive is somehow busy seems plausible.

Is there some way to capture the shutdown messages?  I can't find them in /var/log.  It goes past so fast on the screen that all I can catch is "early crypt" and "failure".

---

### Post by wildmanne39 on 2011-06-17
> **Ross Gayler said:**
> Antu456 wrote:
and vangop wrote:
My symptoms are exactly the same.  When the boot does not hang it goes from selecting Ubuntu in Grub to the purple screen antu456 describes with a Ubuntu logo, 4 progress dots and a prompt for the encrypted disk password.  So when it hangs, it does so before being able to prompt for the encrypted disk password.  Given that there is an encryption related failure message at shutdown, vangop's suggestion that the encrypted drive is somehow busy seems plausible.

Is there some way to capture the shutdown messages?  I can't find them in /var/log.  It goes past so fast on the screen that all I can catch is "early crypt" and "failure".
Hi, it is very possible that it is video driver related on the starting issue, a long time ago I had that problem and if ubuntu does not boot the first time it tries to find a way for it to boot the second time and that is why you get to boot at all because it works out a work around. In my case it was my video card driver. Why don't you post the outcome of this command and maybe someone can help figure it out.
```
sudo lshw
```  post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Ross Gayler on 2011-06-17
Update on the encrypted disk failure message at shutdown.  That appears to probably be normal (see this Debian bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=600922](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=600922))
> can you elaborate on which crypto disk fails to stop? if it's the home partition, then there indeed is a bug. but if it's the root partition, this is intended behaviour. it's technically impossible to stop the encrypted device holding the root partition, as the root partition needs to be unmounted first, and the cryptsetup binary needed for 'cryptsetup luksClose' is stored on the root filesystem.svenakela and wildmanne39 are suggesting the problem is with the nvidia video driver.  I have included the lshw output below (as wildmanne39 suggested) and in the meantime I will try installing the nvidia driver from the nvidia site (not the apt version) as svenakela suggested.

```
ubuntu
    description: Notebook
    product: HP EliteBook 8540w (WP390PA#ABG)
    vendor: Hewlett-Packard
    serial: ### RG deleted this ###
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=WP390PA#ABG uuid=BECF534B-0DF4-DE11-81D0-B9F76E39301F
  *-core
       description: Motherboard
       product: 1521
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 32.2E
       serial: ### RG deleted this ###
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: d
          version: 68CVD Ver. F.08
          date: 04/28/2010
          size: 64KiB
          capacity: 3008KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
          slot: CPU 1
          size: 933MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 3
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273CH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 75023050
             slot: Bottom-Slot 1(left)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 9905428-012.A00LF
             vendor: Kingston
             physical id: 1
             serial: 6D07916D
             slot: Bottom-Slot 2(right)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 9905428-012.A00LF
             vendor: Kingston
             physical id: 2
             serial: 6D079F6D
             slot: Bottom-Slot 2(right)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 9905428-012.A00LF
             vendor: Kingston
             physical id: 3
             serial: 6C07986D
             slot: Bottom-Slot 1(left)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:5000(size=4096) memory:d2000000-d30fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT215 [Quadro FX 1800M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:d3080000-d30fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:d3000000-d3003fff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:d7524000-d752400f
        *-communication:1
             description: Serial controller
             product: 5 Series/3400 Series Chipset KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:6050(size=8) memory:d752b000-d752bfff
        *-network
             description: Ethernet interface
             product: 82577LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 06
             serial: 88:ae:1d:a8:bb:30
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.12-3 ip=192.168.0.207 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:45 memory:d7500000-d751ffff memory:d752a000-d752afff ioport:6020(size=32)
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d7529000-d75293ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:56 memory:d7520000-d7523fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:d7400000-d74fffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=8192) memory:d3400000-d73fffff ioport:d7700000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:d3300000-d33fffff
           *-network
                description: Wireless interface
                product: Centrino Ultimate-N 6300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:44:00.0
                logical name: wlan0
                version: 35
                serial: 00:24:d7:39:43:84
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=9.221.4.1 build 25532 ip=192.168.0.221 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:47 memory:d3300000-d3301fff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:d3200000-d32fffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:45:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:d3200000-d3201fff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:d7528000-d75283ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:d3100000-d31fffff ioport:d8000000(size=67108864)
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:46:06.0
                version: 06
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:20 memory:d3101000-d31017ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:46:06.1
                version: 25
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:22 memory:d3105000-d31050ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:46:06.2
                version: 14
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=0
                resources: memory:d3103000-d31030ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:46:06.3
                version: 14
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:22 memory:d3102000-d31020ff
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 6.4
                bus info: pci@0000:46:06.4
                version: bb
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b04a47460-b04a4745f irq:22 memory:d3100000-d3100fff ioport:2000(size=256) ioport:2400(size=256) memory:d8000000-dbffffff memory:dc000000-dfffffff
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:6048(size=8) ioport:605c(size=4) ioport:6040(size=8) ioport:6058(size=4) ioport:6000(size=32) memory:d7527000-d75277ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS72505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PC4O
                serial: 100610PCK404VLJ6LZPJ
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2e41577f
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 1ec6db72-2ce6-9c4f-b3e9-637426334323
                   size: 298MiB
                   capacity: 300MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-04-08 11:19:12 filesystem=ntfs label=SYSTEM state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: ac0a06fa-6541-3a45-b1d7-7a1da2c50067
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-04-08 09:55:48 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: ba2a13a3-3b3f-a845-aaee-ba889658c9a7
                   size: 14GiB
                   capacity: 15GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-04-08 11:19:41 filesystem=ntfs label=HP_RECOVERY state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 373GiB
                   capacity: 373GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /boot
                      capacity: 382MiB
                      configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 373GiB
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633N
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0300
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=i7core_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:ff:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:ff:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:ff:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:ff:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:ff:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:ff:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:ff:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:ff:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:ff:05.3
          version: 04
          width: 32 bits
          clock: 33MHz
  *-battery
       product: AV08068
       vendor: 31LGLGC
       physical id: 1
       slot: Primary
       capacity: 4720mWh
       configuration: voltage=14.4V
```

---

### Post by svenakela on 2011-06-19
You can also try this howto, which should do the same thing: [http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04](http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04)

Except that I downloaded the latest package and installed it.

---

### Post by Ross Gayler on 2011-10-19
FWIW I just put up with the behaviour and now that I have upgraded Ubuntu from 11.04 to 11.10 the problem has gone away.

I don't know that that counts as a fix, more like walking away from your problems, but - hey - it works.

---

### Post by vangop on 2011-10-20
Confirmed, I was on 10.10 down from 11.04 because of this one, and decided to go for 11.10. The boot is ok, although on shutdown I see 
```
Stopping early cryptodisks       [fail]
```

---

