---
title: "Fans constantly going high / CPU load high / is Ubuntu right for a laptop?"
date: 2009-10-11
forum: General Help
---

### Post by Diablosblizz on 2009-10-11
Hey, I've got a few things I'm just wondering about. Let's start off.

1. The fans constantly are on. I'm using a Toshiba L350D laptop, and the secondary fan (which isn't on all the time on Windows) is spinning fast and making a lot of noise. Is there something wrong, or am I using too much CPU that it has to kick in?

2. According to the resource monitor, I'm constantly using 25% of my CPU always. This would be okay if I was on a desktop, but this is a laptop and it needs to stay cool.

3. Is Ubuntu right for a laptop? I mean, is there a better Ubuntu (KUbuntu, XUbuntu) distro that would run better on my laptop and keep it cool?

Honestly, I just need it for typing documents and possibly sync it with my home machine (which is using Windows - but I'll get to that later). What is the Netbook Remix, and would it run better? Here's my specs:

AMD Turion X2 2.0 GHz dual core
3 GB DDR2 RAM
250GB HDD
ATI Raedon 1250X

4. Why is the minimum time for the monitor to turn off on battery power 11 minutes? That's pretty long if you're running on battery and want to conserve power.

Anyways, I hope to dive into some Linux distro, I'm just not sure which one yet. Ubuntu runs fine, but the heat and fan noise is a big problem for me, my fingers get sticky from the heat and it really peeves me off. Would xUbuntu lower the footprint and allow the fans to chill out?

Thank you very much.

---

### Post by Diablosblizz on 2009-10-12
Just to add, it seems that at startup my fans are quiet, and once I do a resource intensive program, such as installing a program, the fans goes up and never come back down. I can't figure out how to fix this.

Thank you so much. Also my brightness setting on my laptop doesn't go down, I can't change it at all. Is there a driver I am missing?

---

### Post by Boondoklife on 2009-10-12
Well you could try xubuntu but I have a feeling that you will have the same issue. I would put a temp monitor in one of your panels and watch it. You can see when the fans kick on and if they go off when/if it comes back down to that temp. Also you might want to run top to see if there are any rouge apps that are thrashing the laptop.

As far as should linux be on a laptop, a while back I would have said no as hibernate and sleep used to be plauged with issues and wifi was a coin toss for the most part. Now however there is not reason that you shouldn't I personally have it on mine and love it.

---

### Post by Diablosblizz on 2009-10-13
There's no "rogue" applications, everything is from install and I haven't installed anything but DropBox, and it was doing this before I installed dropbox. For the majority though, it's working. Like I read somewhere:

"Linux: if it aint bitchin it's working."

Can somebody shine some light on why the dim the display is 11 minutes though, is there a crack to change this? Thanks!

---

### Post by hwttdz on 2009-10-13
I think the display is linked to the screensaver time, even if screensaver is disabled. So if you run the screensaver slider all the way to 1 minute, then you can sleep the screen after 2 minutes.

---

### Post by P4man on 2009-10-13
First, let me rephrase your question. Its not "is ubuntu right for **a** laptop", but "is ubuntu right for **your** laptop". (Others would ask "is your laptop right for ubuntu"?).

Anyway, there are are a few possible causes. It could be that CPU scaling is not working, and your cpu is constantly running at full speed, instead of slowing down under light load. To check that, right click a panel, and add "cpu frequency scaling monitor". If you get no error message, then have a look if the cpu speed scales up and down depending on load.

A second possible explanation is that your videocard fan is running constantly, and that could be due to the videodrivers (or lack thereof). I believe the  ATI X1250 is no longer supported by AMD/ATI, so the latest binary drivers do not work with your laptop on jaunty (9.04) and later, you can only use the (already installed) opensource drivers. If it turns out those are to blame, then you could consider moving back to ubuntu 8.10, for which there are binary ATI drivers for your card.

A third possible explanation is that simply the deamon that controls the cpu fan is putting your fan at full speed for no reason. You can install some software to take control of your fan speed, but its not that easy, so ill wait a response to the other suggestions before delving in to that.

---

### Post by P4man on 2009-10-13
Digging a bit further, I found that your laptop probably doesn't allow setting fan and other hardware settings through ACPI. Toshiba uses their own proprietary interface, requiring proprietary software. how nice of them. You should ask them for linux software.

Anyway, some blokes reverse engineered it, and made a utility that might work for you. Open synaptic package manager (in system > adminstration)  and look for "toshutils", and install it (altneratively, run "sudo apt-get install toshutils" from a terminal).

Once installed, open a terminal and type 

```
sudo toshset -fan 6 
```

Lower number than 6 seems to be higher fanspeed (4 being full speed?), but you may want to experiment.
More info on all the other stuff you can do with toshset here:
[http://pwet.fr/man/linux/commandes/toshset](http://pwet.fr/man/linux/commandes/toshset)

**Edit**
Turns out you can also use it to set a time out for your display. heh:
-d <num>
    number of minutes until display auto-off

---

### Post by danwood76 on 2009-10-13
> **P4man said:**
> Digging a bit further, I found that your laptop probably doesn't allow setting fan and other hardware settings through ACPI. Toshiba uses their own proprietary interface, requiring proprietary software. how nice of them. You should ask them for linux software.


Not strictly true, most of the time it is actually a bug in the BIOS that causes these issues.
The BIOS usually does the fan control not the OS, it also does the display brightness etc.

Quite often the BIOS ACPIs are compiled using a faulty compiler (Microsoft made ) which windows deals with and loads fine but unfortunately linux does not (linux complies with the standards). Your problem shows classic signs of this error as both the fan control doesn't work and you cannot change display brightness.

Its highly possible that a BIOS update could solve your issue. (try that first)
You can find already fixed dsdt files to load into the kernel that solve issues here: [http://acpi.sourceforge.net/dsdt/view.php?manufacturer=Toshiba](http://acpi.sourceforge.net/dsdt/view.php?manufacturer=Toshiba)
If you cannot find one then you have to recompile and repair the BIOS yourself. (slightly complex)

I have recompiled peoples BIOSes before and had excellent results.
Just as a side not it is not actually the BIOS that gets recompiled but the ACPI code which the Linux kernel loads instead of loading from the BIOS so it doesn't affect the hardware.

-- edit --

A re read and a quick search revealed that someone had good results installing Ubuntu Intrepid on this laptop.
It could very well be the graphics drivers and not the BIOS thought the BIOS usually deals with fans and screen brightness.

---

### Post by Diablosblizz on 2009-10-14
CPU scaling is working, when on battery it goes from 800 MHz and up to 2GHz(when needed) as Windows did. When on AC power it's constantly on 2GHz (this is exactly how I want it).

I installed toshutils and it's giving me an error:

"required kernel toshiba support not enabled."

Whatever, the fan issue isn't a big deal I was just wondering what was wrong, and I don't know how to update my BIOS or kernal. The screensaver did limit the time so thank you!

---

### Post by P4man on 2009-10-14
> **Diablosblizz said:**
> CPU scaling is working, when on battery it goes from 800 MHz and up to 2GHz(when needed) as Windows did. When on AC power it's constantly on 2GHz (this is exactly how I want it).

I installed toshutils and it's giving me an error:

"required kernel toshiba support not enabled."

Whatever, the fan issue isn't a big deal I was just wondering what was wrong, and I don't know how to update my BIOS or kernal. The screensaver did limit the time so thank you!

After posting I noticed those thoshutils where like 6 years old, so I guess its not surprising not everything is working. There is another thing you can try, add 

```
acpi_osi="Linux"
```

as boot option. Detailed info on how to set this parameter in grub here:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

Note in the example in the link they set VGA=775 as boot option, replace that with the option I put above. I also think its case sensitive, so make sure you put an uppercase L in there.

If it works, you can follow the instructions on the next paragraph on the same page to make the change permanent (changing it through grub will only work once, for one boot, allowing you to test the setting).

---

### Post by Diablosblizz on 2009-10-15
That actually does the quite opposite of that expected. Instead of the fan going up and down in conjunction with the CPU scaling it just has one mode (it is spinning) but doesn't go any faster and I suppose the laptop would eventually overheat.

Thanks for the support, is there anything else I can try? If not, at least the fan DOES spin and even if it kills the battery quicker it's better than overheating in my books.

---

### Post by P4man on 2009-10-16
> **Diablosblizz said:**
> That actually does the quite opposite of that expected. Instead of the fan going up and down in conjunction with the CPU scaling it just has one mode (it is spinning) but doesn't go any faster and 


Are you sure ? fan speed shouldn't go up and down with cpu speed, it should go up and down with cpu temperature. Try playing a game for a while or something and see if the fan doesn't kick in higher gear after a while.

---

### Post by Diablosblizz on 2009-10-16
I played a flash game for about 20 minutes and the fan was not moving, though I could feel the air coming from the laptop get hotter.

---

### Post by lavinog on 2009-10-16
gpuscalling is disabled by default

[quote=man radeon]
 Option "DynamicClocks" "boolean"
              Enable dynamic clock scaling.  The on-chip clocks will scale dynamically based on usage. This can help reduce heat and increase battery life by reducing power usage.  Some  users  report
              reduced 3D performance with this enabled.  The default is off.
[/quote]

I am assuming you are using ubuntu 9.04

---

### Post by Diablosblizz on 2009-10-16
> **lavinog said:**
> I am assuming you are using ubuntu 9.04

Yep, until 9.10 comes out of course.

---

### Post by lavinog on 2009-10-16
here is a guide about it:
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features](http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features)

---

### Post by Diablosblizz on 2009-10-17
> **lavinog said:**
> here is a guide about it:
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features](http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features)

I'm not quite sure what you'd like me to do with this page?

---

### Post by lavinog on 2009-10-17
If you post your /etc/X11/xorg.conf I can show you how what to add.

---

### Post by Diablosblizz on 2009-10-18
> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

By any chance if this messes up my Computer, how would I get it back to normal?

---

### Post by lavinog on 2009-10-18
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
Identifier "Configured Video Device"
**Option "DynamicClocks" "on"**
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection 

```

add the bold line to your xorg.conf
you need to edit it as the super user:
```
gksudo gedit /etc/X11/xorg.conf

```
reboot
then post the output of:
```

grep -i 'dynamic' /var/log/Xorg.0.log

```

To undo it just remove the added line, or you can use:
```
sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Diablosblizz on 2009-10-18
Okay, going to sleep now but just wondering what is this trying to accomplish? I'm just wondering, I'll do it tomorrow morning. :)

