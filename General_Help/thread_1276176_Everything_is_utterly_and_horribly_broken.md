---
title: "Everything is utterly and horribly broken"
date: 2009-09-26
forum: General Help
---

### Post by HyperHacker on 2009-09-26
I've been running Xubuntu on my desktop and laptop for about 2 years now. Both used to work great. Since "upgrading" to 9.04, both have developed more and more problems to the point of being almost completely unusable.

My laptop simply stopped connecting to any network, wired or wireless. Now even the 8.04 live CD can't do it anymore. Used to work fine. Something seems to be *permanently* broken. This happened overnight when it was powered off. I'm certain nothing could have happened to it.
Before that it was freezing up at random, in a strange manner: everything continued to run so long as I moved the mouse. If I left it still, everything would stop.
I left it a while, then came back, and magically the networking worked again. For about half an hour. Then the machine completely froze, and it hasn't worked again since.


My desktop is running so unimaginably slow I can hardly do anything. Anything I click - to open a menu, a web page in Firefox, a directory in Thunar, etc - may take *several minutes* to respond. Sometimes it just gives up. During this time I can do nothing else. Even the mouse cursor lags severely. Switching windows can be so slow I can literally get up and make myself a snack and come back before the window has actually come up and rendered. Or I can stay to watch each individual pixel appear one at a time.
I am NOT exaggerating in the slightest.

As I type, it can take as much as a minute for my text to actually appear. Often characters get dropped entirely.

MPD randomly stopped in the middle of a song some time ago and has not responded to anything since. Amarok will not play. mplayer crashes:
-Any time there is heavy disk access.
-Any time there is heavy CPU usage.
-Any time I connect or disconnect a USB device.
-For no apparent reason after usually no more than 8 minutes of playing. Some days no more than 3. Sometimes it will play several songs just fine and then crash 6 times during one song. Sometimes it will play, stutter a little, and then crash again within 10 seconds. Sometimes it will play a SINGLE FRAME and then crash again, or even crash before it's started playing.

Doing just about anything more strenuous than typing in this textbox - deleting a line, moving the cursor (with arrow keys or mouse), adjusting the volume, restarting mplayer again - is likely to lock the entire system up solid for as much as 15 seconds. The disk access LED comes on steady. Sometimes the CPU usage also jumps to 100% the entire time; other times it remains at as little as 2%. (Unless it's just locked up so hard that Conky doesn't even update during this period.)

Even when the machine is sitting there doing absolutely nothing, every few minutes there is a spike in CPU usage or a HUGE amount of disk seeking, which basically locks it up solid for a while. Or mplayer will crash. I've checked that it's not a problem with the songs themselves. A song that crashed 6 times one day may play perfectly the next.

My Internet connection has become horribly slow and unreliable as well. Average download speeds have dropped from ~80k/s to 4k/s. Drops several times per hour.

Pidgin has taken to randomly not playing sounds, and every time my connection drops, nearly 100 buddies have been moved to an "orphans" group.

Thunar has recently started crashing at random as well.

The kernel has not crashed, so I'm pretty certain this is not a hardware issue. I have tested the RAM and power supply and both are working perfectly. I know of no way to test the CPU or hard drive, but the hard drive is quite new, and I can't imagine the kernel not crashing with a faulty CPU.

This is completely ridiculous. After using Linux for this long, I am debating whether to install Windows or a hammer. 8.04 and 8.10 worked great but now even they refuse to work anymore.

---

### Post by oldos2er on 2009-09-26
Have you run fsck lately?

---

### Post by blueridgedog on 2009-09-26
Also, are the temps OK?  If the performance is off when you are on a LiveCD, I would look for hardware causes.

---

### Post by HyperHacker on 2009-09-26
No idea how to check temperature on a laptop. They're fine on the desktop, around 45°C at maximum.

Can I run fsck from within Xubuntu? If not, how?

The sound system just died, while I was off cleaning in another room. Randomly stuttered and quit. mplayer is still going but no sound plays at all now. Nothing else going on at the time.

