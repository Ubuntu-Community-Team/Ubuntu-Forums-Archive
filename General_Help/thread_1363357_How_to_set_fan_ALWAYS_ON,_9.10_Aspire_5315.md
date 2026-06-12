---
title: "How to set fan ALWAYS ON, 9.10 Aspire 5315"
date: 2009-12-24
forum: General Help
---

### Post by Victor Sheckels on 2009-12-24
Good morning.

My fan turns off when Ubuntu boots and will not turn back on.  I have attempted several fixes including installation of a new kernel based on a BUG tracking and setting several suggested ACPI variables in the GRUB configuration file, and none of these have restored my fan's function.  Therefore I want to remove the new kernel's interference with my fan speed and/or manually order my fan to run at all times.

Until this is done, my laptop is a brick.  Any help would be appreciated.  Thank you for your time.

---

### Post by nishant.singh28 on 2009-12-24
Why in the world do you want to run your notebook fan to run all the time? It will kick in as and when required. On my system it kicks in at 2100 RPM when the temperature reaches around 42 and speeds up to 4200 RPM automatically on reaching approx. 56 degrees. Let the BIOS control the fan as it wishes to. You need not force it.

---

### Post by Victor Sheckels on 2009-12-24
It does not kick in when required. The system automatically shuts down when the CPU reaches 98 Celsius, which my laptop happily reaches before too long, and the fan does not care.

---

### Post by nishant.singh28 on 2009-12-24
Are you sure your fan is ok? I've suffered 2 heat sink failures due to Windows crashes so check if the heat sink works normally otherwise.

---

### Post by Victor Sheckels on 2009-12-24
It runs just fine until Ubuntu boots.  It also ran just fine under 9.04.

---

### Post by nishant.singh28 on 2009-12-24
You have lmsensors installed?

---

### Post by Victor Sheckels on 2009-12-24
Not currently.  I had installed it previously, but when I fresh-installed 9.10 to try to fix this problem (as opposed to simply upgrading from 9.04) I lost it, and right now it tells me the package is not found.

---

### Post by Victor Sheckels on 2010-01-01
I made the mistake of restarting my computer and again my fan is dead and my computer is on the way to overheating.

Does anyone know how I can set the fan always on?  I am fully aware that this is not an optimal fix, but then neither is reinstalling my OS again nor have any of the other fixes recommended for this issue actually worked.  (See above.)  I am looking to override any interference with my fan.  I have seen, somewhere, a thread indicating that this can indeed be done but I have been unable to find it again.

I need to be able to turn my computer off and on without praying that this particular boot is the one in fifty that the fan will actually remain on.  Yes, on rare occasion it remains on through the booting process and then remains on constantly--but then I cannot reboot the machine or it will likely fail again.  It DOES NOT activate in response to overheating.  The computer shuts down from overheat, presumably at 98 C--and I get burned by it if I actually have it in my lap--and the fan DOES NOT activate.

I cannot get any work done on my laptop if I cannot take it out with me for fear that the fan will not turn on.  Any help resolving this issue would be appreciated.

---

### Post by Victor Sheckels on 2010-01-02
Let's add insult to injury here.

I found the lm-sensors and sensors-applet.  Went to install them.  Computer overheated while in the process of configuring sensors-applet and shut down.  It now tells me these packages are both broken and to run dpkg --configure -a.  But when I do that it gives me another, similar error and quits.

```
v@Mneme2:~$ sudo dpkg --configure -a
[sudo] password for v: 
Setting up hddtemp (0.3-beta15-45) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing hddtemp (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsensors-applet-plugin0 (2.2.3-2ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsensors-applet-plugin0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sensors-applet:
 sensors-applet depends on libsensors-applet-plugin0; however:
  Package libsensors-applet-plugin0 is not configured yet.
dpkg: error processing sensors-applet (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hddtemp
 libsensors-applet-plugin0
 sensors-applet
v@Mneme2:~$ 
```

I tried to then configure lib-sensors-applet-plugin0 as requested and it broke too.

This is ridiculous.

---

### Post by Victor Sheckels on 2010-01-02
And now I can neither install nor uninstall those two damned packages because some stupid configuration file got broken.  Not that it matters I suppose.

Bump.

---

### Post by Victor Sheckels on 2010-01-02
Trying acpi=off in the GRUB config file causes the system to freeze with bootspew errors while Linux is starting to load.

According to shutdown spew, fancontrol is running, however the /etc/fancontrol file is empty.  pwnconfig will not run because fancontrol is running.  I THINK lm-sensors is working but after I ran sensors all it saw was:

```
v@Mneme2:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +110.0°C)
```

And I know that temperature is a lie.

Please!  How do I get RID of this **** and let my fan be controlled by whatever controlled it in 9.04 and earlier, which did just fine??  I don't have time to waste on this foolishness; I have projects piling up and only one computer right now.  :(

---

### Post by asmotj on 2010-01-02
I am having the same problem with an exception and a pathetic in fact embarrassing fix but, it works for me.
  
If the fan is running when the grub loads it seems to work properly. 
So I turn on the laptop; Then, in about 5 minutes it shuts off if I immediately reboot and the fan is running when the grub loads it is good for the rest of the day. 5715-4713 is my model number

---

### Post by Victor Sheckels on 2010-01-02
```
v@Mneme2:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +63.0°C  (high = +100.0°C, crit = +100.0°C)  
```

63C is about right for the current temp given the time I've had it running, but I have nothing about fans or anything else here.

---

### Post by Victor Sheckels on 2010-01-02
Wow, it's only at 84C now.  I guess I can sometimes keep the computer running a bit longer by only having one program open...  *sigh*

