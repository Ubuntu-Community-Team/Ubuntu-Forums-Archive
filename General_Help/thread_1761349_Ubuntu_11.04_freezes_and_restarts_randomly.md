---
title: "Ubuntu 11.04 freezes and restarts randomly"
date: 2011-05-18
forum: General Help
---

### Post by NekoMao on 2011-05-18
I just upgraded to 11.04, and now every so often the screen will freeze, but I can still move the mouse. I press ctrl alt del and nothing happens, I try waiting and no matter how long I wait it remains the same, so I have to turn the power off.  Also, this happens less often but twice already when I'm in the middle of doing something, ubuntu will reset itself. It doesn't completely restart...I'm not sure how to describe it, but the screen turns black with white writing for a second then it brings up the login screen.  I apologise if these are obvious things to fix, but I'm not very computer smart.

---

### Post by SynonM on 2011-05-18
Did you use Compiz GUI, it could be a problem with your GPU, or something to do with OpenGL's interaction with your GPU.
That happened to me.

...let me know...):P

---

### Post by NormanFLinux on 2011-05-18
Most likely a kernel panic induced by a live wireless connection with a Broadcom card. Temporary workaround is to shut off wireless LAN in the BIOS and connected to Ethernet; permanent fix is to download and install the 2.6.39.0 kernel and reboot. Then wireless can be turned on again and there should be no more kernel panic in Ubuntu.

---

### Post by Yasho on 2011-05-21
> **NekoMao said:**
> I just upgraded to 11.04, and now every so often the screen will freeze, but I can still move the mouse. I press ctrl alt del and nothing happens, I try waiting and no matter how long I wait it remains the same, so I have to turn the power off.  Also, this happens less often but twice already when I'm in the middle of doing something, ubuntu will reset itself. It doesn't completely restart...I'm not sure how to describe it, but the screen turns black with white writing for a second then it brings up the login screen.  I apologise if these are obvious things to fix, but I'm not very computer smart.

Hi all,
I have the same problem here. I'm using a Dell Inspiron 1525 laptop, dual boot Natty 32 bit and WinXP. I am using the Gnome desktop since I'm not too comfortable with the Unity. There is no problem of such a freeze or reboot when I log into Windows XP. In Ubuntu, however, I'm facing the same issues of 'mouse able to move, but everything else is frozen'. The only way out is to force a shutdown using the power button. During the restart, thereafter, there is no disk check or whatever.
Similarly, in the middle of something, I will suddenly see the black screen with the bootup text scroll (Sorry, I don't know what it is called - the text that comes up when you start the computer in Ubuntu)  and then the login is pretty fast.
I suppose I should have the latest kernel, since I have done a full update on the system at about 16:00 GMT on 21 May, and this is still happening now at about 02:00 GMT on 22 May. In fact, this "hanging" has increased in the last four or five days, so may be something to do with a latest update. Also, I'm on a wired broadband, my WiFi is off.

---

### Post by tank82 on 2011-05-25
Hi, I was looking for a solution, since the same thing happens to me. In this [thread]("http://ubuntuforums.org/showthread.php?t=1749511&highlight=natty+freezes+screen") I found that the problem might be related to the kernel. 

So I [upgraded]("http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0") the kernel to 2.6.39-0-generic and so far so good, the problem is gone :)

Hope it helps

---

### Post by phz_swe on 2011-05-28
> **NormanFLinux said:**
> Most likely a kernel panic induced by a live wireless connection with a Broadcom card. Temporary workaround is to shut off wireless LAN in the BIOS and connected to Ethernet; permanent fix is to download and install the 2.6.39.0 kernel and reboot. Then wireless can be turned on again and there should be no more kernel panic in Ubuntu.

