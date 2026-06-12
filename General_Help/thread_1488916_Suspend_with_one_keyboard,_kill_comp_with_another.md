---
title: "Suspend with one keyboard, kill comp with another"
date: 2010-05-20
forum: General Help
---

### Post by x-shaney-x on 2010-05-20
I have always had the little moon hotkey thing on my keyboard (presumably sleep/suspend) mapped to lock screen as a keyboard shortcut since I have never used suspend/hibernate etc (I don't even know the difference between suspend/sleep/hibernate).

Well after installing Lucid I pressed the moon key but realised I had forgotten to set it to lock screen and the computer kind of shutdown and was making no noise but the power button was pulsing on and off.  I assume this is suspend.
I pressed the button and after a short while my desktop loaded up with all the previous apps in the same state as when I pressed the button.

I thought this was pretty neat so I have left the button as it is and have been using this feature.

After recently switching from my old cable keyboard I am now using a wireless deskset but find whenever I press the moon button on this one the screen goes black but the comp is still making noise and doesn't power down or anything.
Unfortunately, nothing gets my desktop back, it's like the whole comp has frozen up completely.
Alt,Ctrl,Del does nothing, pressing the power button does nothing, pressing the moon button does nothing and not even the SysRq thing does anything.
I have to hold down the power button and do a hard shutdown.

---

### Post by tgalati4 on 2010-05-20
Depending on your wireless keyboard (bluetooth or RF-dongle) you need to load and unload the driver for that wireless device.  Search the forums for how to do that in Lucid.  Normally it would be in /etc/default/acpi-support but I think it has changed.

So suspend works for you with a wired keyboard.  But when you use the wireless, suspend doesn't reinitialize the keyboard so you have know way to wake the computer.  If you have a wired or USB mouse, you might look in the BIOS and set a power setting:  "Allow USB devices to wake".

Also use acpitool to keep the certain parts of the computer alive, like your keyboard:

Open a terminal:

sudo apt-get install acpitool
man acpitool
acpitool -w

Of course, your wireless keyboard may go to sleep and the linux driver doesn't know how to handle that gracefully after waking from suspend state.

---

### Post by x-shaney-x on 2010-05-20
Well that certainly made sense.
I added the driver to acpi-support and after rebooting tried again.
Exactly the same thing happened.  I did notice that when it went into suspend, the light on my mouse/keyboard (RF) receiver turned off.
When I touched the keyboard it did light up again to suggest that there is no problem there.

My concern is more that the behaviour is different. The change of keyboard may just be coincidence but before the computer did basically appear to shutdown and made hardly any noise and the power button was pulsing as I said.
Now all that happens is the display goes and there is a noise that sounds exactly like the noise it makes at the point of shutdown when the power goes off except it doesn't and all the fans are still going etc.

---

### Post by tgalati4 on 2010-05-20
There are different levels of suspend.  It's possible that something is preventing it from going to sleep (fan off, hard drive spun down, but RAM has power).

man pm-suspend

You will have to dig into more details.

dmesg | more

Look for sleep/suspend errors and post them.

It's also possible that the driver is broken.  It's a good sign that the receiver dongle wakes when you hit a few keys, but if the kernel doesn't do something to respond then you have no keyboard.

I presume you did a google search on your driver to see what other switches are available.

---

### Post by x-shaney-x on 2010-05-21
I have been unable to find any suspend errors anywhere.
In fact, I looked the pm-suspend.log and compared the entries for the old ps/2 keyboard with the new usb/wireless one and the ONLY difference was in the modules list, with the new keyboard and mouse replacing the old entries.

All other messages are identical and it seems as far as the log is concerned it IS suspending successfully with the wireless keyboard.

I have tried the old keyboard again and these are the (noticeable) steps:

ps:  screen shuts off, a couple of seconds later the had drive shuts down/spins down followed quickly by the fans shutting off and silence. 
The power button is pulsing on and off.  A quick press of the power button wakes everything up and I carry on where I left off.

usb:  screen shuts off, a couple of seconds later the hard drive shuts down/spins down and that's it. Fans still going, power light still solid bright blue and I am unable to do anything other than hold the power button til it powers off completely.

I should also point out that the usb keyboard not waking anything up in itself isn't an issue.  I would rather the keyboard DIDN'T wake it up as I have two children around the house and it wouldn't stay suspended for long.

---

### Post by x-shaney-x on 2010-05-21
Just to add, googling has pointed me to a lot of threads regarding similar suspend problems with logitech usb keyboards/mouse sets on Windows so it does seem to be an issue with Logitech though I haven't managed to find any specific problems with Logitech stuff on linux.

---

### Post by tgalati4 on 2010-05-21
Open a terminal, post the output of:

acpitool -w

What may be happening is that the USB bus stays alive during sleep and since the motherboard still has power for the USB, the motherboard fan continues to run.  Then it could be the hardware itself or the RF-receiver/keyboard driver that doesn't properly reinitialize.  

I presume that both keyboards can be connected and work properly with your system?

If so then leave the wired keyboard connected. 

Remove the wireless keyboard module; open a terminal:

sudo modprobe -r yourwirelesskeyboarddrivername

sudo pm-suspend

Wake with the wired keyboard; verify that the system is working properly.

sudo modprobe yourwirelesskeyboardrivername

Verify that the wireless keyboard now works.

If this manual procedure works, then you can add these commands (without the sudo) to the pm-suspend script.

---

### Post by x-shaney-x on 2010-05-21
```
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. HUB0      S5     disabled  pci:0000:00:10.0
  2. XVRA      S5     disabled  pci:0000:00:04.0
  3. XVRB      S5     disabled  
  4. XVRC      S5     disabled  pci:0000:00:02.0
  5. USB0      S3     disabled  pci:0000:00:0b.0
  6. USB2      S3     disabled  pci:0000:00:0b.1
  7. AZAD      S5     disabled  pci:0000:00:10.1
  8. MMAC      S5     disabled  pci:0000:00:14.0
  9. MMCI      S5     disabled  
  10. PS2M      S4     disabled  pnp:00:07
  11. PS2K      S4     disabled  pnp:00:08
```

Tried your suggestion.
Removed the module which killed both the wireless keyboard and mouse.
Suspended and it still didn't fully suspend.

So next boot I tried unplugging the receiver itself (with wired keyboard still attached) and STILL didn't fully suspend.

Booted up again with the wired keyboard and left the wireless receiver unplugged:
suspended fully with no problems.

So the usb/wireless keyboard is certainly the problem but it seems something is loaded along with the modules that will not unload.

I have lsmod'd and scoured the logs again and only hid, usbhid and hid_logitech come up with the usb keyboard.  I tried removing all those and still won't suspend properly.

---

### Post by x-shaney-x on 2010-05-21
AHA!  Success!
This is semi-solved now.

Thanks to tgalati4 for pointing me in the right direction.
Yet another inspection of the logs threw up another module, "ff_memless" which was always listed with hid_logitech.
I had previously ignored it because it also came up when the usb keyboard wasn't attached.
When I inspected more closely, I noticed ff_memless had a 1 in the "Used by" column when the usb keyboard was attached and a 0 when using the wired one.
So I tried rmmod-ing ff_memless and it finally suspended fully.
I have since added it to pm-suspend along with the logitech module and suspend is working normally with the usb keyboard (without the cabled one attached) and it is also waking up fully and the keyboard working.

So the next question, does anyone know the "correct" place for this ff_memless module to go?
Adding it to to the actual suspend script doesn't seem ideal.

---

### Post by tgalati4 on 2010-05-21
So what you are saying is if you add ff_memless to /etc/default/acpi-support it works properly?

acpi-support has a place for loading/unloading modules for suspend purposes.  You could leave the logitech modules in memory, perhaps only the ff_memless needs unloading.

---

### Post by x-shaney-x on 2010-05-21
No, /etc/default/acpi-support does nothing.  Can't remember which file I saw it in but acpi-support isn't being used, it is pm-utils.

Adding modprobe -r ff_memless hid_logitech to /usr/sbin/pm-suspend works.
I added the line to remove the modules at the end of the suspend routine and to re-add them after the wake-up routine but like I said, not ideal.

(Incidentally, I have to remove both modules. ff_memless won't unload directly because it is being used by hid_logitech so that has to go first).

After poking around my PCLinuxOS install, it seems the correct way to flag modules for suspend is by adding a file in /etc/pm/config.d.

In ubuntu the directory is empty but PCLOS has a file called ndiswrapper with the entry ```
SUSPEND_MODULES="ndiswrapper"
```
So I added a file called logitech with the entry: ```
SUSPEND_MODULES="hid_logitech ff_memless"
```
Unfortunately, this didn't work on either ubuntu or PCLOS.

---

### Post by x-shaney-x on 2010-05-21
Urgh! Seems I spoke too soon.
I assumed it was the modprobe lines in /usr/sbin/pm-suspend but I have re-added them again to check and it's still not suspending.

So right back to square one again.

So to sum up so far...
I can only fully suspend if I manually unload the hid_logitech and ff_memless modules.
So now I need to find a way to automate it.

---

### Post by tgalati4 on 2010-05-21
You would have to trace the logic in pm-suspend to see where it calls the config.d scripts.  It's OK to modify pm-suspend, just keep a backup in case it gets upgraded.  I presume the /etc/pm config files replace /etc/default/acpi-support but I don't know the the appropriate entries.  You will have to keep digging.  It sounds like you are close.

---

### Post by x-shaney-x on 2010-05-22
<sigh> I thought my days of fiddling around like this to get something working were gone.

So going back to the logs I notice that the file I added to /etc/pm/config.d IS being read.
Unfortunately, it still isn't helping.

With the entry ```
SUSPEND_MODULES=hid_logitech ff_memless 
```The log says ```
/etc/pm/config.d/10_logitech: 1: ff_memless: not found
success
```If I reverse the order in the config file so that memless is listed first the log reports that hid_logitech can't be found.

If I just put one or the other, there is nothing about the file in the logs at all.
I also tried creating two files, each one having one of the above entries but again no mention in the logfile and still not working.

I feel like I'm getting nowhere with this.
Looks like I have to make a choice:
wireless keyboard but lose the suspend feature 
or
wired keyboard, get my suspend back but have to put up with knotted cables

---

### Post by tgalati4 on 2010-05-22
Well, you are getting closer.  Keep the faith.  As long as you use Linux and update it and add hardware to it, you will need to chasing the config files.  This is known as "configuration file hell".  The alternative is to drop hardware the way Windows does.  Try getting an old SCSI scanner to work under Vista/Win7.

At least in Linux, after some fiddling, you can still use your old scanner.

ff_memless may actually be ff-memless.  The filename and the module name are sometimes different.  Similarly hid_logitech may actually be hid-logitech.  There are technical reasons for this.  I just don't know what they are.

locate memless
locate logitech

tgalati4@tpad-Gloria7 ~ $ locate logitech
/lib/modules/2.6.28-11-generic/kernel/drivers/hid/hid-logitech.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/hid/hid-logitech.ko
/lib/modules/2.6.28-16-generic/kernel/drivers/hid/hid-logitech.ko
/lib/modules/2.6.28-18-generic/kernel/drivers/hid/hid-logitech.ko

tgalati4@tpad-Gloria7 ~ $ locate memless
/lib/modules/2.6.28-11-generic/kernel/drivers/input/ff-memless.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/input/ff-memless.ko
/lib/modules/2.6.28-16-generic/kernel/drivers/input/ff-memless.ko
/lib/modules/2.6.28-18-generic/kernel/drivers/input/ff-memless.ko
/usr/src/linux-headers-2.6.28-11-generic/include/config/input/ff/memless.h
/usr/src/linux-headers-2.6.28-16-generic/include/config/input/ff/memless.h
/usr/src/linux-headers-2.6.28-18-generic/include/config/input/ff/memless.h

So I would try:

SUSPEND_MODULES="hid-logitech ff-memless"


SUSPEND_MODULES="hid-logitech, ff-memless"

I'm not sure how the module names are parsed in this script.

---

### Post by x-shaney-x on 2010-05-22
I think that was my last hope but still no luck.

Strangely, all my googling has pointed me to people reporting problems with usb keyboards not working after wake up.
I have only found ONE other case that sounded identical to mine, unfortunately that person had no answer either.

---

### Post by x-shaney-x on 2010-05-22
Well I have technically found a solution.
I checked the BIOS again and tried changing the USB Legacy Mode Support option.
By default it was set to Auto so I switched it to Disabled and found suspend was working perfectly with the USB keyboard.
I deleted any files I had created and reverted any I had edited to make sure and it successfully suspended several times in a row with no problems.

No problems that was until I tried to boot into a different linux at grub.
With the BIOS option disabled I am unable to use my keyboard at all until AFTER the OS kernel is loaded.

Tried setting it to Enabled, just in case it was the Auto option itself messing things but I have lost suspend again.

Thwarted again. Really thought I had it solved for a moment there.

---

### Post by tgalati4 on 2010-05-22
Well you learned how legacy USB support works.  What is the version of Linux that does not work?  What is the kernel of that distro?

uname -a

Of course if you stuck with Windows you wouldn't have all these problems.:-$

---

### Post by x-shaney-x on 2010-05-23
Ubuntu Lucid - 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

Though I get the exact same USB keyboard/suspend problem on: 
Mint 9/Ubuntu Maverick
PCLinuxOS
Latest Mandriva One beta
Debian Testing

---

### Post by tgalati4 on 2010-05-23
I would file a bug against the current kernel since none of the recent distros work with this wireless keyboard.  Suspend/Wake has always been a moving target in linux because of the non-standard ACPI implementations and the large variety of hardware that needs it be reinitialized in able to work after resume.  Reference this thread in your bug submission.

Keep your wired keyboard in the meantime.

---