Thank you.

---

### Post by lavinog on 2009-10-18
> just wondering what is this trying to accomplish?
...
> help reduce heat and increase battery life by reducing power usage.

---

### Post by Diablosblizz on 2009-10-18
I ended up not sleeping, but anyways here's what the grep -i... stuff outputted:

> (**) RADEON(0): Option "DynamicClocks" "on"
Dynamic clock gating enable success

Now, how should I really know if this is working? Will the fan stop reving high then never go back down?

Thanks for your support, one of the many reasons I love Ubuntu. Open-source ness and an awesome community! :D

---

### Post by lavinog on 2009-10-19
> **Diablosblizz said:**
> 
2. According to the resource monitor, I'm constantly using 25% of my CPU always. This would be okay if I was on a desktop, but this is a laptop and it needs to stay cool.


sometimes the resource monitor is a cpu hog.
install htop and use that to get a better indication of cpu usage.

---

### Post by lavinog on 2009-10-19
> **Diablosblizz said:**
> 
Now, how should I really know if this is working? Will the fan stop reving high then never go back down?


It should help, but I don't know of a sure test to see if it does.

---

### Post by Diablosblizz on 2009-10-19
So, I removed the added line. I ended up hibernating my laptop, coming back to nothing but a glitchy screen (worked before, and is working now) and had to go into recovery mode to repair it, it did it itself.

