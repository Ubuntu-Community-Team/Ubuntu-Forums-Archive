---
title: "Netbook Battery Life 1 hour in 10.04"
date: 2010-04-30
forum: General Help
---

### Post by A.Scotchmer on 2010-04-30
Hi

Installed Lucid netbook-remix on my Aspire One with SSD and 3 cell battery last night.

Under 9.10 I got 2hr 15mins with wifi and up to 3hr without wifi.

This morning on the train to work I booted the new release only to find that without wifi I'm now getting only 1hr 20mins battery life (fully charged battery).  

I have the brightness turned down low to try and save a little power but it makes no difference.

What can I do.  As this is a netbook-remix release having just over an hour of battery life is plain awful and impractical.

Any suggestions to increase battery life?

---

### Post by mikewhatever on 2010-04-30
Is the 1 hour an estimate, or did you actually time it? Use powertop to see what's using power.

---

### Post by A.Scotchmer on 2010-04-30
For both measurements I used the battery icon in the panel.  9.10 would say over 2 hours, sometimes nearly 3 on full charge, now it says 1hr 20.  

It reduces correctly - ie after 5 minutes it says 1hr 15.

---

### Post by mikewhatever on 2010-04-30
So there is no data on the real battery life for both 9.10 and 10.04, right?

---

### Post by A.Scotchmer on 2010-04-30
No but in 9.10 I always found the icon in the panel to be pretty accurate so I have no reason to doubt 10.04's monitoring of battery life to be any different.

I was using it on the train this morning though and from full charge, by the time I was getting to work the icon and the information it gave was showing that the battery was getting fairly low with only half an hour remaining (my train journey is just under one hour) and it had been consistenly dropping on route.

For this reason I can only assume that it is reliable.

---

### Post by mikewhatever on 2010-04-30
Will you run *sudo powertop* and post the output?

---

### Post by A.Scotchmer on 2010-05-01
Okay I installed Powertop and the output is below.

By the way, I left the netbook run down completely from a full charge and I only get 1hr 40mins. I've now recharged to 100% and still the icon in the notification area still says 1hr 40mins.  

And I'm not thrashing it.  I just have wifi on, firefox and openoffice writer open. 

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 9.7%)         1.60 Ghz     0.7%
polling           0.0ms ( 0.0%)         1333 Mhz     0.0%
C1 halt           0.0ms ( 0.0%)         1066 Mhz     0.0%
C2                0.3ms ( 0.3%)          800 Mhz    99.3%
C3                1.6ms (90.0%)

Wakeups-from-idle per second : 575.8    interval: 10.0s
Power usage (ACPI estimate): 9.1W (0.6 hours) (long term: 11.3W,/0.4h)

Top causes for wakeups:
  49.8% (371.3)   PS/2 keyboard/mouse/touchpad interrupt
  17.5% (130.8)D  firefox-bin
  13.7% (101.8)   [extra timer interrupt]
  10.1% ( 75.3)   [kernel scheduler] Load balancing tick
   4.0% ( 29.9)   [Rescheduling interrupts] <kernel IPI>
   1.3% (  9.9)   ubuntuone-syncd
   1.2% (  8.6)   [uhci_hcd:usb4, ath] <interrupt>
   0.7% (  5.1)   Xorg
   0.7% (  5.0)   syndaemon
   0.3% (  2.0)   gnome-terminal
   0.1% (  1.0)   gvfs-afc-volume
   0.1% (  0.9)   [kernel core] hrtimer_start (tick_sched_timer)
   0.1% (  0.7)   [ehci_hcd:usb1, uhci_hcd:usb2, i915, HDA Intel] <interrupt>
   0.1% (  0.5)   update-notifier

The program 'firefox-bin' is writing to file 'cookies.sqlite-journal' on /dev/sda1.
This prevents the disk from going to powersave mode.

---

### Post by A.Scotchmer on 2010-05-01
Today I reinstalled 9.10 nbr and the power icon was again showing 2hr 30mins.

