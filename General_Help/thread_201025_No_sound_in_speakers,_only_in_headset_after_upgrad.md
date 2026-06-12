---
title: "No sound in speakers, only in headset after upgrade?"
date: 2006-06-21
forum: General Help
---

### Post by annazack on 2006-06-21
Hi,
I just upgraded my Breezy to Dapper and before I could listen to mp3:s using the speakers and at the same time have a headset plugged in in order to skype (no music in the headset). 

Now, after the upgrade (and a lot of work) I finally got Skype to work with the headset but my music comes out via the headset and not the speakers. 

I've tried changning all the things in the volume control but to no use...

If anyone have any hints I appreciate it!

//Anna

PS. I need hints for dummies to be honest...DS.

---

### Post by soze on 2006-06-21
Check out [this ]("http://ubuntuforums.org/showthread.php?t=192316")thread.

---

### Post by annazack on 2006-06-22
Thanks for the link but I only have one soundcard...and it did work in Breezy Badger?

Also, if someone out there has a solution, please keep the advice or instructions detailed and straigthforward since I am not the most experienced Linux-user.

//Anna

---

### Post by annazack on 2006-07-11
Anyone?

---

### Post by dolphinholmer on 2006-10-30
Try this.
From a Terminal type:

sudo gedit /etc/modprobe.d/usb-headset
In the blank file add these lines:

# Set usb headset as second device
options snd_usb_audio index=1

Save the file and reboot.
Advice taken from [https://help.ubuntu.com/community/PlantronicsUSBHeadsetControls](https://help.ubuntu.com/community/PlantronicsUSBHeadsetControls)

---