---

### Post by blueridgedog on 2009-09-26
You can check the tempurature of your chips with lm-sensors.

To install and setup:

```
sudo apt-get install lm-sensors
sudo sensors-detect
```

Then just run with:
```

lm-sensors
```

You should also take a look at the output of 

```
top
```

Just to see what applications are using the CPU and:

```
free
```

to see where your memory is going.

---

### Post by HyperHacker on 2009-09-27
That's the thing, I've got Conky monitoring CPU and memory usage, and they both look normal, except for the random CPU spikes, which mostly are either Firefox (who knows what it's doing) or several programs htting 5-10% at once.

I'm not sure if lm-sensors will work on my laptop, and I can't install it to try without any working network connection.

---

### Post by blueridgedog on 2009-09-27
If you are using conky, then you have good temps on the cpu.  It may be the gfx card that is getting hot.  I don't have any other great suggestions.  A system that runs poorly even when booted from the LiveCD is more likely to have hardware issues.

---

### Post by paradigm2 on 2009-09-27
It could be many different things.

To start check the memory (use memtester or memtest86 from the liveCD) then also check the hard drive file structure as well as the SMART info,

---

### Post by oldos2er on 2009-09-27
> **HyperHacker said:**
>  Can I run fsck from within Xubuntu? If not, how?

 Run **sudo touch /forcefsck **to run fsck on next boot. Partitions need to be unmounted before running fsck.

---

### Post by HyperHacker on 2009-10-08
I rebooted, and the system has been much more responsive, but still slows to a crawl sometimes. Firefox 3.5 in particular tends to lock up solid at 100% CPU. It does seem to be gradually slowing, though memory/swap usage and temperatures aren't increasing. mplayer no longer crashes when connecting a USB device (but still in the other situations mentioned, including for no apparent reason). Other than that, the problems remain.

I rebooted again to test the hard disk using Seagate's utilities, and reorganized some USB and network cables. After this, my sound card isn't detected.> $ aplay -l
aplay: device_list:217: no soundcards found...Only "Null Output (Pulseaudio Mixer)" and "Monitor of Null Output (Pulseaudio Mixer)" are listed in xfce4-mixer. Shut down completely, checked the card was seated properly, checked the cables were connected, no difference. I also forced fsck, and I wasn't there to see the results, but it booted up normally so I assume nothing severe happened.

The hard disk utility reported no errors reading from any sector, but I'm still suspecting it. Is there a program that performs a write test? Read the sector into memory, overwrite it with something, read back to see if it worked properly, and restore the original content? Perhaps doing them out of order to cause some seeking, and reporting any unusually long response times? The whole system seems to perform extremely poorly when there is heavy disk activity, which makes me suspect the disk is working but very slowly. The entire system is in a Truecrypt partition, but I don't think this should cause such a severe effect. Truecrypt uses negligible CPU time, the performance of video playback isn't harmed, and the slowdown isn't consistent.

I also have an external USB hard disk, which is also encrypted. I notice the POST hangs at trying to read its model name; I have to leave it unplugged until afterward. Besides that it seems to work fine, though I haven't tested it; I'm not sure the test utility can test a USB disk. I'm leaving it unmounted for now to see if that helps anything.

Of note as well is that Screenlets keeps forgetting my settings. I had only two of them running and a while ago one reverted to all default settings. I decided to simply remove it, but it keeps coming back at startup. Today, the other one also lost its settings, but it seems to be keeping them now.

The RAM and power supply have been tested with no sign of issue, and the system, CPU and hard disk temperatures are all approximately 40°C at all times. That only leaves the CPU, motherboard, and DVD drive; I can't imagine the former two having an issue that doesn't cause much more severe problems (kernel panics, etc), and I doubt the latter could cause any problem at all when not in use. It reads and burns discs just fine.

One last annoyance is I can't seem to get the "motion" daemon not to start up. I can't seem to find its config file. I want it installed, but I don't want it to start automatically.


As for the laptop, I dug out its factory restore disc (4 years ago computers actually came with these!) and reverted it to its original state. Windows XP was able to detect wireless networks (Linux was unable to use wifi at all, probably because I needed to install a driver), but still not able to detect a wired connection. So that seems to be a hardware issue. It would not be that bad either if wifi worked, but with neither working I can't install any packages. (Other than downloading them individually and transferring via USB stick, which can take forever when a package has many dependencies which all have their own dependencies, etc.) So installing the wifi driver may be near impossible.
Can SSH be coaxed to connect over a serial port? I could tunnel ports 80 and 443 through it, and hopefully that would be enough to download the needed packages.

I put some videos on it that I wanted to show someone, and I was sure they played in Totem when tried, but when it came time to actually show them, it couldn't find the necessary codec. In fact it doesn't seem to have the codecs for anything but OGG and FLAC, though fortunately I was able to install the needed packages for MP3.

The RAM has been tested on this machine as well. I don't know how I'd test the power supply (never opened it, but I doubt there are simple cables I can stick a multimeter onto), and I don't think any programs have been able to detect voltage or temperature sensors, though they must exist.

---

### Post by HyperHacker on 2009-10-17
So I gave up and completely reinstalled. I kept a copy of my home directory and copied it back afterward.

Sound and mpd work again, though I had a little trouble starting mpd. I haven't rebooted since then so I can't say if it's going to keep working. Since mpd works I haven't tried Amarok or mplayer. Don't really care for either of them.
mpd randomly freaked out and started skipping through a song once though.

Scim runs, but doesn't do anything useful. Doesn't respond to keyboard shortcuts or display the panel.

Hasn't slowed to a crawl yet, except Firefox. When I open a new tab it likes to just hang for a minute, pop up a "slow script" box which won't close for a few seconds after it shows up, and then continue running slow for about a minute afterward. During this time it has a habit of randomly following links on the page or closing other tabs.

Pidgin is still shuffling buddies and sometimes not playing sounds.

Thunar hasn't crashed yet. Geany is still not redrawing properly. Didn't install motion so no trouble with it. :p

Curious thing I notice is it's running warmer now (46°C), and it hasn't been unusually warm in the room (a bit cold actually). Fans are working and unobstructed.

I've tried to connect a Rocketfish Bluetooth keyboard and mouse. The mouse works great, but the keyboard won't stay connected. It doesn't show up in the device scan unless I delete it from the known device list. As soon as it connects, it disconnects again showing this in syslog:> Oct 11 20:42:56 mercury bluetoothd[3286]: Discovery session 0xb913a660 with :1.91 activated
Oct 11 20:43:01 mercury bluetoothd[3286]: link_key_request (sba=00:02:72:11:BD:29, dba=00:02:76:0B:34:C4)
Oct 11 20:43:01 mercury bluetoothd[3286]: pin_code_request (sba=00:02:72:11:BD:29, dba=00:02:76:0B:34:C4)
Oct 11 20:43:05 mercury bluetoothd[3286]: link_key_notify (sba=00:02:72:11:BD:29, dba=00:02:76:0B:34:C4, type=0)
Oct 11 20:43:06 mercury bluetoothd[3286]: sdp_extract_attr: Unknown data descriptor : 0xa0 terminating  
Oct 11 20:43:06 mercury bluetoothd[3286]: sdp_extract_attr: Unknown data descriptor : 0x65 terminating  
Oct 11 20:43:06 mercury bluetoothd[3286]: /org/bluez/3286/hci0/dev_00_02_76_0B_34_C4: error updating services: Protocol error (71)I've left the batteries out all day. There's no status indicator of any sort on it to tell me what it's doing.
At the same time I can have the mouse, two Wiimotes, and a phone connected without a problem.

No luck with the laptop: can't find a screwdriver that fits those tiny holes D: ought to look at it myself before I spend $50 having a loose cable reseated or some such nonsense.

---