---

### Post by sabre2th on 2009-10-19
Just wanted to pop in with a little info...

I have an HP TX2500z with similar specs:

AMD Turion X2 @ 2.1 GHz
3GB DDR2 RAM
250GB HDD @ 5400 RPM
ATI Radeon HD 3200

My particular laptop is known to have heat issues and the fan actually runs quite a bit less in Ubuntu than it does in Windows (quieter... it never actually stops spinning).  This sounds like something specific to your setup.

---

### Post by Diablosblizz on 2009-10-19
The difference between mine and yours is the fan is working properly and the computer isn't overheating. I've had it over 80 celcius on Windows before, I know what's hot for it. :P

---

### Post by sabre2th on 2009-10-20
I've seen mine hit 96C running games in Windows, which is a bit scary.  Hot is not a problem for my computer...  You're right though; my fan does seem to work correctly.  It's just inadequate for the heat produced when doing very intensive things.

I just wanted to point out that it's not the flavor of Ubuntu that's causing your issues.  Your specs are more than enough to run plain old Gnome/Ubuntu (quite nicely, actually).  It seems to be something to do with your specific hardware.

It is odd that your CPU is constantly at 25%.  If you haven't already, add the CPU scaling panel applet and make sure it's set to 'On Demand'.  When mine is not set to that, the CPU doesn't slow down or constantly runs at slow speed, causing the fan to run more.

