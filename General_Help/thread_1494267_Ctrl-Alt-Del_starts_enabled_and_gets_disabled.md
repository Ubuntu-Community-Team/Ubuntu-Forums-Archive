---
title: "Ctrl-Alt-Del starts enabled and gets disabled"
date: 2010-05-26
forum: General Help
---

### Post by HotForLinux on 2010-05-26
I had been asking how to enable Ctrl-Alt-Del to call the gnome Logout/Poweroff   [IMG]http://png-images.findicons.com/files/icons/2176/lynx_black/22/gnome_logout.png[/IMG]   or whatever is the hidden name of the program to logout from the GUI in a Hardy system.

Today I discovered that once logged in the GUI, it stared enabled but,  after three or four succesive calls (or a certain amount of time), it became disabled. Can anyone help?

I don't know whether the ouput of dmesg and syslog give a clue. There's a strange interrupt.

```
**$ dmesg|tail**
[   34.323721] apm: BIOS not found.
[   34.462563] sky2 eth0: enabling interface
[   34.466384] ADDRCONF(NETDEV_UP): eth0: link is not ready
[COLOR=DarkOrange]**[   70.977687] Marking TSC unstable due to: cpufreq changes.**[/COLOR]
[   37.147080] [drm] Initialized drm 1.1.0 20060810
[   74.380085] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   74.380101] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   74.380216] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   75.245193] ACPI: EC: non-query interrupt received, switching to interrupt mode
[COLOR=Red][  223.799900] spurious 8259A interrupt: IRQ7.[/COLOR]

**$ tail /var/log/syslog**
May 26 23:20:17 astarte kernel: [   74.380101] PCI: Setting latency timer of device 0000:00:02.0 to 64
May 26 23:20:17 astarte kernel: [   74.380216] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 26 23:20:23 astarte kernel: [   75.245193] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 26 23:20:59 astarte anacron[7130]: Anacron 2.3 started on 2010-05-26
May 26 23:20:59 astarte anacron[7130]: Normal exit (0 jobs run)
May 26 23:24:13 astarte ntpd[4550]: synchronized to 91.189.94.4, stratum 2
May 26 23:24:13 astarte ntpd[4550]: kernel time sync status change 0001
May 26 23:29:40 astarte ntpd[4550]: synchronized to 192.36.143.150, stratum 1
[COLOR=Red]May 26 23:36:28 astarte kernel: [  223.799900] spurious 8259A interrupt: IRQ7.[/COLOR]

```But it must be at user level because for other users it works perfectly well.

---

### Post by HotForLinux on 2010-05-30
I have found the source of this malfunction. It is the

[SIZE=4]dwell-click-applet 2.22.1[/SIZE]

In this desktop, that applet was added to the panel, just to know its features, and then  _"REMOVED_". Nevertheless, its configuration _REMAINED_! (there is even no button to reset all the configuration!)

Moreover, the option: "show position of pointer when the control key is pressed" which had been chosen, interferes with the Ctr-Alt-Del event or signal and disables its normal call to the logout program (however it is called) that shows the dialog box to choose how to leave the session.

---

