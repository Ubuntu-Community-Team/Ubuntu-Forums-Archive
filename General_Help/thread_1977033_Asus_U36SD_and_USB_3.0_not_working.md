---
title: "Asus U36SD and USB 3.0 not working"
date: 2012-05-09
forum: General Help
---

### Post by k999 on 2012-05-09
I have an Asus U36SD laptop with Ubuntu 12.04, recently upgraded from 11.10. The USB 3.0 port doesn't work (it works under Windows). Nothing even appears in my dmesg log when I plug in a USB 3.0 external drive.

I followed the instructions on:

[https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD)

and in my /etc/default/grub I have this line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 pci=nomsi,noaer"

```

and I have rebooted (lots of times).

Has anyone else got this working, or know a different workaround?

---

### Post by adrien214 on 2012-05-10
[COLOR="Silver"]I once got the USB 3.0 to work with these parameters, but that's about it, nothing else was working so I removed them and I haven't looked for a solution since.[/COLOR] how do i delete this now?

---

### Post by adrien214 on 2012-05-10
I once got the USB 3.0 to work with these parameters, but that's about it, nothing else was working so I removed them and I haven't looked for a solution since.

---

### Post by k999 on 2012-05-10
I upgraded my BIOS from 205 to 206 (in Windows with the Asus utility) yesterday, and after rebooting to Linux my disk worked on the USB 3.0 port. Not sure whether the upgrade really mattered, however.

I suspended my laptop, and today after waking it, it's not working. USB 3.0 actually shows up with lspci -vvv, the relevant section now looking like this:

```
04:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev ff) (prog-if ff)
        !!! Unknown header type 7f
        Kernel driver in use: xhci_hcd

```

---

### Post by adrien214 on 2012-05-11
Are you using the script meant to fix the suspend issue?

---

### Post by k999 on 2012-05-11
Yes, I've had the script on [https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD) active for quite a while. However, checking this out a bit more closely, I see that it doesn't handle all three of my USB controllers. On my computer things look like this:

```
$ lspci  | grep USB
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
04:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
```

I'll add 0000:04:00.0 to the BUSES list in the script, and see if that helps. 

If I never post here again, it may have worked...;)

---

### Post by k999 on 2012-05-11
That was NOT the right fix. After adding that to the script, my computer never suspended after I close the lid. I had to remove it again and reboot to even get suspend working again. So now suspend works, but not USB 3.0 (after suspend).

---

### Post by k999 on 2012-05-11
I've modified the suspend script, and my new version seems to solve the problem for me. I've only tested suspending a few times, but now it seems to work every time. 

I had to shut down and restart (not reboot) to get USB 3.0 working before this started working, that's the best way I've found to get it up and running when it's not working.

My modification is to change the script under the Suspend section on [https://help.ubuntu.com/community/Asus_U36SD](https://help.ubuntu.com/community/Asus_U36SD) to the following:

```
BUSES="0000:00:1a.0 0000:00:1d.0"
XHCIBUSES="0000:04:00.0"

case "${1}" in
    hibernate|suspend)
        # Switch USB buses off
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        done
        for bus in $XHCIBUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/unbind
        done
        ;;
    resume|thaw)
        # Switch USB buses back on
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
        done
        for bus in $XHCIBUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/bind
        done
        ;;
esac

```

When USB 3.0 wasn't working, the controller either didn't show up in the lspci output at all, or lspci -vvv would show it like this:

```
04:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev ff) (prog-if ff)
        !!! Unknown header type 7f
        Kernel driver in use: xhci_hcd
```

The best fix for this, as mentioned, is to shut down and start up again (not reboot), and then install the script above as described on the Ubuntu on Asus U36SD page.

---

### Post by adrien214 on 2012-05-12
I just tried it live in 12.04 and the USB 3.0 works just fine.

The "unknow header type 7f" seems to indicate the port is not enabled, at least that's how my nvidia adapter is shown when running lspci and the card is off. If you have an external hdd with extra powering (an extra USB to plug into the USB 2.0 to power up the external device), you might wanna first plug the energy USB, wiat ten seconds, then plug in the USB 3.0, that's the only way it works for me.

---

### Post by k999 on 2012-05-12
I don't think mine was a power issue. As mentioned, if I rebooted after it showed "unknown header type 7f", it didn't show up at all in lspci before I shut down and started up again. And I tried quite a lot of times, sometimes waiting a while before giving up.

My disk doesn't have an extra power connector, so I can't try that approach. But it seems to work when I enable/disable with the script I mentioned, so power doesn't appear to be the issue.

---

