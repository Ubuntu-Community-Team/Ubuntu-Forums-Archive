---
title: "Volume control not working on Karmic Koala"
date: 2009-11-07
forum: General Help
---

### Post by arvindayyangar on 2009-11-07
Hi all,
  I just updated my machine from 9.04 to 9.10 and realized my sound is not working..
When I play songs, hear no sound even though the player seems to be playing them. However the volume control icon is disabled on the player.
I cant even find the Volume Control application in Applications or on the panel..


When I start Preferences->Sound, it throws a dialog box
"Waiting for sound device to respond"

$lspci
  |
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
|
|


Is anyone else facing similar problems ?

---

### Post by sc30317 on 2009-11-07
Maybe try removing the volume control and adding a new one?

---

### Post by P4man on 2009-11-07
sounds like alsa crashed or istnt working.
Does it happen after a fresh boot?

Can you post the output

```
aplay -l
```

and

```
dmesg
```

---

### Post by Athropos on 2009-11-07
I have a similar problem : Sound is working but I cannot set it using gnome-volume-control. I get "Waiting for sound system to respond" from the GUI, and "connection failed" from a terminal.

I found alsamixergui to work properly, even though it's not the sexiest program I've seen in my life. So maybe your sound is working but is just mute or set to a very low volume. If gnome-volume-control doesn't work, just try alsamixergui...

---