If that's not it, you can try a reinstall using the minimal CD and just install what you need (ie. the basic Gnome desktop).  That may stop the CPU from running so much.  If you need help with that, post back here and I can give you a hand.

---

### Post by Diablosblizz on 2009-10-20
The CPU usage seems to be from the resource monitor. I did a "top" and the top was 1% and it was Xorg.

---

### Post by peterwil on 2009-10-20
[LEFT][/LEFT]> **Diablosblizz said:**
> Hey, I've got a few things I'm just wondering about. Let's start off.

1. The fans constantly are on. I'm using a Toshiba L350D laptop, and the secondary fan (which isn't on all the time on Windows) is spinning fast and making a lot of noise. Is there something wrong, or am I using too much CPU that it has to kick in?

2. According to the resource monitor, I'm constantly using 25% of my CPU always. This would be okay if I was on a desktop, but this is a laptop and it needs to stay cool.

3. Is Ubuntu right for a laptop? I mean, is there a better Ubuntu (KUbuntu, XUbuntu) distro that would run better on my laptop and keep it cool?

Honestly, I just need it for typing documents and possibly sync it with my home machine (which is using Windows - but I'll get to that later). What is the Netbook Remix, and would it run better? Here's my specs:

AMD Turion X2 2.0 GHz dual core
3 GB DDR2 RAM
250GB HDD
ATI Raedon 1250X

4. Why is the minimum time for the monitor to turn off on battery power 11 minutes? That's pretty long if you're running on battery and want to conserve power.

Anyways, I hope to dive into some Linux distro, I'm just not sure which one yet. Ubuntu runs fine, but the heat and fan noise is a big problem for me, my fingers get sticky from the heat and it really peeves me off. Would xUbuntu lower the footprint and allow the fans to chill out?

Thank you very much.


I am going to save you some time here- I hope.
The key point is that there are numerous Toshiba Laptops that have exhibited this problem of overheating.
I struggled with this issue a few months ago. My machine is 
a Toshiba L305D-S5881 -bought new about 6 months ago.
Please see this thread( t=1036051) where it is fairly extensively detailed.
[http://ubuntuforums.org/showthread.php?t=1036051&highlight=peterwil&page=5](http://ubuntuforums.org/showthread.php?t=1036051&highlight=peterwil&page=5)

To make a long story short. You have a buggy dsdt due to the vendor using the microsoft aml compiler as opposed to the more stringent intel iasl compiler. Microsoft OS's workaround this problem and so the toshiba laptops seem to run nice and cool on Win. 
In my specific instance, recompiling the dsdt didnt make any difference to the heating.
On win ( preinstalled Vista ) using SIW I see temps in the range of 43C to 50C which is ok.
On hardy it started at 75C ( ie really hot ) so I quickly canned it after a few days and switched to Jaunty 9.0.4 where the temps are right around 55C.
( acpi -v  ).
I tried 
1) A recompiled dsdt
2) installing toshset utils and a whole buch of other stuff

