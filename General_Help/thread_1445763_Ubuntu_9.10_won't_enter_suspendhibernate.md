---
title: "Ubuntu 9.10 won't enter suspend/hibernate"
date: 2010-04-03
forum: General Help
---

### Post by om06zr on 2010-04-03
Greetings forum-goers. I have been trying to get my new (custom built) computer to suspend and hibernate without success. Whenever I tell it to suspend or hibernate the screen goes black, almost as if it were working, but immediately returns to a login screen. The power never turns off. I have successfully been able to suspend under windows vista, so it would seem that hardware is certainly capable. But I cannot replicate this under an installed or live-cd version of ubuntu.

I am using ubuntu 9.10 64 bit, a core i7 920, and a gigabyte X58A-UD3R motherboard.

It would seem that the computer supports suspend and hibernate:
```
$ cat /sys/power/state
mem disk
```But after running
```
$ sudo pm-suspend
```unsuccessfully, the log file shows
```
$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Sat Apr  3 15:45:36 EST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux zeus 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
xhci                   40772  0 
x_tables               25832  1 ip_tables
lp                     11908  0 
psmouse                57124  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
nvidia              10316904  56 
serio_raw               6596  0 
joydev                 13088  0 
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
ohci1394               33780  0 
usbhid                 43968  0 
ieee1394              100896  1 ohci1394
r8169                  38884  0 
mii                     6368  1 r8169
floppy                 65192  0 
             total       used       free     shared    buffers     cached
Mem:       6124104    1838148    4285956          0      44244     237876
-/+ buffers/cache:    1556028    4568076
Swap:      8980292          0    8980292
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Sat Apr  3 15:45:37 EST 2010: performing suspend
Sat Apr  3 15:45:38 EST 2010: Awake.
Sat Apr  3 15:45:38 EST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Sat Apr  3 15:45:38 EST 2010: Finished.

```So I installed uswsusp and tried running s2ram
```
$ sudo s2ram
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Gigabyte Technology Co., Ltd."
    sys_product  = "X58A-UD3R"
    sys_version  = " "
    bios_version = "F1"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.
```forcing it gives
```
$ sudo s2ram --force
Switching from vt1 to vt1
[  739.651149] pm_op(): usb_dev_suspend+0x0/0x10 returns -2
[  739.651151] PM: Device usb9 failed to suspend: error -2
[  739.651154] PM: some devices failed to suspend
s2ram_do: No such file or directory
switching back to vt1
```but running lsusb shows nothing on usb9:
```
$ lsusb
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```I thought it was about time I asked for help. Does anyone have any ideas how I could fix this problem? Thanks!

**Solved (sort of):** The USB port causing the problem was USB version 3. Turning the USB3 controller off in the BIOS alleviated the problem. But it's only really a temporary solution.

---

### Post by TheNerdAL on 2010-04-03
Try ```
apmsleep
```

---

### Post by om06zr on 2010-04-03
```
$ sudo apmsleep +00:01
apmsleep: Your kernel does not support APM.
apmsleep: Recompile kernel with APM and /dev/rtc support
```

---

### Post by TheNerdAL on 2010-04-03
Hmm...How about ```
sudo /etc/acpi/sleep.sh
```

---

### Post by om06zr on 2010-04-03
```
$ sudo /etc/acpi/sleep.sh
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
```

---

### Post by TheNerdAL on 2010-04-03
Then I have no idea, sorry.

---

### Post by om06zr on 2010-04-03
Thanks anyway!

---

### Post by TheNerdAL on 2010-04-03
Anytime.

---

### Post by ipsi on 2010-04-03
I have the exact same problem as you, and have managed to solve it by turning off *all* USB devices in the BIOS.

I'm running an Asus N61J laptop with a Core i7 720M.

Next task is to figure out how, if at all, I can disable the particular USB component that is causing me problems without removing my ability to use a USB mouse/keyboard...

---

### Post by om06zr on 2010-04-07
AHA! It seems that the troublesome usb port was USB3. 

```
$lsusb -v
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12

...
```(the "bcdUSB               3.00" part). By disabling the USB3 controller in the BIOS I am now able to suspend and resume. Although now I don't get to use those ports. I guess linux doesn't have great support for USB3 yet?

**Clarification:** By USB3 I mean USB version 3

---