I'm now using 10.04 desktop edition and its back down to 1hr 50mins (which is an improvement over the netbook edition).

So it has to be something wrong with the Lucid distro as with 9.10 the battery life is fine, or at least acceptable considering its only a 3 cell battery.

---

### Post by toshin696 on 2010-05-02
Oh men... I've an AAO D250. This have an normal HD and the battery life is the same of 9.10... so maybe ur battery is dying like mine :P ...  yeah my battery only charge and stop in 88% ... :(, but the life is the same in 10.01, 9.10 and XP...

---

### Post by utnubuuser on 2010-05-02
Did you add this:> The program 'firefox-bin' is writing to file 'cookies.sqlite-journal' on /dev/sda1.
This prevents the disk from going to powersave mode.or is it part of the output from Powertop? -- And is this the problem?

---

### Post by tgalati4 on 2010-05-02
With an SSD, I doubt that writing to a cookie file is going to use much more power than idle.  There could be indexing going on with the new install that could kill battery life for the first few hours.  Install htop and watch what is running.

sudo apt-get install htop
htop

---

### Post by A.Scotchmer on 2010-05-02
Could this is a possible cause?

I've just noticed that there is no decrease in brightness when I go onto battery power.  Just added the brightness applet to the panel and it says "cannot get laptop panel brightness."  Also the slider doesn't move so I cannot manually lower brightness.

---

### Post by XubeNoob on 2010-05-02
Hi Scotchmer,

I have an Aspire One (ZG5) with SSD. With UNE 10.04 just installed I can adjust display brightness with Fn-Left and Fn-Right, but I'm also getting the backlight dimming when power is unplugged.

I'll be interested in how the battery life question is resolved.

XubeNoob

---

### Post by happydan on 2010-05-06
I have a Dell Mini 9 and UNR 9.10 used to give me around seven hours of battery life. With 10.04, that has pretty much halved. I am surprised at such a dramatic change! Am I missing something?

---

### Post by A.Scotchmer on 2010-05-06
This is exactly what I'm finding happydan.  10.04 is cutting the battery life in half.

---

### Post by dino99 on 2010-05-06
you might report on launchpad: ubuntu-bug linux

---

### Post by bogoliubov on 2010-05-06
On my Aspire One ZG5 I noticed that laptopmode was no longer enabled after upgrading from 9.10 to 10.04. This had large effects no my battery life. Perhaps you have the same problem?

---

### Post by DomesDKG on 2010-05-06
I've also noticed considerable battery life reduction upgrading to 10.4.  There have been other posts on the forums to this effect as well, it would seem this is a buy in 10.4?

---

### Post by A.Scotchmer on 2010-05-06
Now we're getting somewhere.  Googling laptop mode I found this website: [http://www.cyberciti.biz/faq/linux-laptop-power-saving](http://www.cyberciti.biz/faq/linux-laptop-power-saving)

Using the command - cat /proc/sys/vm/laptop_mode I get 0 returned.

So I am not in laptop mode.

Next I used the command - sudo echo 5 > /proc/sys/vm/laptop_mode

but I get "Permission denied" returned.  What!!  I am using sudo to get root privilages.  How can permission be denied root????

So I try and be clever and type - gksu gedit /proc/sys/vm/laptop_mode and manually change the 0 to another number.

Now it tells me "Could not save the file /proc/sys/vm/laptop_mode.  Unexpected error: Error writing to file: Invalid argument"

So lets get this straight - Ubuntu 10.04 netbook edition, the edition that specifically targets netbooks, does not switch on laptop mode by default and what's worse doesn't allow even root to switch it on!!!!

Are we sure Cannonical hasn't been bought out by Bill Gates?

---

### Post by A.Scotchmer on 2010-05-06
SOLVED

The above commands do actually work despite the warnings and "Permission denied."

I have rebooted and now laptop mode is showing 5 and my battery has over 2 hours life remaining.

I still think it's daft that by default laptop mode is disabled in the netbook edition though.

Thanks DomesDKG

---