### Post by riebling on 2009-11-07
Same problem here.  Lost volume control, get "waiting for sound system".  alsamixergui looks hideous - is this really the best volume control there is?  I liked it much better before this 'upgrade' :(

---

### Post by Athropos on 2009-11-07
> **riebling said:**
> Same problem here.  Lost volume control, get "waiting for sound system".  alsamixergui looks hideous - is this really the best volume control there is?  I liked it much better before this 'upgrade' :(

You can also use gnome-alsamixer, at least it's GTK2.

---

### Post by ricardo.gloe on 2009-11-07
uninstalled Pulseaudio and installed esound, following advice from friend and got the sound back. But still couldn't recover the volume icon in the tray. Installed gnome alsa mixer so i could change the volume level, but can't get the icon to load in the tray.

---

### Post by riebling on 2009-11-07
Worst ubuntu audio nightmare, ever.  And I spent months in ubuntu audio hell trying to finally get PCM output working - which it was up until upgrading to Karmic Koala :(

---

### Post by Unitas on 2009-11-08
Same problems here. Pulseaudio has given nothing but problems for me since I started using ubuntu with Intrepid. In Karmic the sound was lagged, if it even played at all. And when it did play it couldn't decide if it wanted to play through the left or right channel, rarely both. 

Rhythmbox threw errors when trying to play an mp3, but other players worked. Games in wine had no sound.

Uninstalled Pusleaudio like I've done every other install/upgrade and sound is back and working fine. Except this time I lost my mixer and volume tray icon. Had I seen this coming I wouldn't have upgraded. Perhaps it is partly my fault for not researching enough first.

I hope they fix this soon, and do away with pulseaudio once and for all. Alsa has been by far the most compatible and most reliable.

---

### Post by P4man on 2009-11-08
Pulse doesnt replace alsa, it sits on top of alsa and isnt going away any time soon if ever. If it works (and it does for me and most) its flexibility is actually quite nice.

Anyway I would suggest you open a bug report on launchpad, thats your best bet for getting this fixed IMHO.

---

### Post by Guell on 2009-11-08
This solved it for me:
[http://ubuntuforums.org/showthread.php?t=1308237&highlight=pluseaudio](http://ubuntuforums.org/showthread.php?t=1308237&highlight=pluseaudio)

Turns out pulseaudio couldn't access the audio server because karmic changed rights on my homefolder.

---

### Post by MeduZa on 2009-11-09
same problem here, after a clean install of koala, I removed pulseaudio, after that, I can't get the icon to load in the tray, but I have sound, also I get the message "Waiting for sound system to respond"

EDIT: I found this on google:

[http://www.damonkohler.com/2009/11/koala-missing-volume-control.html]("http://www.damonkohler.com/2009/11/koala-missing-volume-control.html")

---

### Post by Unitas on 2009-11-09
I reinstalled pulseaudio to experiment with to see if I could get everything reconciled.

I reset the permissions on my home folder to my username and group myusername as was suggested earlier, didn't help. I also tried setting group to admin, pulse, and pulse-access. I even added my account to the pulse and pulse-access groups with no luck.

For rhythmbox I applied the fix listed here by KoalaAirlines: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/442157](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/442157) with success.

However there was no sound in wine. I didn't try any JACK programs like Ardour/Rosegarden/Linuxsampler, etc.

There may be indiviual fixes for programs to use pulseaudio, but since uninstalling pulseaudio makes everything work out of the box that tells me the bugs lie with PA.

-------------------------

About gnome-volume-control, I was getting errors "shm () read-only file system" or somesuch. So I edited fstab to mount /dev/shm as rw instead of ro, and remounted /dev/shm. 

It didn't work, but now the error is "connection failed, reconnecting..."

I also found a different gui alsa mixer called gamix. It's more attractive but still no tray icon.

A way to get a volume control is through avant window manager. Not a tray icon per se, but it works.

EDIT: I tried the fix suggested by Meduza, deleting ~/.pulse. Tried to run gnome-volume-control and its applet, it just created a new ~/.pulse directory and gave the same errors.

---

### Post by TomtheWombat on 2009-11-10
I had a file in my home directory called '/home/username/.pulse-cookie' that was owned by root and write protected.

I did 'sudo rm ~/.pulse-cookie' and everything started working instantly.

---

### Post by Unitas on 2009-11-12
Ok I got it all working correctly with pulseaudio running. I found the fix here from OliW: [http://ubuntuforums.org/archive/index.php/t-1222230.html](http://ubuntuforums.org/archive/index.php/t-1222230.html)

But the package he says to extract libasound_module_pcm_pulse.so is not the 32bit alsa-utils but the 32bit libasound2-plugins package.

The process is still the same though, extract and copy libasound_module_pcm_pulse.so from the 32bit libasound2-plugins package to /usr/lib32/alsa-lib directory and reboot.

I now have sound in wine apps using pulseaudio, also i was experiencing a mic input issue without pulseaudio which is now fixed as well.

Here's the link to the 32bit libasound2-plugins package for Karmic:

[http://packages.ubuntu.com/karmic/libasound2-plugins](http://packages.ubuntu.com/karmic/libasound2-plugins)

---

### Post by Zexium on 2009-11-12
After Karmic, I had:

1. No sound in firefox java or flash applets
2. horrendous constant wah-wah-wah-wah type effect on streamed audio (all formats and sources I tried)
3. popping speakers every time a sound was played

Removed pulseaudio, now I have:

1. No volume control (using gnome alsamixer)
2. No sound in firefox java applets.

Not the first time I've had trouble with pulseaudio after an upgrade, but certainly the worst experience so far :(

Zex

---

### Post by Rat2000 on 2009-11-14
> **TomtheWombat said:**
> I had a file in my home directory called '/home/username/.pulse-cookie' that was owned by root and write protected.

I did 'sudo rm ~/.pulse-cookie' and everything started working instantly.

Many thanks, that worked for me as well!

---

### Post by poe9514 on 2009-12-08
Nothing but problems since Karmic.  I've had all sorts of sound problems: choppy sound in VLC, sporadically no sound in flash, mpd freezing/crashing, etc.  I've tried completely re-installing everything sound-related, I've tried just using alsa, tried configuring any and everything, all to no avail.

Right now I have pulse running, but I need to run 'alsa force-reload' every reboot or volume control won't work.  No two applications can use sound at one time.  Everything is pointed to the pulse sink.  I have no system/preferences/sound, but I have gnome-volume-manager.

I had everything working this morning with just alsa, but gnome-volume-control refused to control my volume.

Any suggestions?  I'm *this* close to reverting to Jaunty.

---

