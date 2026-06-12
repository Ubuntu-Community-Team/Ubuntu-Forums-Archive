---
title: "Suspend to RAM not working"
date: 2012-04-30
forum: General Help
---

### Post by schnurrbidurr on 2012-04-30
Yesterday, I upgraded to 12.04 from 11.10, which ran without any problems.

On 12.04 my computer won't sleep (suspend to RAM). When I hit the button  I get the black screen, hear the HD shutdown only for it to awake  immediately after and the system awaking again.
I increased my SWAP partition to 4 GB (I have 2GB RAM), but it's still  not sleeping. Neither will it suspend to disk (I know it's been disabled  by default, but I enabled it in some file by following a tut).
Any help is greatly appreciated.

I'm running Kubuntu 12.04, KDE 4.8.2, kernel 3.2.0-24-generic
AMD Athlon II X2 245, 2.9 GHz, 2 GB RAM

PS: Even trying suspending it manually from the Terminal doesn't work. I also tried stopping the network-manager first, no success.

below is the what the suspend-log said
> /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Apr 30 21:46:01 BST 2012: performing suspend
Mon Apr 30 21:46:09 BST 2012: Awake.
Mon Apr 30 21:46:10 BST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Apr 30 21:46:10 BST 2012: Finished.


---

### Post by schnurrbidurr on 2012-05-04
Anyone?

---

### Post by *M* on 2012-05-04
My problem was one of my USB devices keeping the computer awake, so I made a script file (as root) in /etc/pm/sleep.d with the following:

```
#!/bin/bash
# Disables echi / ohci / uhci ports on suspend and reenables them on resume. 
# Place this script in /etc/pm/sleep.d


function unbind_usb {
    for driver in ehci ohci uhci; do
        cd "/sys/bus/pci/drivers/${driver}_hcd";
        ids=$(ls | grep :);
        echo $ids > /tmp/DISABLED_$driver;
        for id in $ids; do
            echo "Unbinding $id";
            echo -n "$id" > unbind;
            disabled="$disabled $id";
        done;
    done;
}

function bind_usb {
    for driver in ehci ohci uhci; do
        cd "/sys/bus/pci/drivers/${driver}_hcd";
        for id in $(cat /tmp/DISABLED_$driver); do
            echo "Binding $id";
            echo -n "$id" > bind;
        done;
        rm /tmp/DISABLED_$driver;
    done;
}

case "$1" in
    hibernate|suspend)
        unbind_usb;
    ;;
    thaw|resume)
        bind_usb;
        # Uncomment the following two lines if USB devices stutter after resume
        # unbind_usb;
        # bind_usb;
    ;;
    *)
    exit 1;
    ;;
esac;
exit 0;
```

I have to use the power button to wake but sleep works now :)

---

### Post by mcendoo on 2012-05-04
I had a similar problem when I installed 12.04,which I solved in a slightly different manner.  The command "cat /proc/acpi/wakeup' (without the quotes) list all devices which can wake the system. in my case the result was
```
Desktop$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
SMB0	  S4	*disabled  pci:0000:00:03.2
USB0	  S4	*disabled  pci:0000:00:04.0
USB2	  S4	*enabled   pci:0000:00:04.1
US15	  S4	*disabled  pci:0000:00:06.0
US12	  S4	*enabled   pci:0000:00:06.1
NMAC	  S5	*disabled  pci:0000:00:0a.0
PBB0	  S4	*disabled  pci:0000:00:09.0
HDAC	  S4	*disabled  pci:0000:00:08.0
XVR0	  S4	*disabled  pci:0000:00:0c.0
XVR1	  S4	*disabled  
P0P5	  S4	*disabled  
P0P6	  S4	*disabled  pci:0000:00:15.0
P0P7	  S4	*disabled  pci:0000:00:16.0
P0P8	  S4	*disabled  pci:0000:00:17.0
P0P9	  S4	*disabled  pci:0000:00:18.0
PWRB	  S4	*enabled  
```

The four lines starting with US are USB devices.The command 'echo US15 > /proc/acpi/wakeup' will toggle the state of US15.  (this command must be used in a root terminal as redirection does not work with sudo.  Using 'echo US15 | sudo tee /proc/acpi/wakeup' works from a user prompt.)

I disabled just two of the USB devices (USB0 and US15) and was able to suspend and resume.  This settings are not persistent on booting, so I had to add the commands to my rc.local file.

I did find a tool called acpitool in the repositories which allows enabling and disabling the devices.

This worked for me, YMMV :)

---