### Post by cimh on 2010-05-06
Yes I agree that 10.04 is very poor on battery life on my eee 901.

Although I'm in powersave my cpus are always on 1.6g powertop shows 11-12w  and 500wakes/sec from kernel scheduler load balancer tick - so in my case I think thats the problem. Funny thing is I'm only noticing this since a fresh install of the finshed version. didnt seem to be there in the alphas and beta - 

Its a shame as I like ubuntu but unless this can be solved I'll have to ditch it.

I'm not getting the same with lubuntu power consumption there is 8.1 - 8.9w. and load balancer wake ups are just 30-60/s.

cimh
901

---

### Post by hugmenot on 2010-05-06
> **A.Scotchmer said:**
> Next I used the command - sudo echo 5 > /proc/sys/vm/laptop_mode

but I get "Permission denied" returned.  What!!  I am using sudo to get root privilages.  How can permission be denied root????
?

Basic shell logic. Everything after the > redirect is not performed as root anymore. You echo as root and then want to redirect it to the file as yourself.

use this instead

```
echo 5 | sudo tee /proc/sys/vm/laptop_mode
```

Btw, procfs values are reset after a reboot.

---

### Post by bogoliubov on 2010-05-07
I think there is some setting in /etc/laptop-mode/laptop-mode.conf to enable laptop mode (when on battery) instead of enabling it manually. 

Then look through the files in /etc/laptop-mode/conf.d/ . There you can tweak laptopmode quite a lot to save even more power! As always, make sure you can reset the settings should you run into problems...

---

### Post by biltong on 2010-05-08
I'm using Lucid UNR on my Samsung N140 and the battery has gone from 10 hours (with Koala) to 5 hours with Lucid.

**cat /proc/sys/vm/laptop_mode** gives me ** 0**

**sudo echo 5 > /proc/sys/vm/laptop_mode** works until I reboot.  
**echo 5 | sudo tee /proc/sys/vm/laptop_mode** does not change anything.
Manual edit of file also does not work.

Got any other ideas before I go back to Koala?

---

### Post by bogoliubov on 2010-05-09
> **biltong said:**
> I'm using Lucid UNR on my Samsung N140 and the battery has gone from 10 hours (with Koala) to 5 hours with Lucid.

**cat /proc/sys/vm/laptop_mode** gives me ** 0**

**sudo echo 5 > /proc/sys/vm/laptop_mode** works until I reboot.  
**echo 5 | sudo tee /proc/sys/vm/laptop_mode** does not change anything.
Manual edit of file also does not work.

Got any other ideas before I go back to Koala?

Did you edit /etc/laptop-mode/laptop-mode.conf ? And did you restart the computer afterwards?

---

### Post by chek2fire on 2010-05-09
Is not solved and the problem still exist. I have netbook 10.04 edition in a 1011 inpiron Dell and i have the same problem.
When i try to give this command

sudo echo 5 > /proc/sys/vm/laptop_mode 

it says that permission denied

i try to edit manual the /proc/sys/vm/laptop_mode and change it from 0 to 5 when i try to save it say again permission denied.
I try to do that in terminal safe mode or to login as root user but i have the same message.
I try this command 

echo 5 | sudo tee /proc/sys/vm/laptop_mode

that seems to work and change the /proc/sys/vm/laptop_mode  from 0 to 5 but..
when i try to reboot the system and login again i have the same 0 result.
If this is a problem do we have to create a launchpad bug report because this is very serious for a netbook edition.

---

### Post by biltong on 2010-05-09
After much searching I found out that Laptop_mode_tools are not installed by default.  Therefore Laptop_mode is not enabled.

After installing the Laptop_mode_tools I was able to start configuring.  Things look a bit better now.  Looks like this was a small "slip-up" with the netbook version.

---

### Post by chek2fire on 2010-05-09
One other thing that i have see is that netbook edition is not using laptop-mode-tools but pm-utils-powersave-policy.

---

