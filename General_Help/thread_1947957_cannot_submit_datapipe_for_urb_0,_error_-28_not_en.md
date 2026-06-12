---
title: "cannot submit datapipe for urb 0, error -28: not enough bandwidth"
date: 2012-03-27
forum: General Help
---

### Post by SamuelC on 2012-03-27
First, a bit of background: the machine in question is used by a student radio organization. Equipped with a [Behringer UCA202]("http://www.behringer.com/EN/Products/UCA202.aspx") USB audio interface, its primary task is to run [DarkIce]("http://code.google.com/p/darkice/"), a real-time audio encoder, 24/7 to encode incoming audio to MP3 and then funnel it off to an Icecast server. (Secondary tasks include playing back playlisted and prerecorded content.) The machine is currently running Ubuntu 10.10 32-bit.

Recently, I've been running into a repeating problem where literally hundreds of copies of the following error are generated per second and logged in /var/log/kern.log and /var/log/syslog, quickly filling the primary hard drive (a 32GB SSD):

```
Mar 26 20:03:29 *hostname* kernel: [537023.037432] cannot submit datapipe for urb 0, error -28: not enough bandwidth
```

I'm not sure what this is related to. It generally starts occurring directly after the DarkIce process starts – we restart DarkIce twice per day: once at noon to serve the broadcast day with a configuration file using the [localDumpFile]("http://manpages.ubuntu.com/manpages/hardy/man5/darkice.cfg.5.html") functionality, and once at 23:00 with a configuration file that doesn't specify a local dump – and may occur regardless of which configuration file is used. In the event that it does occur, DarkIce fails to send any audio to the Icecast server.

I'm not aware of any way to systematically reproduce the issue. To make it hush up and stop bothering things, I generally do the following:
[LIST]
[*]Stop rsyslog.
[*]Delete the offending bloated log files.
[*]Kill the DarkIce process.
[*]Restart rsyslog.
[*]Restart DarkIce.
[/LIST]

I feel like the issue may not be directly related to DarkIce, due to the fact that DarkIce has not been updated since the system was set up: we're still running 0.20.1; moreover, there have not been any real changes to the software since that version. I have a suspicion that it may have been due to a kernel issue, as it seems to have gone away/come back as kernel updates have been released; given that, I tried manually updating to a Natty kernel (2.6.38-13-generic-pae) but it doesn't seem to have changed anything.

Any help would be greatly appreciated – obviously, when this error arises, it completely cripples the broadcast until I can do something about it.

---

### Post by sanderj on 2012-03-28
Did you Google "cannot submit datapipe for urb 0, error -28: not enough bandwidth"? Because when I do that, I see a lot of options / causes:

- kernel version
- no / another usb hub
- powered usb hub / device
- ALSA player sound mute

---

### Post by SamuelC on 2012-03-28
Thanks for your reply.

- The kernel version is what I'm primarily asking about. Because I don't know for sure which versions were good, which were bad, and which didn't stick around for long enough to act up, that's a hard thing to figure out. I'm interested in the possibility of better/different logging that would more precisely identify the cause of the error, not just the occurrence of the error.
- The interface is connected directly to the motherboard. I'll try plugging it into a different port, but I'm not sure what it'd do.
- The device is bus-powered and has no option for external power. It's a very small device.
- No non-GUI controls have been changed by me and I don't think anyone else interacting with the system would know how. Additionally, I don't think anyone would bother to touch the GUI controls as it's much easier to control volume and such from the physical mixer.

---

### Post by _az_ on 2012-05-02
I have the same problem with 3.2.0-24-generic but not with 3.0.0-17-generic

---

