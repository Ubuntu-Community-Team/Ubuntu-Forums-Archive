---
title: "Linking up Palm Z22"
date: 2006-03-06
forum: General Help
---

### Post by deadgobby on 2006-03-06
Looking for some help on linking up Palm Z22 to Breezy. I have tried with Jpilot, Kpilot, and Gpilot. I have tried what people have done in past post. So far no go.
Gobby:mad:

---

### Post by lH)4~mK0e on 2006-09-10
You should try Dapper Drake.  I use Kubuntu so I am using Kpilot.  Here's how I got it working.

[http://kubuntuforums.net/forums/index.php?topic=8826.0]("http://kubuntuforums.net/forums/index.php?topic=8826.0")

---

### Post by knoxautoguy on 2006-11-16
I tried this link and even after registering with Kubuntu Forums, found the link to be dead.  I also need to link up to a Palm Z22 via USB.

---

### Post by j o e l on 2006-12-14
knoxautoguy, I just purchased a palm z22 myself.  Although, I have not tried this yet, I did just find this [link]("http://howto-pages.org/palm_z22/") to someone who got it working on slackware linux.  I thought I would try to see if someone got it working on Ubuntu first, when I found this post.

Hope we can get it to work.    Good luck.

---

### Post by rfdeshon on 2007-01-04
I have a Z22 that is syncing great with JPilot (or slightly less great with Evolution/gpilot). Here is the link that I used to get it set up:
[JPilot and Z22]("http://howto-pages.org/palm_z22/")

Of course, I use Ubuntu Edgy so I don't know how helpful this will be for you but... good luck!

---

### Post by Tritonio on 2007-05-15
I think that most palms don't became a device untill they are told to hotsync. Till then they just charge their batteries. Z22 is different. By the time you connect it it becomes a device! And when you press the hotsync button on the palm it disconnects and reconnects to the pc. That's the reason I could get it working with Jpilot and feisty(after installing the visor module to the kernel): I pressed the Jpilot hotsync icon and AFTER this the hotsync on the palm. What happens is that jpilot opens ttyUSB1 and locks it and then Z22 dsconnects and reconnects. This results into creating ttyUSB2 and ttyUSB3. If I press the sync button on the palm first and then on the jpilot I have no problems at all.

---

### Post by sethtriggs on 2008-03-09
I've been trying to get mine to work; I've gone to the Jpilot, you name it - I can't get it to work suitably.

Basically, what happens is I've installed Visor, and I've installed USBserial. I've done the modserial trick, and I made the special rule to get the /dev/pilot to work with USB.

I did notice something bizarre though - the gpilotd-control-applet is duplicated numerous times, and there's a warning about "druid". This error is:

"Cannot run druid if PDAs or devices already configured"

 Running killall gpilotd removes the duplicate entries and then the Gnome-Pilot window finally pops up.

Settings are:

Cradle
USB
Timeout: 20
/dev/pilot
Speed: 115200

I can get it to synchronize once and then the Gpilot applet crashes and locks up. Running killall gpilotd will bring it back. Though sometimes it results in multiple copies of Gpilot launching.

Forget backing stuff up to Jpilot...I can't do it at all. It will just crash and won't back up anything on my PDA.

Here are my custom UDEV rules:
```
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
```

They were put in the /etc/udev/rules.d/10-custom.rules as the instructions went.

Thanks in advance,


Seth

---

### Post by sethtriggs on 2008-03-10
I was able to run the tail/messages command, and it appears that my USB connects properly.

```

Mar 10 13:18:45 seth-laptop kernel: [ 1180.752000] visor 2-2:1.0: device disconnected
Mar 10 13:18:46 seth-laptop kernel: [ 1181.440000] usb 2-2: new full speed USB device using ohci_hcd and address 13
Mar 10 13:18:46 seth-laptop kernel: [ 1181.644000] usb 2-2: configuration #1 chosen from 1 choice
Mar 10 13:18:46 seth-laptop kernel: [ 1181.648000] visor 2-2:1.0: Handspring Visor / Palm OS converter detected
Mar 10 13:18:46 seth-laptop kernel: [ 1181.648000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB2
Mar 10 13:18:46 seth-laptop kernel: [ 1181.648000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB3

```

This one, I'm trying on my laptop - it exhibits the same symptoms as my Ubuntu desktop.

I tried uninstalling pilot-link and the like (since it was claimed elsewhere that jpilot and gpilotd do not like one another); this seems to have no effect and I still can't connect. Though at least I don't have the annoying duplicate gpilot-control-applet entries in my system monitor.

-Seth

---

