---
title: "Latest spree of automatic updates ruins Dapper"
date: 2006-06-15
forum: General Help
---

### Post by keithjr on 2006-06-15
Okay, so that little software update icon was lighting up again earlier this afternoon.  When I clicked it, I saw there were dozens of things to be upgraded, which always makes me a little nervous.

My apprehension, as it turns out, was well deserved... After automatically applying all the updates it wanted, and restarting as suggested, I found my computer to be a shadow of its former self:  flash no longer plays sound, my fglrxinfo now says I don't have a 3d card once again, the sensors I spent a week trying to configure are no longer detected... I'm sure there's more that I haven't uncovered yet.

Really, these things shouldn't happen because of a simple update.  And if they must, there should at least be a disclaimer or something.  "Warning, applying these updates takes away any customization you've applied up to this point."

---

### Post by Slicedbread on 2006-06-15
Try booting back into the old kernel. It seems to have broke more peoples' setup than fix them.

---

### Post by pRedat0r on 2006-06-15
just from my experience, throughout the Flights and into final, every time there is an update to the kernel, fglrx accelleration breaks.  Every time, I have to go into text mode and follow the guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

However, prior to doing that, I usually uninstall xorg-driver-fglrx (even if it is updated to the newest version), then I install the newest linux-restricted-modules-$(uname -r), then reinstall xorg-driver-fglrx.  You shouldnt need to do the aticonfig stuff if you are just doing this to get it working after an update though..  The depmod -a step is new, but im sure it cant hurt..

All of this is assuming you arent installing ati drivers yourself (not provided by ubuntu repos), if so there is a different step you would need to follow.

As an ati owner, you'll learn to do this in your sleep..  I do wish there was a way that the updates could automate this process though -- it seems like it could check if you have the previous restricted modules, and install the new ones before going on to fglrx..

I do agree though, updates really shouldnt cause your system to hang or other large problems that a lot of people are facing.  I simply had xgl installed -- but not running (couldnt get it working), and gdm was bombing after the update..  seems like something not running shouldnt affect the stock programs..

just my 2cents.  If you need help getting anything going just let me know and id be happy to attempt to help if you get stuck!

---

### Post by Slicedbread on 2006-06-15
Its strange though, I downloaded all the updates kernel +fglrx and nothing broke- acceleration, xgl, and everything else was just the same as before.

---

### Post by kvonb on 2006-06-15
I know that this doesn't help your situation, and I would be extremely angry in your situation, but if you are using the non-ubuntu provided graphics drivers you should have seen the disclaimer on the install instructions warning you that kernel updates would require you to re-compile the proprietory driver module!

Find the instructions you used to install it in the first place and do the whole thing again.

Once you have fixed it, go into Synaptic and lock the kernel and restricted modules, that should help in the future.

Best of luck, regards,

Kev :)

---

### Post by Fallom on 2006-06-15
[QUOTE=Slicedbread]Its strange though, I downloaded all the updates kernel +fglrx and nothing broke- acceleration, xgl, and everything else was just the same as before.[/QUOTE]

Yeah I was surprised when the update to fglrx didn't break anything for me. Usually I'm not so lucky.

---

### Post by jetpeach on 2006-06-15
yep, my flash sound got r*ped as well.. arg.

---

### Post by kvonb on 2006-06-15
Just did ALL the updates and the only thing that broke for me is automatic login, it asks me for a password on a black screen with an old crusty looking password box!

Oh well, it will give me something to do for the next week or so :rolleyes:

---

### Post by ampes on 2006-06-16
I dont have any problems at first,but when I restart gdm,ATI driver reverted back to MESA..The only way to enable fglrx is to to make full reboot and same as kvonb,automatic login screen only show black screen and asking for password...

C'mon..I am just enjoying my first Ubuntu for 2 weeks..dont push me back to M$..scary...

---

### Post by Adramelech on 2006-06-16
When u read the guide about installing ur video card on ubuntu it says you have to do it again everytime you update your kernell.

Is the price to update your system, M$ hide security holes and stuff to avoid patches, so the updates are good even if you have to reinstall your video card.

I have learned with time to do it in less than a minute =).

---

### Post by keithjr on 2006-06-16
Thanks for the responses guys.  I already knew how to fix fglrx, was just wondering if anybody else had been having the same issues.

Regarding the flash sound, there is already a thread addressing it.  Seems that if you have multiple devices, the new flash doesn't listen to the OS when it picks which one it should use for output.
[http://www.ubuntuforums.org/showthread.php?t=138297](http://www.ubuntuforums.org/showthread.php?t=138297)

---