-None seemed to produce an acceptable result.

Eventually after a few days of chasing various suggestions,
I was told to file a kernel bug and to try recompiling my kernel.
Being a developer I was amused at the suggestion and decided to do it right away.
I pulled down the src tree for kernel 2.6.30 and compiled it- Thankfully my laptop did not vaporize :)- I watched the temps go upto 79C and then back down to 50C. Then loaded this custom
image. The temps are distinctly lower now ie in the range of 48-56C, when I run my IDE + portal server. I haven't seen it spike enormously. This was about 4 months ago.

A few days I tuned back in to see if the kernel bug was fixed 
and  came across bug # 370173
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370173)
.

I hope this saga helps you understand what you are up against.
Good luck. If you do find an elegant solution to this problem with the net effect of the laptop running a cool 40C or so. please let me know. 

Cheers and regards
-pw

---

### Post by lavinog on 2009-10-20
> **Diablosblizz said:**
> The CPU usage seems to be from the resource monitor. I did a "top" and the top was 1% and it was Xorg.

[System monitor causes Xorg to consume 100% CPU](https://bugs.launchpad.net/bugs/187383)
I suspect it has a little to do with the way the graph uses bezier curves.

Hopefully it is fixed in 9.10, I haven't checked yet.

---

### Post by Diablosblizz on 2009-10-20
@peterwil

My fan is spinning. I have a CPU fan (which constantly spins on both Windows and Ubuntu - that's what I want) and the general fan which spins only when the laptop gets hot (Ubuntu it doesn't go back down, Windows obviously works fine). It seems that the fan revs high when needed, then slows down immediately. Example:

Watching Youtube Videos -> Fan goes to it's highest RMP -> Fan lowers down to a slower RMP (but still enough to push air) and doesn't move from here at all. No matter how hot I get the computer, the fan doesn't move up or down from this point. But the laptop is NOT overheating, I can feel warm air coming out of the vent, nothing burning just warm or cold, and I know what hot feels like. :)

@lavinog

That would be nice to see fixed, I think I had that issue in version 8 as well.


EDIT: Brightness IS working from the applet, although it does NOT work in Power management! Still, very glad that it is working!

---

### Post by Diablosblizz on 2009-10-21
Sorry for double post, but I'd like to update. I'd somewhat like to continue on with the GPU idea, for some reason I've got a feeling it's that. My laptop monitor is off, and it's been running for several hours like that and the air coming from the vent is warm, I'd figure it to be cool.

Also, this is kind of weird. At school today I had a wireless connection with 50% signal. At home right now I have 32% signal. At school, the wireless was constantly dropping (but there was no notice saying that it was dropping, it just stopped working and I still had 2 bars). At my house, with less network connection it's not dropping at all and internet is working fine.

What's going on here? I also get frequent drops at my schools wireless which I never did with Windows, mainly every minute it drops connection then I have to manually reconnect. Does 9.10, or will 9.10, contain better wireless support as did 8.10?

---

### Post by peterwil on 2009-10-21
> **Diablosblizz said:**
> @peterwil

My fan is spinning. I have a CPU fan (which constantly spins on both Windows and Ubuntu - that's what I want) and the general fan which spins only when the laptop gets hot (Ubuntu it doesn't go back down, Windows obviously works fine). It seems that the fan revs high when needed, then slows down immediately. Example:

Watching Youtube Videos -> Fan goes to it's highest RMP -> Fan lowers down to a slower RMP (but still enough to push air) and doesn't move from here at all. No matter how hot I get the computer, the fan doesn't move up or down from this point. But the laptop is NOT overheating, I can feel warm air coming out of the vent, nothing burning just warm or cold, and I know what hot feels like. :)

@lavinog

That would be nice to see fixed, I think I had that issue in version 8 as well.


EDIT: Brightness IS working from the applet, although it does NOT work in Power management! Still, very glad that it is working!

Ok may I suggest a couple of things to start with.
From a terminal window..Pl. post the output of
> acpi -V  

and   dmesg > dmesg_out.txt

Perhaps I could compare your dmesg_out.txt with mine.
Most likely your fan state will show off to start with as you boot up. 
Now some facts..
i) In hardy the fan stayed off until the temps shot up to 79C in about 10 mins of doing "nothing" ie.. gazing at a firefox browser window.

