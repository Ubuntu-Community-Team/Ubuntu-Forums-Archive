---
title: "Two finger scrolling?"
date: 2009-09-27
forum: General Help
---

### Post by GnarMachine on 2009-09-27
So after some research it looks like two finger scrolling can be enabled for laptops with synaptics trackpads. I installed gsynaptics on my sony vaio VGN-T27GP (also known as T270P), but there is no device for the trackpad in my xorg.conf file. This leads me to believe my laptop doesn't use a synaptics trackpad, and sony makes no mention of what it could be other than that.

Is there any way to get two finger scrolling on this machine? 

Thanks for any help or input.

---

### Post by ram2500 on 2009-09-28
I have a Dell laptop at work that (supposedly) permits scrolling...it even has the markings to scroll up and down and sideways on the touchpad. Doesn't work at all (this machine has Vista Business w/ drivers). So, it's definitely a driver issue, I suppose. If your laptop came with Windows, and it still has Windows on it, does it work in Windows? 

I just simply use a USB optical mouse with laptops anyways...I am still not 100% comfortable with touchpads, and I've used laptops a very LONG time, like back in the Thinkpad 700 series days:).

---

### Post by fluffman86 on 2009-09-28
Not all synaptics trackpads support multi-touch scrolling.  Try searching for the appropriate xorg configuration, and if that doesn't work then you should still be able to scroll using the right side of the touchpad.

---

### Post by GnarMachine on 2009-09-28
> **fluffman86 said:**
> Not all synaptics trackpads support multi-touch scrolling.  Try searching for the appropriate xorg configuration, and if that doesn't work then you should still be able to scroll using the right side of the touchpad.

Should scrolling on the right side simply work or are there some adjustments I need to make? 

I know what the appropriate xorg configurations would be, though I cannot make them as there are no sections in my xorg config that have anything to do with the trackpad. Do I need to manually add the trackpad somehow? I'm thinking it isn't a synaptic device (and I don't know what it is), so I'm not sure how I would add it as a device.

---

### Post by StuartN on 2009-09-28
> **GnarMachine said:**
> Should scrolling on the right side simply work or are there some adjustments I need to make?

In System->Preferences->Mouse, go to the Touchpad tab and enable the scrolling.

---

### Post by GnarMachine on 2009-09-28
> **StuartN said:**
> In System->Preferences->Mouse, go to the Touchpad tab and enable the scrolling.

Thanks a bunch!

I'm going to keep poking around and see if I can get the two finger scrolling to work.

---

### Post by benmoran on 2009-09-28
With Karmic, 2 finger scrolling became available for me. I've got an '07 Dell Inspiron 1501. 

Word of warning!! I also tried out the "disable touchpad while typing" option. I kept getting a weird jerking motion while trying to look around in FPS, and didn't realise what it was until a few weeks later.

---

### Post by mikewhatever on 2009-09-28
I've been using two finger scrolling on an HP with Synaptics touchpad and on a Dell mini 10 either with Synaptics or Elantech, not sure which one. Both just worked out of the box.

---

### Post by Handle on 2009-09-28
I could be wrong, but I don't think you should be editing your xorg.conf (at least not yet). In more recent versions of Ubuntu your devices are loaded dynamically so you don't need to.

The first thing you need to do is determine what type of touchpad you have. From a terminal, type:

```
cat /proc/bus/input/devices | grep Touch
```

That should yeild something. If it doesn't, drop the "| grep Touch" part and read through the output yourself looking for something that might be your touchpad.

Once you know what it is, Google should be able to help.

Edit: I replied to your [post in the Ars forums]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/567002361041"). I check that more frequently, so if you want more help (from me) your best bet would be to reply to that post. As a courtesy, you should add your solution here if you find one.

---

### Post by chiefofthejojos on 2009-10-11
I had the same problem with my touchpad. My touchpad name is "SynPS/2 Synaptics TouchPad" and my laptop is a Lenovo Thinkpad T400. I experimented with the two-finger width and pressure settings and found that leaving the width at 7 and changing the pressure to 40 results in the best two-finger scrolling experience. Now I'm just trying to figure out what to do to keep it working after rebooting.

You can change the pressure with this command:
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 7
```

and change the pressure with this:
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 280
```

change "SynPS/2 Synaptics Touchpad" to the name of your touchpad.  The last number of each command is the value you are testing.  By default the pressure is set to 280, but 40 works very well for my laptop.  I found it easier to test by making a shell script:
```
#!/bin/sh
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 $1 && xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 $2 && xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 0
```
I saved it to a file called "two-fing.sh" and tested values with:
```
./two-fing.sh 7 280
```
where 7 and 280 are the width and pressure values you are testing, respectively.

Bug here:
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/422224?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/422224?comments=all)

Maybe it would be a good idea to publish your width and pressure values there along with the output of "lshal" so someone can add a quirk for your laptop.

---

