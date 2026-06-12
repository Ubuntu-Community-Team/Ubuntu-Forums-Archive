---
title: "How do I get kernel panic info? Can't find anything in the /var/log"
date: 2011-01-26
forum: General Help
---

### Post by MadnessRed on 2011-01-26
Hi, I am getting Kernel panic. I was getting is very frequently before, then I re-installed and it starts off fine then after a while it starts happening again.

The problem is I have no idea what is causing it. The screen is completely frozen and won't respond to anything. The Alt sysreq combinations don't work, and I have to power off with the button.

When I restart I can't find anything to help explain.
Here's the bit of the syslog

```
Jan 26 12:45:10 Anthony-Acer kernel: [   47.792974] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jan 26 12:45:10 Anthony-Acer kernel: [   47.792977] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jan 26 12:45:10 Anthony-Acer kernel: [   47.792979] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Jan 26 12:45:17 Anthony-Acer kernel: [   55.129008] usb 3-1: USB disconnect, address 2
Jan 26 12:45:19 Anthony-Acer kernel: [   56.880082] usb 3-1: new full speed USB device using ohci_hcd and address 4
Jan 26 12:45:24 Anthony-Acer kernel: [   61.285683] lo: Disabled Privacy Extensions
Jan 26 12:51:17 Anthony-Acer kernel: [  414.554688] PGD 11d41f067 PUD 11b3fc067 PMD 0 
Jan 26 12:51:17 Anthony-AcJan 26 12:53:04 Anthony-Acer kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 26 12:53:04 Anthony-Acer rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="885" x-info="http://www.rsyslog.com"] (re)start
Jan 26 12:53:04 Anthony-Acer rsyslogd: rsyslogd's groupid changed to 103
Jan 26 12:53:04 Anthony-Acer rsyslogd: rsyslogd's userid changed to 101
Jan 26 12:53:04 Anthony-Acer kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 26 12:53:04 Anthony-Acer kernel: [    0.000000] Initializing cgroup subsys cpu
```

The interesting one is:
Jan 26 12:51:17 Anthony-Ac
Which appears that it has been trying to write something then failed half-way.

Apparently in console mode, kernel panic gives an output, is there anyway to get ubuntu to drop into shell on a kernel panic?

Many thanks.

Anthony



edit: "PGD 11d41f067 PUD 11b3fc067 PMD 0 " appears to be something to do with RAM

---

### Post by Frogs Hair on 2011-01-26
Have looked at the kernel log ? If the problem is driver related it may show up in the jockey or xorg log if you are using proprietary drivers.

---

### Post by MadnessRed on 2011-01-27
> **Frogs Hair said:**
> Have looked at the kernel log ? If the problem is driver related it may show up in the jockey or xorg log if you are using proprietary drivers.

kern.log shows this:
```
Jan 27 20:10:56 Anthony-Acer kernel: [ 4211.120093] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:11:57 Anthony-Acer kernel: [ 4272.081187] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:12:58 Anthony-Acer kernel: [ 4333.122562] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:13:59 Anthony-Acer kernel: [ 4394.080340] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:15:00 Anthony-Acer kernel: [ 4455.121833] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:16:01 Anthony-Acer kernel: [ 4516.080673] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:17:02 Anthony-Acer kernel: [ 4577.120066] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:18:03 Anthony-Acer kernel: [ 4638.080087] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:19:04 Anthony-Acer kernel: [ 4699.120071] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:20:05 Anthony-Acer kernel: [ 4760.080063] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:21:06 Anthony-Acer kernel: [ 4821.122590] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jan 27 20:23:28 Anthony-Acer kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 27 20:23:28 Anthony-Acer kernel: [    0.000000] Initializing cgroup subsys cpuset
```

jockey.log is empty. No contents.

Any suggestions?

---