ii) On upgrade the temps were a bit better but still high.

iii) I compiled a custom 2.6.30 kernel ( jaunty released version was 2.6.28..) with toshiba_acpi options enabled.. This one seems to be doing a bit better in that 
  i) I have never had it go to shutdown 
  ii) I ran some really  intensive tasks(ie kernel compile) and the temps went up to about 78C and cooled off rather rapidly to 60C or so with the fans switching on.

My thermal zone settings are definitely being read by the kernel is there are nice log messages in /var/logs to indicate so.

Also if you could post the output of
>  uname -a  it would be helpful.

Hope this helps you. If you arrive at the same conclusion as I did ie needing to build a custom kernel.. send me a ping and I will point you to the right sources since your laptop is apparently similar to what I have. L305D -S5881.

Now if that still doesn't help we might have to patch the sources in your source tree and recompile to atleast switch the fan ON immediately after bootup.

Win Vista seems to do that in a convoluted way..They dont have 
explicit fan control drivers for this model. You can verify this 
by checking out Toshiba assist in the preloaded OS ie Vista.
There is nada on fan control settings in there. So all the spiel about RPMS and setting FAN speed do not apply to our esteemed model :-).

Also on the Vista side you might want to install SIW..and look at the rather cool settings of the CPU to convince yourself that this is potentially a Ubuntu OS issue.. Don't get me wrong Ubuntu is actually fantastic and hats off to all the fine devs.
on this team to produce a superp product but something as basic
as laptop overheating should be fixed right away else credibilty
as a viable OS on laptops would be in serious question.

Hope the info. in here is precise enough to help you run the laptop at slightly cooler temps. In Hardy I barely ran it for a few days and was about to completely remove it from my laptop when code curiosity got the better of me. I can safely run my laptop currently and wouldn't hesitate to leave it ON for hours on end.

Cheers.

---

### Post by Diablosblizz on 2009-10-21
> keith@keith-laptop:~$ acpi -v
The program 'acpi' is currently not installed.  You can install it by typing:
sudo apt-get install acpi
bash: acpi: command not found


"dmesg > dmesg_out.txt" does nothing.

> keith@keith-laptop:~$ uname -a
Linux keith-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

Does 9.10 have the 2.6.30 Kernal? Also, should I install ACPI? I'd like to add, the fan is working correctly in GRUB / boot screen for Ubuntu. If it revs high it goes back down to either being off or slowed down until needing to be off. It ALWAYS turns off before booting into Ubuntu completely. I'm also not sure if it's understood that this fan that runs high and doesn't go back down DID turn off in Windows, completely. It turned off until it was needed again.

MAJOR EDIT: So I was just reading up on some stuff and the fan was going at a higher pace, and it calmed down and it slowed down. It looks like the fan is somewhat working.

---

### Post by lavinog on 2009-10-22
> **Diablosblizz said:**
> "dmesg > dmesg_out.txt" does nothing.

It saved the output to dmesg_out.txt


> 

