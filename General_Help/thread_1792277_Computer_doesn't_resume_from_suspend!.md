---
title: "Computer doesn't resume from suspend!"
date: 2011-06-28
forum: General Help
---

### Post by gnome1919 on 2011-06-28
Hi guys,
I have this annoying problem in Ubuntu 11.04; when I suspend the system (choosing "Suspend" from power button on top right corner of desktop) everything goes well, but when I try to resume, the system starts on but the monitor stays in standby mode, nothing works and I should hard reset the system! I have searched for this issue on the net and it seems that many people have problem with suspend/hibernate in Ubuntu 11.04. I tried some of the solutions but no chance. Please help me
System Properties:
CPU: AMD Athlon 7750 Dual-Core Black Edition
Mainboard SB: AMD 780G (ATI 3200HD - Proprietary driver installed) 
RAM: 2GB

Thanks in advance.

---

### Post by gnome1919 on 2011-06-28
Bump...

---

### Post by gnome1919 on 2011-06-29
No idea?!?! please....

---

### Post by gnome1919 on 2011-07-01
bump...bump....

---

### Post by gmargo on 2011-07-01
I avoided a similar problem by adding the "nomodeset" option to the boot parameters.  My netbook would suspend fine but crash on resume.

---

### Post by Frogs Hair on 2011-07-01
For some reason on my dual boot the mouse fails to bring the computer out of suspend . I have to resume by slightly depressing power button on my tower , but not to point of restarting the computer. This has been the case on four different Ubuntu releases .

---

### Post by mikejonesey on 2011-07-01
you need to try to find out why it can resume, checkout dmesg or /var/syslog

---

### Post by gnome1919 on 2011-07-02
> **mikejonesey said:**
> you need to try to find out why it can resume, checkout dmesg or /var/syslog

Thanks for your reply mikejonesey.
as I'm new to Linux, I attach my "dmesg" file to this post so maybe you can help me with my problem, thank you very much.

---

### Post by dino99 on 2011-07-02
be sure that your swap partition have at least 4 Gb

---

### Post by jmielke on 2011-07-02
I'm running 10.10 -- 64bit version.  This problem started for me with the most recent kernel upgrade to 30 from 28...  Not sure if this helps anyone but I think this is a bug as opposed to the usual issues with Suspend/resume

---

### Post by Toz on 2011-07-02
The suspend log file is /var/log/pm-suspend. Anything of interest in there? Failure messages?