### Post by chek2fire on 2010-05-09
> **biltong said:**
> After much searching I found out that Laptop_mode_tools are not installed by default.  Therefore Laptop_mode is not enabled.

After installing the Laptop_mode_tools I was able to start configuring.  Things look a bit better now.  Looks like this was a small "slip-up" with the netbook version.

Yes but laptop-mode-tools need to install and hall and i dont know if this is correct way to do that.

---

### Post by biltong on 2010-05-10
It might not be the right way (installing laptop-mode-tools and hal) but it sure does manage the power saving better.

---

### Post by jastonas on 2010-05-10
I also installed laptop-mode-tools and changed the value from 0 to 2. Now, any permanent way to change it to 5? And is that better?

---

### Post by chek2fire on 2010-05-11
> **biltong said:**
> It might not be the right way (installing laptop-mode-tools and hal) but it sure does manage the power saving better.

What time you have now in your netbook?

---

### Post by A.Scotchmer on 2010-05-11
I've removed the [SOLVED] from the title of this thread as the problem clearly isn't solved.  

What I thought had solved the problem clearly hasn't.  I have made some adjustments such as turning off bluetooth etc and got a little more juice from the battery, but nothing like what I had before.

Going to try the laptop-mode-tools and see how that goes.  Something tells me this version was rushed out before the proper checks were carried out.

---

### Post by biltong on 2010-05-11
> **chek2fire said:**
> What time you have now in your netbook?

I'm getting 8 hours now. :P There are some more tweaking options (Samsung Tools) which I am going to play around with.  I sure I can win another hour or two.

I'm sure the Ubuntu team will come up with a suitable fix.  Pity it did not work from the start... now we have to listen to stuff like this ... [http://digitizor.com/2010/05/06/windows-7-more-power-ubuntu-lucid/](http://digitizor.com/2010/05/06/windows-7-more-power-ubuntu-lucid/)

---

### Post by isbiyanto on 2010-05-12
> **chek2fire said:**
> One other thing that i have see is that netbook edition is not using laptop-mode-tools but pm-utils-powersave-policy.

yeah... i think so...

---

### Post by isbiyanto on 2010-05-12
thanks all for sharing

---

### Post by chek2fire on 2010-05-12
i have try this tools but i think i have the same power manager. I dont see any improvement with power management.

---

### Post by A.Scotchmer on 2010-05-12
> **chek2fire said:**
> i have try this tools but i think i have the same power manager. I dont see any improvement with power management.
same is happening with me.  I tried the laptop-mode-tools last night but no improvement.

---

### Post by biltong on 2010-05-13
> **hugmenot said:**
> Basic shell logic. Everything after the > redirect is not performed as root anymore. You echo as root and then want to redirect it to the file as yourself.

use this instead

```
echo 5 | sudo tee /proc/sys/vm/laptop_mode
```

Btw, procfs values are reset after a reboot.

Ok, I have tried the following:
1.) Lucid Netbook install = Battery 5 hours :(
2.) Lucid Netbook install & install Laptop_Mode_Tools = Battery 8 hours :)
3.) Lucid Netbook install & enable Laptop_Mode (echo 5 | sudo tee /proc/sys/vm/laptop_mode) = 8 hours. :)

I can live with option 3. however as *hugmenot* mentioned the procfs values reset after reboot.  Is there a way to enable it permanently without having to run a script at startup?

---

### Post by vintageveloce on 2010-05-13
biltong,
Mind explaining exactly what you did in detail?
Did you uninstll pm-utils-powersave-policy?
Did you use the deb or ubuntu verstions of laptop mode tools? What rev?
Thanks,
Carl

---

### Post by Jimbo8098 on 2010-05-13
Your PS2/Keyboard and Touchpad seems quite high. Try disconnecting unneeded stuff from the laptop. Might help boots times.

---

### Post by BlitzkreigBop on 2010-05-18
I don't know if this helps, but I added the command to my start-up applications list.