### Post by nuage6 on 2010-04-13
On my HP 8540w I have created the following script 

/etc/pm/sleep.d/05_xhci

The content of this file is
```
#!/bin/sh
# Fix some issues with USB3

if [ "$1" = "suspend" ]
then
        modprobe -r xhci
fi

if [ "$1" = "resume" ]
then
        modprobe xhci
fi

```

chmod 755 /etc/pm/sleep.d/05_xhci

And now I can use my USB3 devices and go in suspend mode.
(Perhaps you need to change the script to hibernate)

Note that I use Lucid, version 10.4 beta 2
Perhaps you'll need to store this file on a folder called suspend.d
Thank you for the tips helping me to understand the issue.

Regards
Gab

---

### Post by nohorbee on 2010-04-25
Hi all,
I have the exact same problem that you are reporting. I have followed this thread and I got the same results when tried the commands you suggested. But when i checked the USB configuration, it results i have usb2 instead of usb3. Regardless, I would prefer not to disable usb ports.
It is not the first time installing ubuntu 9.10 on this machine, and previous times, I hadn't this problem. A curiosity, maybe, I didn't remove the previous installation yet (on which suspend was working fine), and now started to fail on that partition too (that is weird, I know).

Any Idea? Thanks in advance!
(sorry for my poor english, from Argentina ;) )

---

### Post by freem4n on 2010-05-19
Hi,
it seems, that I have the same or similir problem.
I am runnig Ubuntu 10.04 on Acer Aspire 9303.

When I try to suspend (either with pm or s2ram) it starts suspending process and then instead of powering off it returns to the system.

In logs I can find messages, that "Device usb1 failed to suspend".

lsusb output:
```
Bus 002 Device 004: ID 04b4:0033 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I have tried sudo modprobe -r xhci before suspending but it doesn't help. I have also tried modprobe -r usbhid hid, but that doesn't help either.

lsusb -v doesn't show any usb3 device.

Suspend and hibernate worked just fine before upgrade to 10.04.
Hibernate works now, but I dont use it much. I would prefer to use suspend.

I would appreciate any idea, which might lead to solving this issue. Thanks.

---

### Post by freem4n on 2010-05-19
It seems that I have found a solution for me (well it's more a workaround than a solution, but suspends works fine now).

I understood from _[this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515109")_, that problem was in my web camera, which is using gspca_m5602 driver.

What I had to do was create a simple script:
```
#!/bin/bash
echo disabled >/sys/bus/usb/devices/.../power/wakeup
# (instead of "..." put usb device which is causing you problems.
# You can find more info in the bug report linked above. For me it was "usb1".)
```
and put it into /etc/pm/sleep.d/ directory. Don't forget to "chmod 755 your_script_name".

Thats all! Now suspend works fine for me! I guess that for hibernate u can do the same.

Hope this will help to someone.

---

### Post by rmcd on 2010-06-04
I wanted to mention that the suggestion of nuage6 didn't work for me (I'm running 9.10). But using this script (which I installed in /usr/local/sbin) did work:

#!/bin/sh
modprobe -r xhci
pm-suspend
modprobe xhci

Thanks to all who contributed to this thread! Great help.

---

### Post by arkobose on 2010-06-04
> **rmcd said:**
> I wanted to mention that the suggestion of nuage6 didn't work for me (I'm running 9.10). But using this script (which I installed in /usr/local/sbin) did work:

#!/bin/sh
modprobe -r xhci
pm-suspend
modprobe xhci

Thanks to all who contributed to this thread! Great help.
How do I install the above script? I mean, do I put the above code in a text file and then save it in /usr/local/sbin? Should the file have a special name and a particular format? 
I am new to Linux, and would really appreciate the help. Thanks!

---

### Post by rmcd on 2010-06-04
You pretty much have it right. You create a file containing the commands I posted. I named it "mysleep.sh" because there is already a "sleep" command. Then do the following
```

sudo chmod +x mysleep.sh
sudo cp mysleep.sh /usr/local/sbin