Resource: [https://wiki.ubuntu.com/UnderstandingSuspend]("https://wiki.ubuntu.com/UnderstandingSuspend")

---

### Post by webbrowser on 2011-07-02
I believe I have the same problem.  Suspend appears to work (when selected from button on top right corner of desktop).  When I attempt to resume, I just get a blank screen.  

What's different is that it is not sufficient for me to hard reset the notebook.  Not even powering off the notebook, waiting a few seconds, and powering it back on helps - if I do that while it is connected to the power mains, it just goes back into the blank screen.  I found that I needed to power off the notebook, disconnect the power adaptor, power on the notebook, and connect the power adaptor only after the boot process has started.

I have tried to install tuxonice, hibernate, but they don't appear to help.

My notebook:
Asus K52Dr
AMD Phenom II N830
ATI Radeon HD5470 (using standard drivers, not the proprietary ones)

Others have suggested:
- ensuring there is sufficient swap.
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3960       1351       2608          0         76        514
-/+ buffers/cache:        761       3199
Swap:         4091          0       4091

- checking pm-suspend.log (attached)

---

### Post by Toz on 2011-07-03
Do you have an sd card plugged in? If so, try suspending without it plugged in.

If it doesn't work or this isn't the case, can you post back the contents of:```
ls /sys/bus/pci/drivers/ehci_hcd/
```

---

### Post by webbrowser on 2011-07-03
I don't have any SD cards inserted.

[FONT=Fixedsys]$ ls /sys/bus/pci/drivers/ehci_hcd/ -l
total 0
lrwxrwxrwx 1 root root    0 2011-07-03 17:07 0000:00:12.2 -> ../../../../devices/pci0000:00/0000:00:12.2
lrwxrwxrwx 1 root root    0 2011-07-03 17:07 0000:00:13.2 -> ../../../../devices/pci0000:00/0000:00:13.2
lrwxrwxrwx 1 root root    0 2011-07-03 17:07 0000:00:16.2 -> ../../../../devices/pci0000:00/0000:00:16.2
--w------- 1 root root 4096 2011-07-03 17:07 bind
lrwxrwxrwx 1 root root    0 2011-07-03 17:07 module -> ../../../../module/ehci_hcd
--w------- 1 root root 4096 2011-07-03 17:07 new_id
--w------- 1 root root 4096 2011-07-03 17:07 remove_id
--w------- 1 root root 4096 2011-07-03 17:07 uevent
--w------- 1 root root 4096 2011-07-03 17:07 unbind
[/FONT]
Sorry to add... maybe it's not the same as the OP after all.  I noticed that after attempting to suspend, the notebook's power and wireless indicator lights remain on, and the NB's cpu fan continues blowing.  Bizarrely, it is to this state that the NB returns to after a supposed hard reset with the power button pressed for 4s (without disconnecting power adaptor).

---

### Post by Toz on 2011-07-03
There are a number of **acpi_sleep** kernel parameters you could try ([http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")):
```
acpi_sleep=	[HW,ACPI] Sleep options
			Format: { s3_bios, s3_mode, s3_beep, s4_nohwsig,
				  old_ordering, s4_nonvs, sci_force_enable }
			See Documentation/power/video.txt for information on
			s3_bios and s3_mode.
			s3_beep is for debugging; it makes the PC's speaker beep
			as soon as the kernel's real-mode entry point is called.
			s4_nohwsig prevents ACPI hardware signature from being
			used during resume from hibernation.
			old_ordering causes the ACPI 1.0 ordering of the _PTS
			control method, with respect to putting devices into
			low power states, to be enforced (the ACPI 2.0 ordering
			of _PTS is used by default).
			nonvs prevents the kernel from saving/restoring the
			ACPI NVS memory during suspend/hibernation and resume.
			sci_force_enable causes the kernel to set SCI_EN directly
			on resume from S1/S3 (which is against the ACPI spec,
			but some broken systems don't work without it).
```
I would try: **acpi_sleep=old_ordering** and **acpi_sleep=nonvs**

The second thing you could try is to unbind ehci_hcd devices from the kernel prior to suspend and rebind on resume (they are known to hang up the suspend cycle). Here's how:
1. ```
gksudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd
``` and add the following contents (specific to your devices from **ls /sys/bus/pci/drivers/ehci_hcd/**):
```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device 0000:00:1a.0:
               echo -n "0000:00:12.2" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:13.2" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:16.2" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device 0000:00:1a.0:
              echo -n "0000:00:12.2" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:13.2" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:16.2" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac
``` 2. Make it executable```
sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd
```3. Lets unload some other usual suspects:
```
gksudo gedit /etc/pm/config.d/unload_modules
```with the following contents:```
SUSPEND_MODULES="xhci sdhci"
```

And try again. Post back the contents of **/var/log/pm-suspend** again as well as **/var/log/syslog**.

---

### Post by jmielke on 2011-07-03
I think this is a bug in the most recent kernel.  At least that is the case with Ubuntu 10.10 64-bit...  Try using a previous kernel.  That worked for me.  Hope they fix it in the next upgrade.

---

### Post by webbrowser on 2011-07-06
I tried appending acpi_sleep=old_ordering first, then acpi_sleep=nonvs.  Neither helped suspend to work.

Then I tried steps 1, 2 and 3.  Wahey - sleeping and resuming finally worked!

Then I removed the /etc/pm/confid./unload_modules file (undo step 3), and sleep/resume still worked.  So my conclusion is that unbinding the ehci devces did the job for me, running the asus K52Dr on amd64.

Many thanks!:popcorn:

---

### Post by gnome1919 on 2011-07-07
Thanks for your replies,
I did what were mentioned in previous posts but no chance :( !
Hare are two logs which may help solving my problem.
Thanks again

---

### Post by Toz on 2011-07-07
Try adding:
```
Option "VBERestore" "true"
```
to the "Device" section of your **/etc/X11/xorg.conf** file and rebooting.

If that doesn't work, try creating (or adding to if the file exists) a file in **/etc/pm/config.d** called **config**:
```
gksudo gedit /etc/pm/config.d/config
```
with the following contents:
```
SUSPEND_MODULES="fglrx"
```

If that doesn't work, try:
```
SUSPEND_MODULES="rt2500usb"
```

And if that doesn't work, try them both:
```
SUSPEND_MODULES="fglrx rt2500usb"
```

After each one of those suggestions, save a copy of /var/log/pm-suspend and post back.

---

### Post by mikejonesey on 2011-07-07
have you installed any 3rd party drivers?

my best guess would be it may be somthing to do with;
"ATI Catalyst driver detected, not using quirks."

if it can't find the driver to unload is it failing to find this driver to load it?

this is the video driver,

after your pc goes to suspend what behaviour does it have when you try and wake it? (what works, what doesn't, do you get any signs of life?)

maybee Toz's solution will work as it will force the removal of fglrx for the video/graphics?

---

### Post by gnome1919 on 2011-07-08
> **Toz said:**
> Try adding:
```
Option "VBERestore" "true"
```
to the "Device" section of your **/etc/X11/xorg.conf** file and rebooting.

If that doesn't work, try creating (or adding to if the file exists) a file in **/etc/pm/config.d** called **config**:
```
gksudo gedit /etc/pm/config.d/config
```
with the following contents:
```
SUSPEND_MODULES="fglrx"
```

If that doesn't work, try:
```
SUSPEND_MODULES="rt2500usb"
```

And if that doesn't work, try them both:
```
SUSPEND_MODULES="fglrx rt2500usb"
```

After each one of those suggestions, save a copy of /var/log/pm-suspend and post back.

Thanks for your reply Toz,
I did what you told in your post (all 4 solutions), but I still have the same problem. Here is the log file after trying the last solution.
Thanks again

---

### Post by gnome1919 on 2011-07-08
> **mikejonesey said:**
> have you installed any 3rd party drivers?

my best guess would be it may be somthing to do with;
"ATI Catalyst driver detected, not using quirks."

if it can't find the driver to unload is it failing to find this driver to load it?

this is the video driver,

after your pc goes to suspend what behaviour does it have when you try and wake it? (what works, what doesn't, do you get any signs of life?)

maybee Toz's solution will work as it will force the removal of fglrx for the video/graphics?

Thanks again mikejonesey,
I told about Toz's solutions in my previous post. About ATI Catalyst Driver; yes I have ATI Catalyst driver installed on my system. Actually I installed it because of this problem! I thought maybe installing the ATI Catalyst driver would solve the problem.

---

### Post by Toz on 2011-07-09
Try installing the package uswsusp from the Software Centre or:```
sudo apt-get install uswsusp
```

Once installed, try:
```
sudo s2ram
```

If you get an error about an unknown system, then try:
```
sudo s2ram -f
```

Does this package suspend/resume properly?

---

### Post by gnome1919 on 2011-07-09
> **Toz said:**
> Try installing the package uswsusp from the Software Centre or:```
sudo apt-get install uswsusp
```

Once installed, try:
```
sudo s2ram
```

If you get an error about an unknown system, then try:
```
sudo s2ram -f
```

Does this package suspend/resume properly?

Thank you very much Toz, It finally works!
By the way, is there a way to create a shortcut file (like a user script) to use it when I want to put the machine in suspend state? I mean if I want to call the command (sudo s2ram -f) outside the Terminal by just clicking on a shortcut file like when I use Suspend button.
Thanks in advance

---

### Post by Toz on 2011-07-09
I haven't used uswsusp for a couple of years, but I remember you can set it as your default suspend mechanism allowing you to use the normal menu suspend options. IIRC, you need to:

1. Copy over a default file:
```
sudo cp -a /usr/lib/pm-utils/defaults  /etc/pm/config.d/config
```

2. Edit the file:```
gksudo gedit /etc/pm/config.d/config
```
and uncomment and/or add these lines:
```
SLEEP_MODULE="uswsusp"
S2RAM_OPTS="--force"
```
and save the file.

I believe you need to reboot to make it work. Test it out. If it doesn't work, post back your /var/log/pm-suspend.log file. 
For some reason, I'm remembering that we may need to update your initramfs as well.

---

### Post by gnome1919 on 2011-07-11
> **Toz said:**
> I haven't used uswsusp for a couple of years, but I remember you can set it as your default suspend mechanism allowing you to use the normal menu suspend options. IIRC, you need to:

1. Copy over a default file:
```
sudo cp -a /usr/lib/pm-utils/defaults  /etc/pm/config.d/config
```

2. Edit the file:```
gksudo gedit /etc/pm/config.d/config
```
and uncomment and/or add these lines:
```
SLEEP_MODULE="uswsusp"
S2RAM_OPTS="--force"
```
and save the file.

I believe you need to reboot to make it work. Test it out. If it doesn't work, post back your /var/log/pm-suspend.log file. 
For some reason, I'm remembering that we may need to update your initramfs as well.

Thank you for your reply Toz,
I forgot to post back. After I installed uswsusp, it automatically changed default sleep module to itself, and I think that I don't need to do anything else, but thank you anyway, your post will definitely help me in the future.

---

### Post by Toz on 2011-07-11
Glad to hear and thanks for posting back. Can you please mark this thread as solved via the "Thread Tools" link above?

---

### Post by gnome1919 on 2011-07-26
Hi Toz,

I'm having a problem with suspend again; after a few days when I tried to suspend the system by clicking on suspend button from top right menu, the same problem occurred again; it didn't resume from suspend! I did what you said on your last post to make it default module on suspend, but it didn't solve the problem, but still I can suspend and resume the system safely by entering "s2ram -f" in Terminal. I will post "/var/log/pm-suspend.log" on the thread as you asked for.
Thank you very much in advance for your help Toz.

---

### Post by Toz on 2011-07-26
Try putting:
```
SLEEP_MODULE="uswsusp"
```into the file **/etc/pm/config.d/00sleep_module** and
```
S2RAM_OPTS="--force"
QUIRK_NONE="true"
```into the file **/etc/pm/config/defaults**.

Reference link: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")

Try another suspend. If it doesn't work, and you have to reboot, post back the contents of /var/log/dmesg.0.

This should make uswsusp default. If not, we can still try to overwrite system files.

---

### Post by gnome1919 on 2011-07-26
> **Toz said:**
> Try putting:
```
SLEEP_MODULE="uswsusp"
```into the file **/etc/pm/config.d/00sleep_module** and
```
S2RAM_OPTS="--force"
QUIRK_NONE="true"
```into the file **/etc/pm/config/defaults**.

Reference link: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")

Try another suspend. If it doesn't work, and you have to reboot, post back the contents of /var/log/dmesg.0.

This should make uswsusp default. If not, we can still try to overwrite system files.

Thank you for your help Toz,
I did what you said but still no luck on resuming from a system default suspend. here is what you requested for.
Thanks again

---

### Post by Toz on 2011-07-26
Ok. Lets try this:

1. Make a backup of your existing pm-suspend file.
```
sudo mv /usr/sbin/pm-suspend /usr/sbin/pm-suspend.original
```

2. Create a new starter script:
```
sudo gedit /usr/local/bin/s2ram.sh
```
...with the following content:
```
#!/bin/bash
s2ram -f
```
...save the file and make it executable:
```
sudo chmod +x /usr/local/bin/s2ram.sh
```

3. Link the new starter script to the pm-suspend command:
```
sudo ln -s /usr/local/bin/s2ram.sh /usr/sbin/pm-suspend
```

Now try it again. 

***One thing to keep in mind if using this workaround is that if pm-utils (the package that contains pm-suspend) ever gets updated, it will overwrite this change. In that case, you will need to redo step #3.

---

### Post by gnome1919 on 2011-07-27
> **Toz said:**
> Ok. Lets try this:

1. Make a backup of your existing pm-suspend file.
```
sudo mv /usr/sbin/pm-suspend /usr/sbin/pm-suspend.original
```

2. Create a new starter script:
```
sudo gedit /usr/local/bin/s2ram.sh
```
...with the following content:
```
#!/bin/bash
s2ram -f
```
...save the file and make it executable:
```
sudo chmod +x /usr/local/bin/s2ram.sh
```

3. Link the new starter script to the pm-suspend command:
```
sudo ln -s /usr/local/bin/s2ram.sh /usr/sbin/pm-suspend
```

Now try it again. 

***One thing to keep in mind if using this workaround is that if pm-utils (the package that contains pm-suspend) ever gets updated, it will overwrite this change. In that case, you will need to redo step #3.


It didn't solve the problem Toz :(:confused:
I post the log files again in case you need them.
Thanks

---

### Post by Toz on 2011-07-27
Does it work when you type in **sudo s2ram -f** in the terminal?

What do the following commands return:
```
ls -l /usr/sbin/pm-suspend
ls -l /usr/local/bin/s2ram.sh
cat /usr/local/bin/s2ram.sh
```

---

### Post by gnome1919 on 2011-07-27
> **Toz said:**
> Does it work when you type in **sudo s2ram -f** in the terminal?

What do the following commands return:
```
ls -l /usr/sbin/pm-suspend
ls -l /usr/local/bin/s2ram.sh
cat /usr/local/bin/s2ram.sh
```

Hi,
Yes, it always works when I type in **sudo s2ram -f** in the terminal without any problem.

```
ls -l /usr/sbin/pm-suspend
```
*Returns:*
```
lrwxrwxrwx 1 root root 23 2011-07-27 10:34 /usr/sbin/pm-suspend -> /usr/local/bin/s2ram.sh
```


```
ls -l /usr/local/bin/s2ram.sh
```
*Returns:*
```
-rwxr-xr-x 1 root root 21 2011-07-27 10:30 /usr/local/bin/s2ram.sh
```


```
cat /usr/local/bin/s2ram.sh
```
*Returns:*
```
#!/bin/bash
s2ram -f
```

Did I do something wrong?

---

### Post by Toz on 2011-07-27
And:
```
cat /etc/pm/config.d/config
```

---

### Post by Toz on 2011-07-27
Also try creating a file called module in /etc/pm/config.d:
```
gksudo gedit /etc/pm/config.d/module
```
with the following contents:
```
SLEEP_MODULE=uswsusp
```

Reference: [https://wiki.archlinux.org/index.php/Pm-utils#Using_another_sleep_backend_.28like_uswsusp.29]("https://wiki.archlinux.org/index.php/Pm-utils#Using_another_sleep_backend_.28like_uswsusp.29")

---

### Post by gnome1919 on 2011-07-27
> **Toz said:**
> And:
```
cat /etc/pm/config.d/config
```

I attached the file instead of copy its output.

---

### Post by Toz on 2011-07-27
That looks good. Can you try the suggestion in post #36?

And if that doesn't work, try running a:
```
sudo update-initramfs -u
```
and reboot.

---

### Post by gnome1919 on 2011-07-27
> **Toz said:**
> Also try creating a file called module in /etc/pm/config.d:
```
gksudo gedit /etc/pm/config.d/module
```
with the following contents:
```
SLEEP_MODULE=uswsusp
```

Reference: [https://wiki.archlinux.org/index.php/Pm-utils#Using_another_sleep_backend_.28like_uswsusp.29]("https://wiki.archlinux.org/index.php/Pm-utils#Using_another_sleep_backend_.28like_uswsusp.29")

After doing this and rebooting twice it finally works again! I didn't mention it in my last post because after the first restart the problem still existed! By the way I updated initramfs before as you said earlier in post #25. Thank you so much Toz for your great help [-o<=D>:D

---