I ran into this error with a Broadcom card on an Acer Aspire 5745G. The computer would hang and reboot. Sample dmesg output: [http://pastebin.com/SabTTyy0](http://pastebin.com/SabTTyy0) (not from a session that crashed, but there are a lot of WLAN errors present).

[s]Upgrade to 2.6.39-0 from kernel-ppa solved it.[/s]

EDIT: Nope, error noticed again. It seems to only happen whan I'm in a spot with bad WLAN reception. network-manager automatically connects me, but I can't reach any network places. A short while after trying, the computer reboots.

EDIT 2011-06-17: My problem still persists. It happens when I start to use the wireless connection. At first I thought it was because of bad reception, but I just now realised that it also is correlated with me running on battery power. Will investigate this further.

For some reason, it also seems to happen less frequently if I have ping running in the background, talking to my access point. I discovered this by chance. It might be related to a power saving issue or something for the wireless connection - if it feels unused, maybe it tries to set som power saving flag which crashes the system.

I can't see any messages in dmesg or any other log I can think of, though. If anyone has a good idea of how to find an error message to clarify the issue, I would be glad to hear it.

EDIT 2011-06-17-2: Thank Xenu, I think I solved it. The problem was battery/AC power. In battery mode, the driver told the card to go into a power saving mode.

In AC mode:
```
$ sudo iwconfig eth1 | grep power
          Power Management:off
```

On battery power:
```
$ sudo iwconfig eth1 | grep power
          Power Managementmode:All packets received
```

In this mode, the driver would die and take Ubuntu with it, which triggered a hard reboot on my laptop.

To fix it (on battery power):
```
$ sudo iwconfig eth1 power off
$ sudo iwconfig eth1 | grep power
          Power Management:off
```

After that it worked without a hitch. I thought I had fixed this problem once before though, so I'll wait and see if everything continues to work before closing the issue.

I'm not against power management per se, but when it renders my computer unusable, I rather inactivate it :-)

---

### Post by phz_swe on 2011-06-17
The people in this thread might very well have different problems, with different solutions, but I found the one to mine.

My laptop rebooted frequently when it tried to use the WLAN when running on battery power. It started to occur after upgrade to 11.04. No important messages were logged, all that happened was that the system froze, became totally unresponsive, and after ~5 seconds rebooted.

I have the following WLAN-card (info from lspci):
```
03:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
```

I use the "wl" module.

In AC mode, I got the following output:
```
$ sudo iwconfig eth1 | grep power
          Power Management:off
```

On battery power:
```
$ sudo iwconfig eth1 | grep power
          Power Managementmode:All packets received
```

This means the power saving mode is active (see "man iwconfig").

To turn it off (still on battery power):
```
$ sudo iwconfig eth1 power off
$ sudo iwconfig eth1 | grep power
          Power Management:off
```

Now it worked. The problem is the file /usr/lib/pm-utils/power.d/wireless, which sets power saving mode for the card when on battery. It is part of the pm-utils package. Power saving _should_ be a good thing, but apparently it doesn't work very well. My case was extreme, but I've seen many reports of very bad WLAN performance with power saving active (which in turn might be related to the AP not handling the function gracefully, but that's another story).

**To fix it permanently:** create /etc/pm/power.d/wireless with the content
```
#!/bin/sh
/sbin/iwconfig eth1 power off
```
_and make it executable_ (I missed this point for a while)! Now this file will override /usr/lib/pm-utils/power.d/wireless and disable power saving mode after reboot. It might suffice to just touch /etc/pm/power.d/wireless and leave it blank, depending on your system, but it wasn't enough for me. The power saving mode can apparently be activated through other mechanisms.

For those who want to just copy+paste a command:
```
echo "#!/bin/sh
/sbin/iwconfig eth1 power off" | sudo tee /etc/pm/power.d/wireless
sudo chmod +x /etc/pm/power.d/wireless
```
To be modified if your card is not named "eth1", see output of "iwconfig". Check the power saving status with "sudo iwconfig" after reboot. It should be off.

---

### Post by _Mono_ on 2011-07-07
Dear all,

I am having exactly the same two problems, either random freezes (today 3) (with no chance of escape) or random relogs, with loss of all not saved data... (today 2). Though I am working on a 64-bit Desktop machine and a standard LAN cable. So no battery nor WLAN...

This bug is quite annoying, especially since I am doing long Monte Carlo calculations. So any help is appreciated.

---

### Post by amulet on 2011-09-23
> **_Mono_ said:**
> Dear all,

I am having exactly the same two problems, either random freezes (today 3) (with no chance of escape) or random relogs, with loss of all not saved data... (today 2). Though I am working on a 64-bit Desktop machine and a standard LAN cable. So no battery nor WLAN...

This bug is quite annoying, especially since I am doing long Monte Carlo calculations. So any help is appreciated.

I confirm I have precisely the same problem, working on 32 bit desktop with LAN.  It can happen 3 or 4 times a day or not at all for 3-4 days! Totally random, and totally infuriating.

---

