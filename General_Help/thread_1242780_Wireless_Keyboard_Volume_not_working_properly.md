---
title: "Wireless Keyboard Volume not working properly"
date: 2009-08-17
forum: General Help
---

### Post by ciaopaulo on 2009-08-17
Hi,

I have a wireless USB Logitech LX710 keyboard and mouse. I've noticed that the volume up and down keys don't quite work right. (Although mute does)

When I press the keys I get no change in volume, but the lovely GUI does appear to show that the volume *should* be changing in that direction!

After searching around I launched Alsamixer from terminal. It shows the same thing as the GUI, Master volume is fixed at 83% until a mute point is reached. Then the volume is muted.

Any ideas? I'm running latest Jaunty.

Ta,

Paul

Edit: Fixed: [http://ubuntuforums.org/showpost.php?p=7888711&postcount=7](http://ubuntuforums.org/showpost.php?p=7888711&postcount=7)

---

### Post by ciaopaulo on 2009-08-28
Anyone?

Possibly related...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/321740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/321740)

---

### Post by bchurchill on 2009-08-28
I'm not on Ubuntu at the moment, but look in the System menu, and somewhere there's a sound config GUI besides Volume Control that allows you to change how those sound buttons affect the mixer.  Make sure that they are attached to 'Master' and are enabled.

Do you have another keyboard to test with?  If other keyboards do the same things it's more likely an Ubuntu/ALSA/gnome issue, but if it's just this one, you might be out of luck.  Check your keymap to make sure it's right.

---

### Post by ciaopaulo on 2009-08-29
Hi bchurchill, any idea what that app is called?

I tried to find one that would perform that fucntion but couldn't see it. 'Course there's so many to choose from...

I don't have another keyboard to test with atm.

---

### Post by ciaopaulo on 2009-09-02
Here's what I'm seeing:

This pretty graphic appears when I press the volume keys... unfortunately the "steps" have no effect apart from the zero level, which mutes the volume.

[IMG]http://i25.tinypic.com/11v6snb.png[/IMG]

This graphic appears if I click on the volume icon at the top and then click "Volume Control"...


[IMG]http://i30.tinypic.com/2n7p076.png[/IMG]


Manually sliding the volume up and down via this control works fine. Similarly, launching alsamixer confirms this volume slider controls the master volume.

So there appear to be two programs running. The one interpreting wireless keypresses is the duffer.

---

### Post by bchurchill on 2009-09-02
Sorry it's taken me a while to reply.  The program I was talking about is the utility in System->Preferences->Sound.  At the bottom it says "Default Mixer Tracks" and below that there's a mixer device and several tracks to choose from that affect what the keyboard does.

Try several settings to see what works.  For me I use the track 'Master' and my default sound device.

It sounds to me like the keystrokes are being recognized (since you're seeing *something* come up on the screen.  So it's not a problem with the keyboard driver/software.  Since ALSA seems to be working fine, I'm guessing this is a gnome issue (so hopefully the above fix will work)

If you can't get it to work then I highly encourage you to borrow another keyboard to see if it has the same issue.  If it has problems then we'll know for sure that this is a gnome (maybe hal) issue.  

Another thing you can try is unplugging and plugging back in your wireless adapter (I assume it's usb) and then running 'dmesg' from a terminal and posting the end of the output.  This will indicate if there's a hardware problem.

---

### Post by ciaopaulo on 2009-09-02
Ah ha!

Under System->Preferences->Sound...

It seemed to have been set to "Master Capture"

If I change it to "Master" then it works correctly, and uses the default 6% increase as programmed under Config.

How bizarre! Anyway, chalk this one as FIXED. Thanks bchurchill!

:KS:KS:KS

---

