---
title: "System freeze, no logs no clues"
date: 2009-12-18
forum: General Help
---

### Post by mfa on 2009-12-18
I'm experiencing occasional freeze on Toshiba Portege R500 running Ubuntu 9.04. While this happens i'm only able to move the mouse cursor, but the system does not respond to any clicks. Keyboard control is lost too, except for that i can reboot by issuing ctrl + alt + sysrq + REISUB. I haven't got any clues from log files. In fact, no events get written to the log files when a freeze occurs. I have experienced similar symptoms before, say, once a month or so, but for a couple of weeks it has been occuring more frequently, once or twice a day. I'm using the mouse or the keyboard every time it happens. It never happens while the laptop is idling.

So my question is, is there any debug info reachable while the system is in such a state? I don't see much point in filing a bug report with these symptoms alone.

---

### Post by avilella on 2009-12-19
when that happens, can you plug an external mouse or keyboard and use them effectively or is the whole system unresponsive?

If you can reboot, you can at least look at the stored dmesg logs in:

ls -lt /var/log/dmesg*

That's a good start for a bug report in [http://bugs.launchpad.net](http://bugs.launchpad.net)

> **mfa said:**
> I'm experiencing occasional freeze on Toshiba Portege R500 running Ubuntu 9.04. While this happens i'm only able to move the mouse cursor, but the system does not respond to any clicks. Keyboard control is lost too, except for that i can reboot by issuing ctrl + alt + sysrq + REISUB. I haven't got any clues from log files. In fact, no events get written to the log files when a freeze occurs. I have experienced similar symptoms before, say, once a month or so, but for a couple of weeks it has been occuring more frequently, once or twice a day. I'm using the mouse or the keyboard every time it happens. It never happens while the laptop is idling.

So my question is, is there any debug info reachable while the system is in such a state? I don't see much point in filing a bug report with these symptoms alone.

---

### Post by Lukas666 on 2009-12-19
> **mfa said:**
> I'm experiencing occasional freeze on Toshiba Portege R500 running Ubuntu 9.04. While this happens i'm only able to move the mouse cursor, but the system does not respond to any clicks. Keyboard control is lost too, except for that i can reboot by issuing ctrl + alt + sysrq + REISUB. I haven't got any clues from log files. In fact, no events get written to the log files when a freeze occurs. I have experienced similar symptoms before, say, once a month or so, but for a couple of weeks it has been occuring more frequently, once or twice a day. I'm using the mouse or the keyboard every time it happens. It never happens while the laptop is idling.

So my question is, is there any debug info reachable while the system is in such a state? I don't see much point in filing a bug report with these symptoms alone.

I had similar symptoms when one of the memory sticks went bad. Try a live CD with ubuntu or a different distro. First step is to determine if it's a hardware of software issue. Running memtest86 is a must.

---

### Post by jerrrys on 2009-12-19
> **Lukas666 said:**
> I had similar symptoms when one of the memory sticks went bad. Try a live CD with ubuntu or a different distro. First step is to determine if it's a hardware of software issue. Running memtest86 is a must.

me too.  happen on a desktop and it was a memory stick...

---

### Post by mfa on 2009-12-20
> **Lukas666 said:**
> I had similar symptoms when one of the memory sticks went bad. Try a live CD with ubuntu or a different distro. First step is to determine if it's a hardware of software issue. Running memtest86 is a must.

Thank you for the suggestion. I just ran memtest86 for one pass, took about an hour, didn't find any errors. I'm going to run more tests overnight just to be sure.

---

### Post by Lukas666 on 2009-12-20
> **mfa said:**
> Thank you for the suggestion. I just ran memtest86 for one pass, took about an hour, didn't find any errors. I'm going to run more tests overnight just to be sure.

1. Test sticks individually! I had 4 x2GB sticks and only testing them one by one found errors.

2. Get the most recent memtest86 version. It's not on the website (they have version 3.5). I downloaded opensuse 11.2 live CD and it has Memtest86 version 4.0 in the bootloader. That's the most recent version and I could not find it anywhere else.

Good luck!

---

### Post by mfa on 2009-12-20
Thank you for your reply!
> **avilella said:**
> when that happens, can you plug an external mouse or keyboard and use them effectively or is the whole system unresponsive?
I will try to plug in USB keyboard and mouse next time and see if it works.
> **avilella said:**
> If you can reboot, you can at least look at the stored dmesg logs in:

ls -lt /var/log/dmesg*

That's a good start for a bug report in [http://bugs.launchpad.net](http://bugs.launchpad.net)

