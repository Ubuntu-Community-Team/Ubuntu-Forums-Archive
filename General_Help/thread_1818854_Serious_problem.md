---
title: "Serious problem"
date: 2011-08-05
forum: General Help
---

### Post by Hovercat on 2011-08-05
Hi.

I have a computer running Ubuntu 10.10 which runs 3 game servers. I recently replaced the CPU, motherboard, and memory with better parts, and now I'm noticing after a couple of hours, the system shuts down, but the fans and such are still powered on. 

Unfortunately, I do not have a graphics card for the machine (nor does it have integrated graphics), so I can't tell if it's crashing, freezing, or going into standby.

Is there anything I can do?

Thank you!

---

### Post by sbraz on 2011-08-05
is it possible that your system goes into S1 standby?

---

### Post by Hovercat on 2011-08-05
> **sbraz said:**
> is it possible that your system goes into S1 standby?

It could be. I tried hitting some keys and the power button, but the system didn't restore functionality. (Couldn't log into SSH/connect to Apache)

---

### Post by allwimb on 2011-08-05
Could you check the /var/log/messages maybe you can find something that'll tell you if the system's going into standby or something similar.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by Hovercat on 2011-08-05
> **allwimb said:**
> Could you check the /var/log/messages maybe you can find something that'll tell you if the system's going into standby or something similar.

I've already looked through there (and syslog), there's nothing representing a crash or standby. A friend of mine said it could be driver problems, since the hard drive was recently moved out of another system. I'm going to put the RAM from that motherboard onto another one that has integrated graphics and do a memtest.

---

### Post by sbraz on 2011-08-05
what kernel are you running? 

uname -r

---

### Post by Hovercat on 2011-08-05
> **sbraz said:**
> what kernel are you running? 

uname -r

2.6.35-22-generic

---

### Post by Hovercat on 2011-08-05
I still need help...

---

### Post by blind2314 on 2011-08-05
> **Hovercat said:**
> I still need help...

Does the motherboard you bought happen to have a diagnostic LED display on it? If it's throwing a code, that will help eliminate whether or not the mobo is part of the problem.

---

### Post by Hovercat on 2011-08-05
> **blind2314 said:**
> Does the motherboard you bought happen to have a diagnostic LED display on it? If it's throwing a code, that will help eliminate whether or not the mobo is part of the problem.

No. It's an Asus P5N-D.

Could it be a chipset driver problem? I moved the hard drive from a motherboard which had the AMD K8 chipset to the P5N-D which has the NVIDIA nForce 750i SLI chipset.

---

### Post by blind2314 on 2011-08-05
> **Hovercat said:**
> No. It's an Asus P5N-D.

Could it be a chipset driver problem? I moved the hard drive from a motherboard which had the AMD K8 chipset to the P5N-D which has the NVIDIA nForce 750i SLI chipset.

That's possible, but I'm going to say unlikely. However, it's easy to test, so why don't you try that. Remove the software/driver install from the old mobo, and install the software from the new one. Do they both have native-Linux installs?

---

### Post by Hovercat on 2011-08-06
I have no idea. I don't know how to uninstall the old one or install the new one.

Also, the PC seems to stay up as long as I'm logged into SSH, otherwise it'll probably crash. It's never crashed while I have SSH open.

---

### Post by sbraz on 2011-08-06
depending on your system you might or not have some drivers installed, you can check with *jockey-text -l*.

when there's a kernel panic the scrollLock led starts blinking on the keyboard; when the hardware goes nuts it just hangs.