### Post by jolan on 2012-05-07
> **mcendoo said:**
> I had a similar problem when I installed 12.04,which I solved in a slightly different manner.  The command "cat /proc/acpi/wakeup' (without the quotes) list all devices which can wake the system. in my case the result was
```
Desktop$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
SMB0	  S4	*disabled  pci:0000:00:03.2
USB0	  S4	*disabled  pci:0000:00:04.0
USB2	  S4	*enabled   pci:0000:00:04.1
US15	  S4	*disabled  pci:0000:00:06.0
US12	  S4	*enabled   pci:0000:00:06.1
NMAC	  S5	*disabled  pci:0000:00:0a.0
PBB0	  S4	*disabled  pci:0000:00:09.0
HDAC	  S4	*disabled  pci:0000:00:08.0
XVR0	  S4	*disabled  pci:0000:00:0c.0
XVR1	  S4	*disabled  
P0P5	  S4	*disabled  
P0P6	  S4	*disabled  pci:0000:00:15.0
P0P7	  S4	*disabled  pci:0000:00:16.0
P0P8	  S4	*disabled  pci:0000:00:17.0
P0P9	  S4	*disabled  pci:0000:00:18.0
PWRB	  S4	*enabled  
```

The four lines starting with US are USB devices.The command 'echo US15 > /proc/acpi/wakeup' will toggle the state of US15.  (this command must be used in a root terminal as redirection does not work with sudo.  Using 'echo US15 | sudo tee /proc/acpi/wakeup' works from a user prompt.)

I disabled just two of the USB devices (USB0 and US15) and was able to suspend and resume.  This settings are not persistent on booting, so I had to add the commands to my rc.local file.

I did find a tool called acpitool in the repositories which allows enabling and disabling the devices.

This worked for me, YMMV :)
Thank you so much. This did the trick. I've been looking for solution to this problem for two days...

---

### Post by Olly TH on 2012-05-13
Thank you for the post, mcendoo, because it solved the issue for me. (I am using a desktop with Ubuntu 12.04 and an nVidia graphic card with nouveau.)

I have put your solution in a script that you could install as root, with execute permissions, in "/etc/pm/sleep.d/8_disable_USB.sh". The script disable all USB devices at suspend time. I attach it, as some may find it easy, it makes the fix persistent and easy to install.

---

### Post by mcendoo on 2012-05-14
> **Olly TH said:**
> Thank you for the post, mcendoo, because it solved the issue for me. (I am using a desktop with Ubuntu 12.04 and an nVidia graphic card with nouveau.)

I have put your solution in a script that you could install as root, with execute permissions, in "/etc/pm/sleep.d/8_disable_USB.sh". The script disable all USB devices at suspend time. I attach it, as some may find it easy, it makes the fix persistent and easy to install.

I am not very familiar with regular expressions, but I don't think your script covers all tha USB entries in /proc/acpi/wakeup.  As I understand it, usb entries can be USB0 to USB9, then US11, US12 etc. Your script seems only to look for USB0 to USB9.  In my case I had to disable USB0 and US15 to get suspend to work.  Also, by disabling all the USB entries, will that not preclude waking a system with a USB devise? (In my case this is not an issue as my motherboard has an error on it that shuts the 5v power off on suspend, preventing any USB device waking up the system)

---

### Post by fiikske on 2012-05-20
Hi,

in my case, this is what I get
> 
~$ cat /proc/acpi/wakeup  | grep US
USB1	  S3	*disabled  
USB2	  S3	*disabled  
USB3	  S3	*disabled  
USB4	  S3	*disabled  
USB5	  S3	*disabled  
USB6	  S3	*disabled  
USB7	  S3	*disabled 


so all the usb are disabled. 
Could there be any other cause of my suspend problem? Also, after suspending, my ubuntu does not restart, just stays half suspended: screen on but black. 

Any ideas?
Fiikske

---

### Post by acjohnson on 2012-09-10
Okay, originally I got confused when I ran cat /proc/acpi/wakeup and didn't see any USB devices... Here's what it looked like at first on my new Toshiba L840:
```

Device	S-state	  Status   Sysfs node
P0P1	  S4	*disabled  
GLAN	  S0	*disabled  
EHC1	  S3	*enabled   pci:0000:00:1d.0
EHC2	  S3	*enabled   pci:0000:00:1a.0
XHC	  S3	*enabled   pci:0000:00:14.0
HDEF	  S0	*disabled  pci:0000:00:1b.0
RP01	  S4	*disabled  pci:0000:00:1c.0
PXSX	  S4	*disabled  
RP02	  S4	*disabled  
PXSX	  S4	*disabled  
FRES	  S0	*disabled  
RP03	  S0	*disabled  pci:0000:00:1c.2
PXSX	  S4	*disabled  pci:0000:02:00.0
RP04	  S4	*disabled  pci:0000:00:1c.3
PXSX	  S4	*disabled  pci:0000:03:00.0
RP05	  S4	*disabled  
PXSX	  S4	*disabled  
RP06	  S4	*disabled  
PXSX	  S4	*disabled  
RP07	  S4	*disabled  
PXSX	  S4	*disabled  
RP08	  S4	*disabled  
PXSX	  S4	*disabled  
PEG0	  S4	*disabled  
PEGP	  S4	*disabled  
PEG1	  S4	*disabled  
PEG2	  S4	*disabled  
PEG3	  S4	*disabled  
LID	  S5	*enabled   

```