```
To explain: The first line makes the file executable. Executing the commands in the file requires that you have root privileges. You cannot execute a script in an "sbin" directory unless you become root or execute by prefacing with sudo. It goes in /usr/local/sbin because it's provided by you (local), not part of the standard installation.

Then you run the command as 
```
sudo mysleep.sh
```
If I've botched the explanation, I'm sure someone will jump in and clarify.

---

### Post by MadEgg on 2010-06-17
Same problem here. Disabling USB3 does the trick on my Gigabyte X58A-UD3R mainboard. But the approach you are taking for unloading the module before suspending is more of a workaround then necessary. Suspending has the right tools for this.

I implemented it like this. Put the following code (as root) into 

/etc/pm/sleep.d/05_disable_usb3
```

#!/bin/bash

## Unload USB 3 module before sleep

case "$1" in
    suspend)
        /sbin/modprobe -r xhci
        ;;
    hibernate)
        /sbin/modprobe -r xhci
        ;;
    thaw)
        /sbin/modprobe xhci
        ;;
    resume)
        /sbin/modprobe xhci
        ;;
esac
```

After saving this, make it executable:

```
chmod ugo+x /etc/pm/sleep.d/05_disable_usb3
```

Now, when suspending, the script is passed suspend, and while resuming the scripts is passed resume, so it always performs the correct action.

Works great here. But I'm afraid that it will give difficulties when the driver is in use, for example, when an external HDD is connected using USB3. Hopefully the driver will have improved by the time I get me one.

Has anyone filed a bug report about the XHCI driver (maybe in combination with the NEC chip?) yet?

---

### Post by Pedram Veisi on 2010-08-09
I'm using ubuntu 10.04, Core i7 860 on P55-USB3 motherboard and I had the same problem.Disabling onboard USB3 solved it.

Thanks.

---

### Post by sorens on 2010-09-11
Wow, you guys rock. This worked for my motherboard: Gigabyte GA-790XTA-UD4. I used the script supplied by nuage06.

---

### Post by mojotexas on 2010-09-15
the mysleep.sh solution worked for me to be able to Sleep my computer. 

That is, I have a file with these lines:
```
#!/bin/sh
modprobe -r xhci
pm-suspend
modprobe xhci


```

and if I ```
sudo mysleep.sh
``` in the terminal, then my computer does go to sleep. 

That's great, but how can I get it to work so that when I press the suspend button, or Ctrl+alt+del SUSPEND, it runs that command?
Any ideas for incorporating this into the regular controls?

---

### Post by teeedubb on 2011-03-02
Thanks nuage6, your script solved my suspend issues.

The problem was the Asus U3S6 sata usb3 card and Im running ubuntu 10.04.2. Disabling the xhci drivers doesnt affect the sata portion of the card either.

Thanks again!

---

### Post by NertSkull on 2011-08-20
> **MadEgg said:**
> Same problem here. Disabling USB3 does the trick on my Gigabyte X58A-UD3R mainboard. But the approach you are taking for unloading the module before suspending is more of a workaround then necessary. Suspending has the right tools for this.

I implemented it like this. Put the following code (as root) into 

/etc/pm/sleep.d/05_disable_usb3
```

#!/bin/bash

## Unload USB 3 module before sleep

case "$1" in
    suspend)
        /sbin/modprobe -r xhci
        ;;
    hibernate)
        /sbin/modprobe -r xhci
        ;;
    thaw)
        /sbin/modprobe xhci
        ;;
    resume)
        /sbin/modprobe xhci
        ;;
esac
```

After saving this, make it executable:

```
chmod ugo+x /etc/pm/sleep.d/05_disable_usb3
```

Now, when suspending, the script is passed suspend, and while resuming the scripts is passed resume, so it always performs the correct action.


I know this thread is a year old.  And I believe the problem has been fixed for more recent releases.  But I'm still on 10.04 (LTS) and finally got suspend working due to this.

But I wanted to update it.  The above works for me.  But the xhci module has been renamed to xhci_hcd

So I used the above script, but substituted "xhci" for "xhci_hcd" and it works for me.

So maybe others that are still on the old LTS this will work for them also.

---

### Post by joytree on 2011-09-24
thanks for this thread. But it still doesn't work out for me though I tried the script

For Hibernate or Suspend, my laptop just turns to black screen but is still running and what's worse is I cannot get it back.. it remains the black screen though I push the power botton..

any idea? thanks

---

### Post by rmcd on 2011-09-24
For me, this tip helped greatly in 10.04. Edit the boot command line (in /etc/default/grub, if you're using grub2) to add "nomodeset":

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

Then run sudo update-grub, and reboot.

---

