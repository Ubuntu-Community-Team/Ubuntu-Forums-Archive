---
title: "Tv Tuner and webcam conflict ?"
date: 2011-01-24
forum: General Help
---

### Post by tominto on 2011-01-24
I've got a simple USB webcam which I would like to use with google video chat, but firefox crashes everytime I try to use it.  I think the problem is a conflict between the webcam and my tv tuner card.  If I go to twestwebcam.com, I get the output of my tv. If I use cheese and select device to open, I see video0 for the tvtuner card, and video01 for the webcam. The webcam works fine in cheese. How can I fix this so google video chat works?  Thanks

---

### Post by davidmohammed on 2011-01-24
suggest, instead of using firefox for your web-chat, use either empathy or pidgin instead.

---

### Post by tominto on 2011-01-24
thanks, but I really would like to use google video chat.

I *think* this might have something to do with udev rules, but the examples I've researched didn't really concern my particular problem.  Am I right?  

"If I go to twestwebcam.com, I get the output of my tv"

Ooops, I meant testwebcam.com

---

### Post by davidmohammed on 2011-01-25
Gmail Settings > Chat > Voice and Video Chat > Camera 

I think you can choose between your camera and webcam there.

---

### Post by tominto on 2011-01-25
Thanks, but as soon as I go to chat in the settings, my browser crashes.  I think gmail is trying to connect to whatever is at video0 which is my tv tuner, and crashes.  I need to rearrange how the webcam and tvtuner are setup up somehow.

---

### Post by davidmohammed on 2011-01-25
hmmm - google brought [this up]("http://ubuntuforums.org/showthread.php?t=295293&page=2") - a bit old - maybe this will lead you into a solution?

---

### Post by meens78 on 2011-08-12
can any one help me in getting fix the problem of tv tuner card is selected in cheese instead of my usb camera and cannot change the device. I uninstalled the adobe flash player also. Not able to do video chat with my daughter

---

### Post by fragos on 2011-08-12
If you have a webcam and a TV card which device will be video0 is up for grabs. You can fix this with udev rules. Create text file /lib/udev/rules.d/51-video.rules and redefine each video device. Here's the one I use:

  KERNEL=="video*", SYSFS{vendor}=="0x109e", SYSFS{device}=="0x036e", SYMLINK+="video/bttv"
  KERNEL=="video*", SYSFS{vendor}=="0x046d", SYSFS{device}=="0x092e", SYMLINK+="video/webcam"

You'll need to determine the values for the devices. If the device is USB like a webcam, run lsusb in a terminal window. The values for ID were what I was looking for. My lsusb output was:

  Bus 005 Device 002: ID **046d:092e** Logitech, Inc. QuickCam Chat

If you need the vendor and device of a PCI card you can install "hwinfo" and run it in a terminal. There's a lot of output but your card will be in there. The info you want is on the "Vendor:" and "Device:" lines. For my TV card the output was:

  33: PCI 107.0: 11200 TV Card
  [Created at pci.318]
  Unique ID: 2_DJ.jkuH1hutKMA
  Parent ID: 8otl.vpWef0P80d9
  SysFS ID: /devices/pci0000:00/0000:00:04.0/0000:01:07.0
  SysFS BusID: 0000:01:07.0
  Hardware Class: tv card
  Model: "Hauppauge computer works Hauppauge WinTV"
  Vendor: pci **0x109e** "Brooktree Corporation"
  Device: pci **0x036e** "Bt878"
  ...

My video card will also be known as /dev/video/bttv and my web cam as /dev/video/webcam and I can use to configure tvtime, cheese or whatever video ap you're using.

---