Also, this is kind of weird. At school today I had a wireless connection with 50% signal. At home right now I have 32% signal. At school, the wireless was constantly dropping (but there was no notice saying that it was dropping, it just stopped working and I still had 2 bars). At my house, with less network connection it's not dropping at all and internet is working fine.

What's going on here? I also get frequent drops at my schools wireless which I never did with Windows, mainly every minute it drops connection then I have to manually reconnect. Does 9.10, or will 9.10, contain better wireless support as did 8.10?


I have this problem in jaunty with my broadcom 4318 wireless.  I have read that many others are having a similar problem.  Unfortunatly this is not an easy thing to diagnose without specifics from the school.

I have noticed that this happens more frequently in populated areas of the school like the library where everyone is using a laptop, but it works fine in areas like a computer lab where there are only a small handful of laptops.

I haven't updated my laptop to karmic yet, but this is on my list of things to check on when i do.

---

### Post by peterwil on 2009-10-22
> **Diablosblizz said:**
> "dmesg > dmesg_out.txt" does nothing.



Does 9.10 have the 2.6.30 Kernal? Also, should I install ACPI? I'd like to add, the fan is working correctly in GRUB / boot screen for Ubuntu. If it revs high it goes back down to either being off or slowed down until needing to be off. It ALWAYS turns off before booting into Ubuntu completely. I'm also not sure if it's understood that this fan that runs high and doesn't go back down DID turn off in Windows, completely. It turned off until it was needed again.

MAJOR EDIT: So I was just reading up on some stuff and the fan was going at a higher pace, and it calmed down and it slowed down. It looks like the fan is somewhat working.

Some answers to your q's:

0) Your statements above are accurate. On booting the FAN state is OFF in Ubuntu but not so in Vista.
from a terminal  type in the following:
```
 cat /proc/acpi/fan/FAN1/state 
```
You will see it shows off.

1) 9.10 has 2.6.31. It is not clear to me that merely switching to 9.10
is going to alleviate your heating problem on your Toshiba laptop.
As mentioned before I am running a custom personally built kernel  currently which is behaving properly. :-)

2)Yes please install acpi .

Then run this from command line ie a terminal. with multiple firefox browsers open..

```
acpi -V
```.. Your output should look similar to..
-------------------------------------------------------
peter@neutrino:~$ acpi -V
     Battery 0: Unknown, 100%
     Battery 0: design capacity 4000 mAh, last full capacity 4064 mAh = 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 46.0 degrees C
     Cooling 0: LCD 1 of 7
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 0 of 1
-----------------------------------------------

Then do any compute intensive task ie watching a skype video that causes your laptop to blow hot air and run the same command again as above.


3) The output of dmesg is sent to dmesg_out.txt. Please open that file
see there are some statements in them and then attach it here.

The rest of the actions will depend on the outcome of 1,2,3.

Cheers

---

### Post by Diablosblizz on 2009-10-23
The fan indeed shows to be off, although it is on right now. Weird. ACPI -v shows:

> keith@keith-laptop:~$ acpi -v
acpi 1.2

Copyright (C) 2001 Grahame Bowland.
              2008 Michael Meskes.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

dmesg puts out: [http://pastebin.com/f71bbb2f6](http://pastebin.com/f71bbb2f6) (was too long, so instead of quoting it I pastebinned it, I hope that's okay).

Thank you.

---

### Post by peterwil on 2009-10-25
> **Diablosblizz said:**
> The fan indeed shows to be off, although it is on right now. Weird. ACPI -v shows:



dmesg puts out: [http://pastebin.com/f71bbb2f6](http://pastebin.com/f71bbb2f6) (was too long, so instead of quoting it I pastebinned it, I hope that's okay).

Thank you.
Apologies,
I meant to say 
```
 acpi -V ( not lower case ) 
```

To check your temps: 
you can use ```
  acpi -t  
```  as well.

From a quick look at your dmesg.. I see your temps at the time
was  59C. Also that your fan was registered.

Your kernel is the generic build. 2.6.28-12

. 
Please print the output of the temps under
1) With no load right after boot up. ie acpi -t

2) With slightly extreme processing as well.
Reason is.. 
We need to find out if your fan ever turns ON at all ?