I've looked into just about every file in /var/log but there really doesn't seem to be anything out of the ordinary there. I'll include a small excerpt from syslog just to give you an example. The only thing that catches my eye is that there are no entries for about 10 minutes before the "SysRq : Keyboard mode set to system default", which is me doing REISUB. The freeze most certainly has occured at some time during that 10 minute gap.

```

Nov 23 08:05:12 kernel: [27165.734857] PM: resume devices took 2.792 seconds
Nov 23 08:05:12 kernel: [27165.734979] Restarting tasks ... done.
Nov 23 08:05:12 kernel: [27166.036095] usb 2-2: USB disconnect, address 4
Nov 23 08:05:12 kernel: [27166.066597] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 23 08:05:12 kernel: [27166.277129] usb 2-2: new full speed USB device using uhci_hcd and address 5
Nov 23 08:05:12 kernel: [27166.277859] Registered led device: iwl-phy0:radio
Nov 23 08:05:12 kernel: [27166.277900] Registered led device: iwl-phy0:assoc
Nov 23 08:05:12 kernel: [27166.277938] Registered led device: iwl-phy0:RX
Nov 23 08:05:12 kernel: [27166.277976] Registered led device: iwl-phy0:TX
Nov 23 08:05:12 kernel: [27166.335636] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 23 08:05:12 kernel: [27166.395399] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Nov 23 08:05:12 kernel: [27166.452562] usb 2-2: configuration #1 chosen from 1 choice
Nov 23 08:05:13 kernel: [27167.092742] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input14
Nov 23 08:05:13 kernel: [27167.153044] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input15
Nov 23 08:05:41 kernel: [27194.877127] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 23 08:14:40 kernel: [27733.704456] SysRq : Keyboard mode set to system default
Nov 23 08:14:43 exiting on signal 15
Nov 23 08:15:43 syslogd 1.5.0#5ubuntu3: restart.

```

I can get some response with REISUB and i was thinking that there might be some other sequence i could type that would force the system to dump something about it's state to some file. The next thing i would hope is that this would give some hint to what is actually going wrong.

---

### Post by mfa on 2009-12-20
> **Lukas666 said:**
> 1. Test sticks individually! I had 4 x2GB sticks and only testing them one by one found errors.
I believe the Portege R500 has 1GB built in and 1GB optional memory modules. Unless there is a way to somehow select the memory module through memtest86, the best i can do is to remove the optional 1GB module and test the built in module alone.

> **Lukas666 said:**
> 2. Get the most recent memtest86 version. It's not on the website (they have version 3.5). I downloaded opensuse 11.2 live CD and it has Memtest86 version 4.0 in the bootloader. That's the most recent version and I could not find it anywhere else.

I followed your advice and aquired an opensuse 11.2 live CD with memtest86 4.00. I ran one pass with both memory modules installed without an error. The built in memory just finished a pass without an error. It's beginning to look like the problem isn't in the memory. Anyway, i'll run a series of tests overnight in hope to catch an error.

Thank you for advice!

---

### Post by Lukas666 on 2009-12-20
> **mfa said:**
> I believe the Portege R500 has 1GB built in and 1GB optional memory modules. Unless there is a way to somehow select the memory module through memtest86, the best i can do is to remove the optional 1GB module and test the built in module alone.


Yep, that's how it should be done. Only one module sitting in THE slot (usually slot 0) at a time.

---

### Post by mfa on 2010-03-13
> **avilella said:**
> when that happens, can you plug an external mouse or keyboard and use them effectively or is the whole system unresponsive?

Plugging in USB mouse and keyboard makes no difference - no response.

Just for update, after trying various solutions suggested here, the problem went back to a monthly schedule for a while before it got more frequent again. I recently updated to Karmic, and haven't had a freeze yet. If and when the problem comes back, i'll be submitting a bug report. There's just not much to put into it, so i'm afraid it won't be much use, but i'll do it anyway.

Thanks again for everyone!

---

### Post by romy.mathew on 2011-01-15
Hi 

Even I experinced this system freeze on ubuntu 10.04. I was working late night without any problem. but on morning when i logged in it seems my system got freezed completely on log in window. I could not move my mouse to select the user neither type my password. I used an USB mouse then my mouse start moving around[Thanks for the posts and members]. But I found my log in environment has changed completely. It seems to be quite fancy earlier but now it looks more optional now. 

I havnt able to log in yet as I dont have an USB keyboard to enter the password. I just want to know the reason for this change .

---

