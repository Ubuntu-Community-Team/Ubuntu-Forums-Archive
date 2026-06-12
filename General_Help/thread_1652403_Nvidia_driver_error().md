---
title: "Nvidia driver error(?)"
date: 2010-12-24
forum: General Help
---

### Post by singerj on 2010-12-24
Hi.

Today, I decided to boot up my computer, as I normally do every day. Unfortunately, I ran into a problem with no obvious (to me, at least) cause, taking the form of the following error during Ubuntu's boot:

```
Ubuntu is running in low-graphics mode

The following error as encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:    system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.
```

in a window with an "OK" button in the lower-righthand corner.

I've tried googling for possible solutions, all of which require being able to log in via terminal or similar. Unfortunately, I also have a different problem; none of my input devices (1 usb keyboard, 1 ps/2 keyboard, 1 usb mouse) work. There's simply no response from moving/clicking the mouse, or any keystrokes from the keyboards.

Additionally, I've tried booting in recovery mode, which... isn't much more help. Every time it just hangs at some point, and just stops. Again, no keyboard response.

With my usb keyboard plugged in (Logitech G15), it hangs at one of the two following messages (at random, seemingly):

[    2.317726] generic-usb 0003:046D:C222.0004: input.hiddev97,hidraw3, USB HID v.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:1a.-2.4/input0

or

[    2.245920] usb 3-2.4: configuration #1 chosen from 1 choice

If I unplug the usb keyboard, it hangs consistently at this message (even after letting it run for extended periods of time):

[    3.175799] Adding 4883720k swap on /dev/sda6. Priority:-1 extents:1 across:4883720k

I'm using Ubuntu 10.04, with the 2.6.32-26-generic kernel (though the same errors occur selecting earlier kernels). The whole issue is quite vexing, and I'm not really sure where to go from here, since I can't actually complete the boot sequence to get to the point of logging in or doing, well, anything.

A preemptive "thank you" for any of you willing to offer help. :)

---

### Post by theasprint on 2010-12-24
Hi,

As my signature suggests, I can help.

So I would like to know if you've installed any nvidia drivers?
I assume that you do, and you got it from System> Administration> Hardware Drivers. This Nvidia driver should then be provided from Ubuntu and not Nvidia itself.

About solving the graphics problem I definitely can help.
But yes, you may have guessed right, I still require a terminal, or at least something that can give Input to the PC.

Perhaps you can try this to break the deadlock.
Upon getting the Grub screen, (it seems you did go through) while selecting your kernel (the latest one i suppose), then press "e" to go for advanced options (I hope you can press it)

Under there there are like a bunch of words.
Find "quiet splash" and REPLACE it with "nomodeset" (removing the quotes)
That means quiet splash is gone and nomodeset is in their place.

Then press Ctrl+X to boot.

Tell us the results.

Hope this works.

Good Luck :D

---

### Post by singerj on 2010-12-24
Your assumptions re: installed drivers is correct.

I do have input from my ps/2 keyboard when navigating GRUB, and I've tried your boot suggestion, and it ended up in the same place, with the aforementioned error window and lack of working input devices. The baffling thing (to me) is that the messages displayed during boot up seem to indicate the usb devices have been initialized (and my G15 receives power/the screen turns on, etc.), but none of the input works. No luck. :/

---

### Post by singerj on 2010-12-24
I'm not sure if double posting is frowned upon here (apologies if it is), but I -am- able to successfully boot into ubuntu using a live cd. Is there any way I can access my actual install from here to try fixing stuff?

EDIT: Alternatively, is it possible to install 10.10 over 10.04 from a boot disk without wiping my data? I'd imagine this wouldn't exactly be the most ideal option, and might not work/might just invite more problems but as a last ditch effort... idk. :/

---

### Post by theasprint on 2010-12-24
Hi,

About the wiping thing, if you really want to do it, you should change the name of this thread (I don't know if its possible) or remake another one.

Er, to give you a headstart.
If you remember having 3 partitions in Ubuntu, which is the root, /home partition and swap, then your data will not be gone. 
But if you don't, I'm sorry.
Unless you want to extract it first?

* There's a guide from kansasnoob on how to retrieve data before upgrading Ubuntu. I can't really find it but he did some effort in also explaining the Disadvantages of 10.10 [http://ubuntuforums.org/showthread.php?t=1622388]("http://ubuntuforums.org/showthread.php?t=1622388") so that blur people would not get f**ked up with the installation.

For what i think, you may want to start another thread on extracting your data out.

---

### Post by singerj on 2010-12-24
Well, if possible, I'd still like to figure out a way to fix the problem without upgrading, especially since that's not a guaranteed fix (even if I can do it and preserve my data). That'd really be a last-ditch effort, and is really only an idle thought at the moment.

---

### Post by theasprint on 2010-12-24
Hi,

I really don't know how to solve your problem now but I still can give some help.

Can your PC boot from the LiveCD?
Just boot from the LiveCD (Try Ubuntu without Changes) and then play around with the keyboard, mouse etc 

And in the meantime, while in the LiveCD, would you mind going to nvidia.com and then download the driver for your graphics card? 
Then transfer the driver file into your PC (because you are not accessing your HDD while in LiveCD mode)
I think you would need to mount your HDD, and then copy the file into somewhere like your desktop.

Here, something like what I want this guy to do:
[http://ubuntuforums.org/showthread.php?t=1652119]("http://ubuntuforums.org/showthread.php?t=1652119")

I really hope that your keyboard can work.

Are you sure that there is no command line thing in the low-graphics mode?
Because I assume that in low-graphics mode, basic terminal commanding should be able to be carried out.

For now test the LiveCD first and get your Nvidia driver from nvidia.com

* If your PC is unable to use its keyboard and mouse even in LiveCD mode, then I may conclude that your PC is incompatible with Ubuntu.

Good Luck :D

---