(I'm a noob at Ubuntu and thats the first thing that came to mind.)

I'll update if it works or not once my battery is fully charged.

EDIT: Well everything seems a bit better now..

---

### Post by tushantin on 2010-05-20
Nah, doesn't work for me, despite adding the command to the startup. Still gives me 0, and the battery still lasts for only 1 hour 20 mins (without wifi).

HP Mini 210 (3 cell battery)
Lucid Lynx

Hasn't the problem with the UNE ISO's been resolved yet by Canonical? 

Weird thing is that the battery icon only shows the percentage of charging/discharging, and not the amount of time it'd take to discharge. I've calculated based on the old school "waiting" game.

---

### Post by tushantin on 2010-05-22
Bump (not really)

I saw this
[http://forum.eeeuser.com/viewtopic.php?id=85230](http://forum.eeeuser.com/viewtopic.php?id=85230)

> **Laptop_Mode?**

Thanks to the removal of HAL it  is a bit tricker to get Laptop_Mode_Tools installed.  Also there will be  a warning about removing the ""pm-utils-powersave-policy"  package"   which so far as I can tell can safely be ignored unless you were  planning on wrting your own power management scripts...

The  command you want is:

**Code:**

sudo apt-get install --no-install-recommends laptop-mode-tools sdparm ethtoolGonna try it today. :P



**EDIT:** Okay so I did that, uninstalling the power save thingy in exchange, without the need for installing Hal. 
**cat /proc/sys/vm/laptop_mode **gives me 2. Not sure if that's good or bad. Anything, mates?

---

### Post by adam_d on 2010-05-23
I'm not sure if this is related at all, but I just went ahead and installed 10.04 netbook remix on my Aspire one a110, all original, and after fixing a couple of issues it all seemed alright except for the battery life only being 50 minutes, and everytime I booted up I got a warning saying my battery was old or broken. I thought the short battery life was this problem as it was always around 2 hours on the old Linpus.

However, I needed to use it on battery power earlier, and I thought I would let it run right down so I could get a good charge in, as I haven't used it for a while. The battery estimated 50 mintes and went down from there. As it got to 9.9%, I got a low warning message from Ubuntu, but the low battery light on the netbook didn't light (in Linpus it came on at about 10%). The meter kept going down the 5.5%, and now there is no estimate, it just says 'Laptop battery discharging.' The thing is, it's been on that now for nearly 40 minutes, I still have no low battery light and it is still running. I have no idea how it's managing this, and if I check for laptop_mode, I get a value of 0. 

If this doesn't help at all, I'm sorry, I just thought it was a strange occurence that stems from what seems to be the same problem. :confused:

Edit: The battery charge graph has also stopped completely instead of flattening out, trying to show data from the last 10 minutes just shows no data to display. The time to empty graph however has flattened out and is still going.

Edit again: Battery light has just started to flash now, that's about 2 hours 20 minutes, about 1 hour 15 of those have been with Ubuntu telling me the battery was at 5.5% and battery meter empty and red. And the estimate dropped to 4.3% as the light started flashing. Actually, it now seems like it's working correctly again, it's dropped to 2.9% and the hibernate warning has appeared, and the graph is dropping again.

Final Edit: Added another picture to show the power monitor coming back to life again. So in my case it looks like the fault is with the battery monitor, and laptop mode is supposed to show 0. I got about 2 hours 30 minutes before hibernation, which is more than I got in Linpus. You can see in the 2nd graph the gap where it stopped, and then restarted as the last drops of power went from the battery. It also shows 1 hour to recharge, which is about right, so that appears ok. If I'm way off here and this doesn't help, I'm sorry.

---

### Post by tushantin on 2010-05-31
Hello? Anybody?

I recieved an update, so I thought "what the heck, it's just an update." Updated. Now although laptools are still in my system it's giving me 0 again. Netbook heats up pretty much. 

Damn, Lucid Lynx doesn't seem have the expected improvement towards netbooks. I'm gonna go back to Karmic...

---

### Post by Karachi123 on 2010-05-31
I don't know much about laptop's batteries. please let me know what is the age of average battery.

---

### Post by kleeman on 2010-05-31
There seem to be a lot of reports of laptops running hotter and battery life declining under Lucid. I have researched this thoroughly as I have two laptops (thinkpads) with this issue. I am beginning to think this is a kernel issue. If you run powertop with no apps open the main culprit for wakeups is

[kernel scheduler] Load balancing tick

It takes up 45% of the wakeups and is way too high. There is a bug open against this in launchpad:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/524281)

If you have upgraded from Karmic the old kernel may still be sitting on your system. Might be interesting to boot to this from the grub menu and see what happens.....

I have just confirmed on my system that this indeed is the issue (see bug report). I installed the last Karmic kernel (2.6.31-21) and the number of wakeups dropped dramatically by more than 50%. I am pretty sure this is the problem. If you want to try this download the kernel from here:

[http://packages.ubuntu.com/karmic-updates/i386/linux-image-2.6.31-21-generic/download](http://packages.ubuntu.com/karmic-updates/i386/linux-image-2.6.31-21-generic/download)

and install with 

sudo dpkg -i linux-image-2.6.31-21-generic_2.6.31-21.59_i386.deb

then reboot and select this option from the grub menu

Edit: I notice that the number of wakeups from this source is still high with the Karmic kernel so this fix is just a workaround and imho the kernel people need to fix this properly. The temperature on my thinkpad had dropped by 6C after reverting kernels. Hmmmm

Further update: This fix also works for my other Thinkpad (X300 and T60) in exactly the same way and another user confirms on launchpad already that this fix woirks. Suggests a widespread kernel problem.

---

### Post by chandearriba on 2010-06-01
Just bumping. An AAO d250 here and one hour of battery life approximately.

Powertop says this: 45,4% load balancing tick; this percentage fluctuates between 70% and 20% if I let powertop to go on. On the other hand, there's an "extra timer interrupt" sucking between 20 and 40%. And touchpad/keyboard/mouse PS/2 seems high too (up to 42,2%).

Powertop recomends
> echo 1 > /sys/module/snd_hda_intel/parameters/power_save. Of course, I'm not allowed to do that even sudoing.

---

### Post by A.Scotchmer on 2010-06-06
Getting frustrated with Ubuntu-Netbook I've installed Lubuntu 10.04 and everything is back to normal.  2 hours 20 mins with full charge.

---

### Post by colin.p on 2010-06-06
> **tgalati4 said:**
> With an SSD, I doubt that writing to a cookie file is going to use much more power than idle.  There could be indexing going on with the new install that could kill battery life for the first few hours.  Install htop and watch what is running.

sudo apt-get install htop
htop

This has absolutely nothing to do with a netbook, but I did notice that after a clean install of lucid, my CPU cycles would run quite high.
I was fairly concerned about that, but left it and after a week or so (I leave the computer on 24/7) it settled down. So maybe it is something to do with the way lucid works. I would have to say that this version is the best so far, even though I have only run ubuntu since intrepid.

Colin

---

### Post by NightwishFan on 2010-06-06
To echo a file you need to do:
```
sudo su
echo example > /etc/example
```

---

### Post by blekos on 2010-06-19
Hello,
although I managed to implement laptop tools
I found this [http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You](http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You)
easier to implement and handle.
The only catch is, if you have more than one core you need to specify the power state for each one (it only takes 10secs).

Pros: you can choose the cpu frequency as well.

Hope it helps

P.S do not forget to reduce your screen's brightness

---

### Post by tushantin on 2010-06-20
> **blekos said:**
> Hello,
although I managed to implement laptop tools
I found this [http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You](http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You)
easier to implement and handle.
The only catch is, if you have more than one core you need to specify the power state for each one (it only takes 10secs).

Pros: you can choose the cpu frequency as well.

Hope it helps

P.S do not forget to reduce your screen's brightness
Except if you're using UNE like me then you can't seem to add any panels (or at least find place to rightclick to add panels, that is)

Dammit! I really wonder why this UNE doesn't go to PowerSave mode by default! At least there shoulda been an easier to access option to it. I tried Echo, I tried changing the values, I also tried laptop_mode_tools (worked a bit, then stopped working after I updated the system), etc. Lappy's heating up. Hopefully Intel Atom doesn't get burned out.

---

### Post by tushantin on 2010-08-03
Just heads up for everyone using Lucid Netbook. Got this at Launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/582471](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/582471)

> [SIZE=3]acpi-support calls pm-powersave even when upower is running

[/SIZE]SRU justification:
On some hardware, calling pm-utils power.d scripts twice causes system crashes.
 Regression potential:
If I got this wrong, then in some cases users will have nothing  processing power events at all, which may result in the system being  left in "performance" mode while on battery.


Looks like the fix is still in Beta. But hell, it's about time! :D Anywhos most of you might want to wait until August 12 then upgrade to 10.04.1 since the fix "might" be released by then. Worth the wait. Thanks, Canonical!

---

### Post by tushantin on 2010-09-03
Okay updated to 10.04.1. Still killing my battery. No luck...

---

### Post by cloyd on 2010-09-03
The problem is not limited to UNR. I have the laptop edition on my Gateway netbook. I just don't like the netbook desktop; I like the standard desktop screen. Still, with laptop edition, I've had high temp issues and short battery life in Lucid. Different kernels have been better as far and temp goes, with 2.6.32-24 being the best so far as far. Battery life is still poor. With every upgrade, I'm hoping they've fixed it, but not yet.  But the 32.24 kernel was a big improvement. I have tried a 2.6.35 kernel, and a 2.6.36. Did not like the 35 at all, but the 36 was useful. Had some error messages on boot, but worked well just the same.

---

### Post by cimh on 2010-09-03
I'm running 10.10 a3 on my eee901. And I must say its all running very cool. powertop reports 8w, battery 4.4 hrs left at about 75% charge, cpu temp 40C, fans not running, getting about 320-400 wakes/s I'd like to see that a bit lower. but I'm very pleased. Cant remember what kernel they are on but its the std issue one.

I am running 'eee-control' a small package which gives control over fans, on board devices and chip speed. 

cimh
901 ubuntu, lubuntu & unr

---

### Post by tushantin on 2010-09-03
@cimh, did you recently upgrade your previous version to beta 10.10, or did you freshly installed it? If the former, I really can't wait for next month. :D

Initially I supposed it may have been pm-powersave / upower issue, but I'm not much of a tech guy (hell, I can't even remember code syntax and such). Even if it's done manually it'd be awesome to have some tips to fix this.