Even though I don't have any USB devices, the three devices at the top that are listed as enabled are in fact USB. So I just had to disable EHC1, EHC2, and XHC by putting this is my /etc/rc.local file and rebooting:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "EHC1" > /proc/acpi/wakeup
echo "EHC2" > /proc/acpi/wakeup
echo "XHC" > /proc/acpi/wakeup

exit 0

```

...this is the only permanent solution I could find, which isn't very clean in my opinion. If there is a better way to permanently disable these devices then please someone post it!

---

### Post by ironboy on 2012-11-10
Well I don't believe it.

acjohnson you are not only genius, but courteous enough to post this vital piece of information that I've needed for months.

I've never had USB anything in my /proc/acpi/wakeup file, and that whole usbcore.suspend=-1 thing did nothing.

I only have 2 entries now that are enabled.( I still don't know what NECU is but even I am smart enough to know that LID means the laptop screen!!!!), but I don't care, because now I can finally suspend more than once.  It's been driving me batty.

Where on earth is /proc/acpi/wakup getting these values from, and why are the different after reboot than after resume?     

I tried to modify the /sys/devices/pci:0000:00/0000:00:1a.0/power/wakeup file but even with sudo it wouldn't let me change it. 

I was able to change /sys/devices/pci:0000:00/0000:00:1a.0/usb1/power/wakeup from enabled to diabled but that had no effect.  I'm willing to bet the former would've fixed it though had I been able to save the change.

Anyway, thanks a million.

---

### Post by acjohnson on 2012-11-11
> **ironboy said:**
> Well I don't believe it.

acjohnson you are not only genius, but courteous enough to post this vital piece of information that I've needed for months.

I've never had USB anything in my /proc/acpi/wakeup file, and that whole usbcore.suspend=-1 thing did nothing.

I only have 2 entries now that are enabled.( I still don't know what NECU is but even I am smart enough to know that LID means the laptop screen!!!!), but I don't care, because now I can finally suspend more than once.  It's been driving me batty.

Where on earth is /proc/acpi/wakup getting these values from, and why are the different after reboot than after resume?     

I tried to modify the /sys/devices/pci:0000:00/0000:00:1a.0/power/wakeup file but even with sudo it wouldn't let me change it. 

I was able to change /sys/devices/pci:0000:00/0000:00:1a.0/usb1/power/wakeup from enabled to diabled but that had no effect.  I'm willing to bet the former would've fixed it though had I been able to save the change.

Anyway, thanks a million.

That's great, I'm glad I could help someone out. Without the other comments on this thread though, I would not have figured it out. However thanks for growing my head size two sizes larger :P

---

### Post by refle on 2013-04-28
Hi,
I have a similar problem. My acer aspire timeline 3820tg SOMETIMES doesnt wake up from suspend (the screen stays off, although the computer itselfs wakes up), and i cant get the screen to work then. but as i said, most of the time i can wake up, but not always (strange as it is).
Now my cat /proc/acpi/wakeup file is:

[HTML] 
Device    S-state      Status   Sysfs node
P0P1      S4    *disabled  pci:0000:00:1e.0
EHC1      S3    *enabled   pci:0000:00:1d.0      
USB1      S3    *disabled  
USB2      S3    *disabled 
USB3      S3    *disabled  
USB4      S3    *disabled  
EHC2      S3    *enabled   pci:0000:00:1a.0
USB5      S3    *disabled  
USB6      S3    *disabled  
USB7      S3    *disabled  
HDEF      S3    *disabled  pci:0000:00:1b.0
RP01      S5    *disabled  pci:0000:00:1c.0
PXSX      S5    *disabled  pci:0000:03:00.0
GLAN     S5    *disabled 
LID0       S3    *enabled   
SLPB      S3    *enabled   [/HTML]

what do you recommend?
Thank you in advance1

---

### Post by acjohnson on 2013-04-28
What version of ubuntu are you running? Are you running unity or kde? Also, are you running 32 bit or 64 bit ubuntu?

---

### Post by refle on 2013-04-28
Sorry for not giving these infos.
I'm Using Ubuntu 12.04 64bit with Unity3d.

---

### Post by acjohnson on 2013-04-28
I pretty much guarantee if you upgrade to 13.04 64-bit you won't experience these issues any more. A lot of changes have been made to the xserver stack and kernel modules since 12.04. Also, correct me if I'm wrong, but it looks like the timeline 3820tg has an integrated ati graphics chip. Are you able to use the fglrx proprietary driver with that chip or are you using the open source radeon driver that comes with ubuntu?

---

### Post by refle on 2013-04-29
I'm using the proprietary driver... However i don't want to switch to ubuntu 13.04 since i prefer a LTS version (moreover, i have installed a lot of drivers on 12.04 and im afraid they won't be available for 13.04 - or again hard to install). 
do you have any idea what i could do to solve my problem?
Thank you!

---

### Post by acjohnson on 2013-04-29
You could try installing the r-series backport ppa and do a apt-get dist-upgrade and install the linux-lts-raring package: [https://launchpad.net/~ubuntu-x-swat/+archive/r-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/r-lts-backport)
Or if you don't want to change kernel versions you could try the xorg crack pushers ppa instead: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

What do you mean by "i have installed a lot of drivers on 12.04"? What drivers could you be installing on a laptop besides video drivers? Aren't they all built-in to the kernel?

---

### Post by refle on 2013-04-30
its the graphics driver and the printer driver. for both i have followed a very long tutorial on the web... i'm afraid that they wont work with the new version.

can you tell me what the two ppa's are doing?
thank you for your support!

---

### Post by acjohnson on 2013-04-30
I don't have a lot of experience with the fglrx proprietary driver so I'm not sure what to expect, but isn't it included in the repositories?

I suppose the proprietary graphics driver might not work until AMD adds support for 13.04. Right now the release notes for the latest drivers state that 12.10 is supported: [http://support.amd.com/us/kbarticles/Pages/amdcatalyst13-4linreleasenotes.aspx](http://support.amd.com/us/kbarticles/Pages/amdcatalyst13-4linreleasenotes.aspx)

If you install the r-series ppa you will likely loose support for the proprietary graphics driver since the 3.8 Linux kernel is not supported.

The printer driver will most likely work however since printer drivers do not depend on the kernel, and are usually built to support CUPS.

Perhaps your best bet would be to try 12.10 and see how it runs. You could even install it to a USB hard drive just to test it first and see how it goes, or just be patient and wait for support from the proprietary drivers from AMD on 13.04.

You're going to have a much more stable experience if you upgrade to 13.04. The ppa's that I've suggested are unsupported and could possibly cause other problems.

If you want to learn more about the two ppa's that I suggested then click on the link and read the top of the page, or just do a google search and you'll learn just as much as I have :)

Also, your problem isn't really the same issue that others have had on this thread so you might have better luck by posting a new thread that is more specific to the issue that you are experiencing.

---

### Post by refle on 2013-05-01
okay thank you. i wil stay with 12.04 since i need my graphics driver and printer driver as well and don't want to spend another weeks on getting my system to run...

---

### Post by LiveFreeDead on 2013-05-07
> **Olly TH said:**
> Thank you for the post, mcendoo, because it solved the issue for me. (I am using a desktop with Ubuntu 12.04 and an nVidia graphic card with nouveau.)

I have put your solution in a script that you could install as root, with execute permissions, in "/etc/pm/sleep.d/8_disable_USB.sh". The script disable all USB devices at suspend time. I attach it, as some may find it easy, it makes the fix persistent and easy to install.

Thanks for this script attached to your post, it IS the only thing that got my S2R working again. I think my USB WiFi was causing havok with my PC sleeping soundly.:D

I can't believe such a simple fix couldn't be applied to 13.04, if some hardware is keeping the PC awake, it should at least disable that device and it will be re-enabled by the Kernel. It would then repair itself after the first few failiers.

---

### Post by pmontrasio on 2014-03-07
I'm experiencing this problem on a HP ZBook 15 with a fresh install of 12.04. It happens only after I attach an external USB disk. I can suspend until I do that, I can't after then. It resumes after a couple of seconds. It didn't happen on my old HP laptop with 12.04. There is a visible difference between the two laptops: I could power down that external hard with udisks --detach /dev/sdX on the old laptop. That command detaches the disk on the new one, but it doesn't power it down.

Anyway, the workaround is to unbind the USB device and rebind it as in the script. I don't need to run it before suspending and after resuming. It's enough to unbind the device after unmounting the disk and rebinding it right away. If the device is unbound the USB port is dead and won't recognize any other disk.

---

### Post by HobbitTR on 2014-05-11
acjohnson your simple solution worked for me, thank you. 
Previously every time I plugged in a USB drive, suspend would immediately resume. After editing the rc.local file and rebooting everything works great for me.

Running Lenovo IdeaPad Y510P
Card- 1: Intel 4th Gen Core Processor Integrated Graphics Controller 
Card-2: NVIDIA GK107M [GeForce GT 755M]
NOT running NVIDIA drivers and Linux Mint MATE

---