If you think your fan is switching ON.. 
pl. print the temp at which it switched on.

also run ```
 cat /proc/acpi/fan/FAN1/state 
```
it should show ON when you think it has switched ON.
If indeed your fan never switches ON you may have 
your CPU burn and fry.

---

### Post by Diablosblizz on 2009-10-25
acpi -V:

> keith@keith-laptop:~$ acpi -V
     Battery 0: Charging, 80%, 00:20:39 until charged
     Battery 0: design capacity 4000 mAh, last full capacity 4912 mAh = 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 53.0 degrees C
     Cooling 0: LCD 0 of 7
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 0 of 1

acpi -t right after boot:
58 celcius

acpi -t after watching YouTube videos / listening to music / OpenOffice open / Gimp open (switched CPU scaling to max):

When the fan kicked in it was 75 celcius... after a few minutes of the fan running it has changed to 56. The fan is running! :D After a few more minutes the laptop is averaging in at about 50-60 celcius, which is great! The fan never turns off though. :P

The state of the fan still shows OFF, but I can hear it running and the temp of my laptop is going down (according to acpi -t).

---

### Post by peterwil on 2009-10-25
> **Diablosblizz said:**
> acpi -V:



acpi -t right after boot:
58 celcius

acpi -t after watching YouTube videos / listening to music / OpenOffice open / Gimp open (switched CPU scaling to max):

When the fan kicked in it was 75 celcius... after a few minutes of the fan running it has changed to 56. The fan is running! :D After a few more minutes the laptop is averaging in at about 50-60 celcius, which is great! The fan never turns off though. :P

The state of the fan still shows OFF, but I can hear it running and the temp of my laptop is going down (according to acpi -t).

Very good!. Looks like your laptop is doing ok.
The fact that the fan kicked in at 75C and then quickly brought down the temps to 55C or so is good. :-)

Also when you heard the fan switch on did you check
```
 cat /proc/acpi/fan/FAN1/state 
```
the output should have shown ON at that point 

I would keep an eye on the temps to make sure everything is ok.
Good luck..

---

### Post by Diablosblizz on 2009-10-25
The fan state was still OFF, as I stated in the previous post, and even with the fan on it NEVER turns back off which I'd like to happen if possible.

---

### Post by peterwil on 2009-10-28
> **Diablosblizz said:**
> The fan state was still OFF, as I stated in the previous post, and even with the fan on it NEVER turns back off which I'd like to happen if possible.

What bios  v are you running. Is it Insyde v 1.5.?
In WIN with the AC adapter plugged on the temps are 10deg higher.
There is no fan speed utility that allows control of the fan speeds for this laptop. Most likely this is a bios vendor issue.
However with the AC adapter not connected I see the fan speed
being increased periodically to bring the temps down from 58C to about 54C. So the OS seems to be handling the extra heat ok.

On Ubuntu this does NOT happen. The fan is ON but the state is being reported as OFF. And more interestingly I ran stress from a
command terminal and saw the temps shoot upto 78C with the fan
doing essentially NOTHING to cool it. I didn't wait to check if it sent it shutdown at 105C.
It is clear that the linux kernel (2.6.30) is not handling thermal trip points correctly by increasing the fan speed as required under heavy CPU processing load. 
Currently I run a small trivial script to keep an eye on the temps. 
The bug listed above when fixed in the newer kernel may resolve this issue. 
Until then if you are a developer you can try pulling down the sources from git and looking at the acpi modules.
Good luck..

---

### Post by Diablosblizz on 2010-03-31
I apologize for reviving such a old post, but I didn't feel like making a new one. So even though this problem is fixed, I was wondering if it is possible to get Ubuntu to show me the temperature in the panel (where the CPU scaling was located).

Thanks, and sorry for reviving again.

---

