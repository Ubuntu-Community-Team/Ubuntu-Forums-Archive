---
title: "Sound problems when network disconnected"
date: 2009-09-10
forum: General Help
---

### Post by jiussa on 2009-09-10
Hi, I'm running Ubuntu 8.10 with Xfce. My sound chipset is HDA Intel Realtek ALC662 rev1.

I suffered an adsl disconnection recently (isp was performing maintenance) and started having serious sound problems. These included:

- If I tried to play an avi with vlc, vlc would not appear for about 10 seconds. I would then hear the sound of the video but the vlc window would not appear and I had to kill the vlc process.

- If I tried to play an audio file with Banshee, banshee would lock up and need to be killed.

- I was unable to open either alsamixer or gnome-volume-control from the command line. Both would immediately become unresponsive.

- Logging into xfce took much longer than usual (about 10 - 15 seconds).

As soon as my adsl connection was restored these problems disappeared. In fact I can reliably reproduce the above problems by logging into my modem and disconnecting the adsl connection.

I find it quite baffling that losing my network connection results in these problems. I would have thought that the sound and network systems would be completely unrelated to each other. Any help would be appreciated in solving this.

Thankyou

---

### Post by jiussa on 2009-09-10
Something else I just noticed:

Whenever I open an avi (using either vlc, totem or banshee) there is a small burst of network activity. I have no idea why this is the case but it happens consistently.

---

### Post by jiussa on 2009-09-11
Anybody have any ideas? I don't expect to be without a network connection very often, but I find it worrying that unrelated parts of my system will break when I am.

---

### Post by P4man on 2009-09-11
What sort of modem/router do you have? If its a LAN connection to an ADSl modem/router then Im as baffled as you. Does unplugging the LAN cable give the same problem?

If its a USB or internal ADSL modem, then at least I can somewhat understand. These are software modems that use your "soundcard" for some of the signal processing of the xDSL signal. Not saying it should behave like that, but then Im no fan of soft/win modems to begin with :).

---

### Post by jiussa on 2009-09-11
Yeah, it's an external iConnect Access 621 adsl modem connected via a Belkin Wireless G router (although my computer has a WIRED connection to the router).

I just tried reproducing the problems with my network cable unplugged from the computer and wasn't able to, i.e. everything worked fine. It seems to only be a problem if the network is connected but the adsl is offline.

---

### Post by jiussa on 2009-09-11
I've also just discovered that I can trigger the problems by locking my firewall (firestarter). It's not quite as bad as when the adsl is disconnected, but opening an avi with vlc takes longer than 5 secs, and starting or switching between songs with banshee takes about 10 secs.

---

### Post by jiussa on 2009-09-11
If anyone's interested, I found the solution to my problem [here]("http://geekwolf.wordpress.com/2008/12/04/bug-301430-in-netcfg-ubuntu-&#8220;ipv6-etchosts-missing-localhost-hostname&#8221;/").

Turns out my system couldn't find the ip of my ipv6 localhost and so was asking my router for it, which would fail and eventually time out.

[Wireshark]("http://www.wireshark.org/") was very useful in diagnosing this.

---