---

### Post by derekmbarnes on 2010-01-03
> **Victor Sheckels said:**
> And now I can neither install nor uninstall those two damned packages because some stupid configuration file got broken.  Not that it matters I suppose.

Bump.

I'm in a group of Toshiba users who have been having the same problem; research leads us to believe it's a conflict between BIOS and the latest kernel, but we're not totally sure. (Thread: [http://ubuntuforums.org/showthread.php?t=1282161](http://ubuntuforums.org/showthread.php?t=1282161) )

Given the state your computer is in right now, I'd recommend trying to boot from the installer disk and see if it functions any better. I'm about ready to try that myself.

---

### Post by Victor Sheckels on 2010-01-06
Bump.

Same **** different day.

---

### Post by pgp_protector on 2010-01-06
Tell you find a valid solution, have you looked at adding an external fan that you can control to keep your system running while trying to fix the control issue?

May not be the "proper" solution, but it should keep you running.

---

### Post by Victor Sheckels on 2010-01-06
Something portable?  Would a laptop cooling pad do the trick I wonder?  No idea how much those run... hm.

---

### Post by pgp_protector on 2010-01-06
> **Victor Sheckels said:**
> Something portable?  Would a laptop cooling pad do the trick I wonder?  No idea how much those run... hm.
They should help, I've seen them from around $20-$40 at Fry's Electronics. YMMV

ETA
$20 at Amazon for some.
[http://www.amazon.com/Targus-Laptop-Chill-Pad-PA248Y01U/dp/B000OE1RGI](http://www.amazon.com/Targus-Laptop-Chill-Pad-PA248Y01U/dp/B000OE1RGI)

---

### Post by Victor Sheckels on 2010-01-06
From what I can tell, this IS a somewhat common issue, isn't it?

---

### Post by pgp_protector on 2010-01-06
> **Victor Sheckels said:**
> From what I can tell, this IS a somewhat common issue, isn't it?

It's getting better.
I'm still new to Linux & Ubuntu, I've tried it a few years ago & had problems with it seeing some of my hardware (WiFi anyone) , but it's gotten much better over the years.

Part of the problem is that the hardware manufactures don't supply Linux drivers often, as they don't want to spend the time for that segment of the market, but this is changing.

---

### Post by Victor Sheckels on 2010-01-06
*nods*  It's tough, I know.  I was meaning this specific bug-hive though.

---

### Post by Victor Sheckels on 2010-01-06
```
/usr/sbin/fancontrol: line 50: /var/run/fancontrol.pid: Permission denied
Loading configuration from /etc/fancontrol ...
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
Some mandatory settings missing, please check your config file!
v@Mneme2:~$ 
```

Interesting.  I tried to run fancontrol and got this.  Is this relevant?

---

### Post by Victor Sheckels on 2010-01-07
Bump.

SSDD.

---

### Post by Victor Sheckels on 2010-01-07
Failed to revert to 9.04.  The installer CD won't work; it locks up every time.  I've also tried installing 9.10 on my new system and that doesn't work either.  Why does the installer lock up on multiple versions of Linux, on two completely different computers with different hardware and OSes, on multiple discs burned at various speeds on two different burners hosted on two different systems??

Is there a way to nuke your **** back to a previous version without a CD?  This is getting ridiculous.

---

### Post by Yellow Pasque on 2010-01-16
> Why does the installer lock up on multiple versions of Linux
Are you sure you haven't damaged the CPU with overheating? It should automatically shut down at a lower temp than 98C. That's pretty high...

Also, if you can get your system running with the fan operating properly while booting a CD with memtest, run that.

---

### Post by josephpford on 2010-03-05
> **Victor Sheckels said:**
> Failed to revert to 9.04.  The installer CD won't work; it locks up every time.  I've also tried installing 9.10 on my new system and that doesn't work either.  Why does the installer lock up on multiple versions of Linux, on two completely different computers with different hardware and OSes, on multiple discs burned at various speeds on two different burners hosted on two different systems??

Is there a way to nuke your **** back to a previous version without a CD?  This is getting ridiculous.

I've got a similar problem with my Acer.  I have an old Acer Aspire 3000.  Acers are notorious for having over-heating problems.  (I got this one for free and would never purchase one myself).  

Here's a solution that will at least allow you to work on your computer while you investigate and whatnot...  

Step 1. Locate the side of the laptop that the fan exhaust port is.  You can tell it is the fan exhaust port by putting your finger near it and hot air should blow out once in a while (according to your posts - this may only be while it's booting or while you are installing linux).  

Go get a vacuum.  Not the kind with the spinning brush or the robotic ones that spin around, scare cats and get dogs all riled up.  The kind that has suction.  Put that suction right up to the exhaust port.  If you want to, you can install a cpu temp monitoring application like sensors-applet and see your cpu-temp go down...down...down...  even if you run something like Seti@Home to test the CPU out...  

Obviously this is a less than ideal solution, but it will at least allow you to play around on the computer and try to fix the issue permanently without damaging your CPU (if it is not already damaged).

Good luck.

-Joe

---

### Post by flippo on 2010-03-05
Back when I had direct control over my fans I had a file in /proc/ for them (this is where most hardware based stuff is) run something like ```
sudo find /proc/ -name '*fan*'
```mine had something like fan1_min which I could```
echo "5000" > /proc/.../fan1_min
```to ensure my fan was always going strong.  Ideally you really want your PC to do this automatically though, now that my fan control drivers are better I have it compiled into my kernel and it no longer pops up in proc.

---