---

### Post by cimh on 2010-09-03
I did a fresh install of alpha2 and upgraded to alpha3 with synaptic. the beta comes out sept 2nd. I personally wouldnt worry about waiting. Have to say the alphas have been rock solid with no significant problems for me since alpha one. It all depends on what you use your netbook for. I dont keep many files on it its mostly used to access the net so its a simple matter just to dump the couple of GBs of documents / images onto a stick or sd card then reformat and install from a usb stick then reload my files. In fact I have 3 partitions one with ubuntu one with lubuntu and one with the UNR all in alpha stage. but the std ubuntu is my favourite the unr has lots of problems. Lubutnu is lighter and quicker - but there isnt much in it (I must check its power consumption)

of course you shouldnt rely on an alpha if its your main machine.

you could always run the alpha from a usb just to see what you think before installing. Or if you have enough space on your netbook - install it side by side in a separate partition so you can dual boot and compare 10.10 and 10.04. (I'm Not sure if you can decrease a partition with an os already on it to make room for 10.10 -it needs about 4-5G for the OS and 1-2+G more for your stuff.

cimh
eee901

---

### Post by cimh on 2010-09-03
I have just checked power consumption with LXDE alpha 3. It seems to be a little greener than ubuntu. powertop shows a consumption of 7.3W and wake ups are reduced quite a lot running between 60-90/s. A lot less than ubuntu.

I suppose that is to be expected as LXDE is designed to be lighter than gnome.

---

