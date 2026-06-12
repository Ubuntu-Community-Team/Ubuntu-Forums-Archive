---
title: "Battery not recognized"
date: 2009-12-08
forum: General Help
---

### Post by jfinner1 on 2009-12-08
I have a Toshiba Satillite, running Ubuntu Jaunty, and for some reason my battery is not recognized. When viewing the battery monitor, it shows that the battery has no life, even if it's fully charged, or running on battery. The battery still works normally, charges normally, ect., but I have no indication of the battery charge, and no warning before the battery dies. Any idea why this is, or how I can fix it?

---

### Post by jfinner1 on 2010-01-03
bump.

---

### Post by chaanakya_chiraag on 2010-01-03
That seems really weird!!!  Did it work ok in Intrepid or Hardy?

---

### Post by chaanakya_chiraag on 2010-01-03
Also, maybe Karmic will work better...??  Try loading the Karmic live cd and see if it recognizes your battery.

---

### Post by chaanakya_chiraag on 2010-01-03
Also, do suspend/hibernate work as they usually do??

---

### Post by jfinner1 on 2010-01-03
It's worked fine since I first installed Ubuntu, I think that was Hardy. It worked fine on my first install of Jaunty, I'm not sure if it worked when I installed Karmic (I had a lot of problems), but when I did a reinstall id Jaunty, it stopped working. I don't remember ever having issues, so I'm really not sure why they would start now.

---

### Post by MindFusion on 2010-01-03
I have thesame problem and i think i know why. It's because when i installed ubuntu 9.10, i didn't branch in my battery in my laptop but i just plugged it in with the cable. That's probably why my battery wasn't included in the installation and why i can't access my battery settings now, neither can i even add battery to my panel...

---

### Post by chaanakya_chiraag on 2010-01-03
@jfinner1: did you do what MindFusion did and take the battery out before installing??  That could be why the "driver" for the battery is not installed and your battery is not detected.

@MindFusion: That sucks...let me see if I can find a solution...

---

### Post by jfinner1 on 2010-01-03
I can add the battery to the panel, but it shows as always plugged in, even when it's running on battery. When I unplug the computer, the screen will dim. But I have no other indication that the computer realizes it's running on battery. As for hibernation, I don't think it works correctly. I know that when the battery dies it attempts to hibernate, but it never wakes up, so I have to hard shut it down and reboot. I haven't tried to hibernate while still plugged in.

---

### Post by chaanakya_chiraag on 2010-01-03
Hmmm...Have you gone into Power Management and checked the settings there?

---

### Post by jfinner1 on 2010-01-03
No, the battery was in during install. I don't see any settings in Power Manager that would help me out. It's possible that the drivers weren't installed. If this is the case, how do I find and install the drivers to use my battery?

---

### Post by chaanakya_chiraag on 2010-01-03
Is ACPI enabled in your BIOS?  I think ACPI is required in order for power manager to work correctly...??  Please correct me if I'm wrong, because I'm not really sure :D

---

### Post by jfinner1 on 2010-01-03
What's that and how do I check?

---

### Post by chaanakya_chiraag on 2010-01-03
Well, actually, let's try this:
Open up a terminal and enter the following command:
```
cat /proc/acpi/battery/<press [Tab] key>/info
```

---

### Post by jfinner1 on 2010-01-03
No such file or directory

---

### Post by chaanakya_chiraag on 2010-01-03
Try this:
```
ls /proc/acpi/battery
```

---

### Post by jfinner1 on 2010-01-03
Still no such file or directory

---

### Post by chaanakya_chiraag on 2010-01-03
So you don't even have a battery directory in acpi.  That would explain why Power Manager thinks the battery doesn't exist.  Does the livecd pick up the battery just fine?  Or does it behave exactly like the install?

---

### Post by jfinner1 on 2010-01-03
I'm not sure. I don't currently have my live install cd, or any blank discs to make a new one. I'm OOT for a bit.

---

### Post by chaanakya_chiraag on 2010-01-03
I think your best bet is to try a live cd, and if it works, reinstall.  Or, if a friend has the exact same laptop and runs Ubuntu, you could go into /proc/acpi and copy the battery folder to your own installation.  If it's not really a hassle, I would say just let it be, because reinstalls are such a pain if you don't have a separate /home partition.

---

### Post by jfinner1 on 2010-01-03
It's a big hassle. I run on battery and I've lost quite a bit of stuff due to the battery dying without warning... Well, I don't know anyone else with a Ubuntu install, and I really don't want to do a reinstall. Is there any other way to fix it?

---

### Post by chaanakya_chiraag on 2010-01-03
I mean, Ubuntu doesn't recognize ur battery, but I'm not sure how to fix that.  Time for the experts to step in... :D

---

### Post by chaanakya_chiraag on 2010-01-03
If you know your battery's specs or can find it, do the following:
1)Open the terminal and type ```
sudo mkdir /proc/acpi/battery
cd /proc/acpi/battery
sudo mkdir BAT1
cd BAT1
sudo gedit info
```2) Type the following into the window that opens up:
```
present:                 yes
design capacity:         38880 mWh
last full capacity:      34387 mWh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 691 mWh
design capacity low:     0 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            G71C00001110
serial number:           1000001428
battery type:            Li-ION  
OEM info:                
```[B]
Be sure to substitute the actual values in for the values I have provided.[/B]
See if that works.  I'm not sure, but it's worth a shot :)

---

### Post by chaanakya_chiraag on 2010-01-03
Also do the following:
3) Go back to the terminal window and type:
```
sudo gedit alarm
```
and type the following into the window that appears:
```
alarm:                   712 mWh
```

---

### Post by jfinner1 on 2010-01-15
Again with it telling me that there's no such file or directory, lol. Hrm... I'm thinking I really might need a fresh install. Could this have anything to do with me using the alternate install?

---

### Post by chaanakya_chiraag on 2010-01-15
Wait...so you don't have a /proc/acpi directory either?  Try this command:
```
cd /proc/acpi
```
If it tells you there is no such file or directory, there are some BIG problems.  I would think it's time to reinstall.

---

### Post by MindFusion on 2010-01-18
Just reinstall the OS, like i did. Just save your docs to an external hard drive and reinstall the operating machine. I did leave in my battery while reinstalling and now it is perfectly detected.

---

### Post by ShawnCP on 2010-05-28
My situation was a somewhat different but I found a workaround.  Symptoms:

 - Acer Aspire One NAV50 532h
 - Ubuntu Netbook Remix 10.4
 - Boot log message: ACPI: Battery slot [BAT0] (battery absent)    <-- not true
 - Power icon showed AC connected when booting on battery power
 - Plugging/unplugging AC causes the power icon to switch over and show battery correctly
 - Also suspending/resuming caused the battery icon to show correctly

I found that simply querying the battery state from the /proc/acpi/... caused the power icon to flip to battery so I added this line to my rc.local:

cat /proc/acpi/battery/BAT0/state >/dev/null

Now the battery icon appears correctly when booting on battery power.

One thing I wondered about - The BAT0 seems to be an identifier.  Is this associated with the specific physical battery itself?  If so, then I suppose if you have more than one battery you would need a line for each battery lol.  Does anyone know?

---

