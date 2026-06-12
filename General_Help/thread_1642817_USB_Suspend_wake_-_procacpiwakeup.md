---
title: "USB Suspend wake - /proc/acpi/wakeup"
date: 2010-12-10
forum: General Help
---

### Post by fivedots on 2010-12-10
Hi! New to Ubuntu and so far very impressed. Been running it for about a week on a very old P4 system that I use as a cheap media center. I've had a lot of luck so far and worked through most issues, but one thing has me stumped. 

I'm running Ubuntu 10.10.

I was following the instructions here...

[http://ubuntuforums.org/showthread.php?t=1332166&highlight=wireless+keyboard+wake](http://ubuntuforums.org/showthread.php?t=1332166&highlight=wireless+keyboard+wake)

...to enable my Microsoft Wireless USB Keyboard/Mouse to wake the system from suspend. Once I set USB & USB2 to enabled, it worked perfectly. But when trying to adjust some things, I accidentally overwrote the contents of the /proc/acpi/wakeup file and now it is blank. 

Performing 'cat /proc/acpi/wakeup' returned nothing and editing the file showed it blank as well. I then deleted the file hoping that the system would recreate it to no avail.

How do I restore this file to its default values?

Also (and the reason I was continuing to tinker and killed this file) once I've restored the file, how do I get the USB & USB2 to remain enabled upon reboot? The solution in the linked thread did not work for me at all; they return to disabled.

Thanks!

---

### Post by fivedots on 2010-12-11
Problem solved! First, for some reason along the way I started to use '/etc/acpi/wakeup' -- which of course is incorrect. Sure enough, '/proc/acpi/wakeup' was still intact. 

Here are the steps I took to allow my USB keyboard and mouse to wake the computer from sleep and to make sure that these settings persisted after a reboot:

In terminal, type:

```
cat /proc/acpi/wakeup
```

You will see a list of devices. Note the USB ones (named as USB, USB0, USB1, etc.). I only have two, so instead of going through the trouble of figuring out which one was the keyboard/mouse wireless receiver, I decided to enable both. In my case, this was USB and USB2.

In terminal, type (and adjust 'USB...' to match the names of your devices):

```
sudo -s
echo USB > /proc/acpi/wakeup
echo USB2 > /proc/acpi/wakeup
```

Now you should be able to resume from suspend via a USB device. In order to force these settings to stay upon reboot, you need to add all of the 'echo USB...' lines that you used above to  /etc/rc.local so it executes upon boot.

That should take care of it!

---

### Post by jacdaniels on 2012-02-06
[QUOTE=fivedots;10225603]Problem solved! First, for some reason along the way I started to use '/etc/acpi/wakeup' -- which of course is incorrect. Sure enough, '/proc/acpi/wakeup' was still intact. 

Here are the steps I took to allow my USB keyboard and mouse to wake the computer from sleep and to make sure that these settings persisted after a reboot:

In terminal, type:

```
cat /proc/acpi/wakeup
```

You will see a list of devices. Note the USB ones (named as USB, USB0, USB1, etc.). I only have two, so instead of going through the trouble of figuring out which one was the keyboard/mouse wireless receiver, I decided to enable both. In my case, this was USB and USB2.

In terminal, type (and adjust 'USB...' to match the names of your devices):

```
sudo -s
echo USB > /proc/acpi/wakeup
echo USB2 > /proc/acpi/wakeup
```

Now you should be able to resume from suspend via a USB device. In order to force these settings to stay upon reboot, you need to add all of the 'echo USB...' lines that you used above to  /etc/rc.local so it executes upon boot.

That should take care of it![

---

### Post by jacdaniels on 2012-02-08
i don't quite follow how to save this in the terminal(newbie)
can someone tell me exactly what i need  to do to save this command?

---

### Post by oldos2er on 2012-02-08
Could you please start a new thread, and give as many details about your problem as possible? Thanks.

---