it is possible that you need to clean all the pci/pcie/dimm slots with a specific spray-electric-contacts-cleaner (make sure it doesn't melt plastics!) because there might be some micro-dust preventing signals to go as they should.

---

### Post by blind2314 on 2011-08-06
> **Hovercat said:**
> I have no idea. I don't know how to uninstall the old one or install the new one.

Also, the PC seems to stay up as long as I'm logged into SSH, otherwise it'll probably crash. It's never crashed while I have SSH open.

...have you searched?

[http://support.asus.com/Download.aspx?SLanguage=en&m=P5N-D&p=1&s=22](http://support.asus.com/Download.aspx?SLanguage=en&m=P5N-D&p=1&s=22)

Select Linux in the drop down box, and then choose Others -> Linux Support Drivers. That's *probably* the chipset drivers. Download it, and run the script inside (likely an install.sh script, but could possibly have a configure script, which means it will need to be compiled).

---

### Post by Hovercat on 2011-08-06
> **sbraz said:**
> depending on your system you might or not have some drivers installed, you can check with *jockey-text -l*.

when there's a kernel panic the scrollLock led starts blinking on the keyboard; when the hardware goes nuts it just hangs.

it is possible that you need to clean all the pci/pcie/dimm slots with a specific spray-electric-contacts-cleaner (make sure it doesn't melt plastics!) because there might be some micro-dust preventing signals to go as they should.

hovertac@game-dedi-server:~$ jockey-text -l
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
hovertac@game-dedi-server:~$

Also, I've had that dust issue once before with RAM on my old server.


> **blind2314 said:**
> ...have you searched?

[http://support.asus.com/Download.aspx?SLanguage=en&m=P5N-D&p=1&s=22](http://support.asus.com/Download.aspx?SLanguage=en&m=P5N-D&p=1&s=22)

Select Linux in the drop down box, and then choose Others -> Linux Support Drivers. That's *probably* the chipset drivers. Download it, and run the script inside (likely an install.sh script, but could possibly have a configure script, which means it will need to be compiled).

There are chipset drivers inside the download. Thank you for that.

Edit: There's different folders in the driver folder, which should I choose?

Fedora6
RHEL3_U7
RHEL3_U8
RHEL4_U4
RHEL4_U5
RHEL5
SLES10
SuSE10.2

---

### Post by gordintoronto on 2011-08-06
Overheating? Can you run lm-sensors on it?

Surely you could pick up a cheap graphics card on eBay, if only for debugging? I bought one for $10, which was a huge improvement over the onboard graphics on an old computer.

---

### Post by Hovercat on 2011-08-06
> **gordintoronto said:**
> Overheating? Can you run lm-sensors on it?

Surely you could pick up a cheap graphics card on eBay, if only for debugging? I bought one for $10, which was a huge improvement over the onboard graphics on an old computer.

I've already bought a GPU from eBay.

This is from LM-sensors on Monitorix (not configured for all 4 cores):

[img]http://i.imgur.com/iviUh.png[/img]

However, acpi -t always reports 40C.

Edit: As you can see, there are no "skips" in the graph that represents down time because I've had SSH open the whole time, and it will never crash if SSH is open. As of now, it's been up for 1 day, 6 hours and 32 minutes

---

### Post by sbraz on 2011-08-06
> **Hovercat said:**
> if SSH is open. As of now, it's been up for 1 day, 6 hours and 32 minutes
you can always have rc.local open a ssh from->to localhost :)
this is the strangest fix ever. :D

i don't know... swapping hardware shouldn't cause any issue like this.

the first thing that comes to my mind is trying to reconfigure any hardware related package, for example lm-sensors.

also, make a backup of your system before installing those "magic" drivers, you don't want to rely on funny "install.sh" scripts risking a veeeeeeery long chroot session, especially because it's not a simple desktop computer. :)

---

### Post by Hovercat on 2011-08-06
> **sbraz said:**
> you can always have rc.local open a ssh from->to localhost :)
this is the strangest fix ever. :D

i don't know... swapping hardware shouldn't cause any issue like this.

the first thing that comes to my mind is trying to reconfigure any hardware related package, for example lm-sensors.

also, make a backup of your system before installing those "magic" drivers, you don't want to rely on funny "install.sh" scripts risking a veeeeeeery long chroot session, especially because it's not a simple desktop computer. :)

Oh yeah, I originally installed LM-sensors on the old machine, so I guess it's trying to load the old drivers and that could be the problem.

Edit: I removed f71882fg (which was a driver from the old motherboard)

---

### Post by gordintoronto on 2011-08-07
> **Hovercat said:**
> This is from LM-sensors on Monitorix (not configured for all 4 cores):

[img]http://i.imgur.com/iviUh.png[/img]

However, acpi -t always reports 40C.

Edit: As you can see, there are no "skips" in the graph that represents down time because I've had SSH open the whole time, and it will never crash if SSH is open. As of now, it's been up for 1 day, 6 hours and 32 minutes

If the configuration has changed, you can re-run sudo sensors-detect. After a reboot, run sensors to get as much information as it can provide.

Do the fans seem to be noisy? That's an unscientific indication of high temperatures.

---

### Post by Hovercat on 2011-08-15
I don't mean to bump an old thread, but I'm still having this problem.

I put the original CPU/motherboard back in place of the P5N-D because I have to send that one to Asus for an RMA, and while I had the original CPU/motherboard in place, the crash happened again.

What should I do?

---

