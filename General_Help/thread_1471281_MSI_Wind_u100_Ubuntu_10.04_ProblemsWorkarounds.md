---
title: "MSI Wind u100 Ubuntu 10.04 Problems/Workarounds"
date: 2010-05-03
forum: General Help
---

### Post by dh04000 on 2010-05-03
Since the MSI Wind u100 and clones are so popular, I decided to make a separate thread devoted to its issues and workarounds. In order to get msi wind u100 users linked to here from google, I'm going to keyword the crap out of this thread. People say that users should contribute back, this is my way of doing so.


Alright Here's the Current Issues with the MSI Wind u100


MSI Wind u100 gnome power manager Issue 

Description: Hibernates when unplugged from AC

When started up with no AC, there is no issue, but when plugged in to AC and then unplugged from AC, the netbook mistakenly thinks the battery life/charge is less than 2%, and thus hibernates.

Bug Location: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/558627](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/558627)

Work Around: Press Alt-F2 and use the pop-up to launch gconf-editor.
Navigate to Apps / gnome-power-manager / general.
De-select the option use_time_for_policy.

No need to restart, just close the config editor



No Start Up Screen/Bootup Screen/Plymouth

Description: At start up there is black screen with flashing cursor and then a very short duration plymouth.

Launchpad Bug Location: [https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)

Workaround:

Code: gksu gedit /etc/initramfs-tools/conf.d/splash

and add this option FRAMEBUFFER=y, save the file.
Then

Code: sudo update-initramfs -u




Description:lock up randomly and the screen displays flashing blocks (mostly) on the right hand side over what was last displayed.

Launchpad Bug Location: Not Known

Workaround: Not Known




If any mod finds any more issues, or wants to sticky this thread, feel free to do whatever with it. I'll check it every day for updates. I hope the msi wind u100 can be fixed for a flawless experience, and this helps anyone with similar issues or raises awareness of these issues.

G'Day!

---

### Post by dartmusic on 2010-05-03
Thanks for starting this.

I'm also STILL experiencing the issue where the machine will lock up randomly and the screen displays flashing blocks (mostly) on the right hand side over what was last displayed.

ANY info on this would be great...can't seem to find anything via Google, etc.

Thanks!

---

### Post by Scarlet_Chantel on 2010-05-12
Thank you!  :)

---

### Post by dh04000 on 2010-05-12
Your welcome.

---

### Post by w1ll1am on 2010-05-18
Hello I have been using ubuntu since 9.04 and have and very few problems till the newest release I have an acer netbook and I decided that I would use the Ubuntu netbook edition. I was using the desktop edition of 9.10 before. Any way I am having a problem with my battery icon being displayed. When I start up it shows a lightning bolt but nothing  else then if I close the lid and then wake it back up the battery icon will be displayed and everything works until it says my battery is critically low, even if it's fully  charged. My computer will then hibernate because it thinks the computer is about to die. I don't have this problem with the desktop edition of Ubuntu 10.04 when booting it on the same computer. If anyone knows how to fix this please let me know. 

Acer Aspire-One 532h 
1gig ram
160gig hard drive
Ubuntu 10.04 LTS Netbook Edition
Windows XP Professional

---

### Post by coyogross on 2010-05-19
Hi there
I had installed 10.04 two weeks ago and I am really happy, at last I have found "THE ONE".
 I have the same problem with the startup logo, in addition i can see a really fast  screen with some lines does said something about a cheksum error, after that ubuntu starts up well.
I will like to ask you about something that i am no sure it is a problem. i have notice that the wind fan is really noisy now compare with other OS. Is this normal?

Thanks, Coyo

---

### Post by crlang13 on 2010-05-19
> **dartmusic said:**
> Thanks for starting this.

I'm also STILL experiencing the issue where the machine will lock up randomly and the screen displays flashing blocks (mostly) on the right hand side over what was last displayed.

ANY info on this would be great...can't seem to find anything via Google, etc.

Thanks!

On this issue, with a u123 atleast, I solved it in 9.10 with a bios update.  But, if you don't want to do that, I have heard, but not certain, that this issue was fixed in 10.04.

On the issue of wanting to hibernate when you disconnect from AC power.  I've found that when the prompt comes up, if I hit "OK" it hibernates, if I click "cancel" it just goes away...

---

### Post by chingdaotze on 2010-05-21
The splash screen bug is being tracked:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

And here is the solution that worked for me:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

It's right below this block of text:

"Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth. "

---

### Post by mediamind on 2010-07-07
> MSI Wind u100 gnome power manager Issue

Description: Hibernates when unplugged from AC

When started up with no AC, there is no issue, but when plugged in to AC and then unplugged from AC, the netbook mistakenly thinks the battery life/charge is less than 2%, and thus hibernates.

Bug Location: [https://bugs.launchpad.net/ubuntu/+s...er/+bug/558627](https://bugs.launchpad.net/ubuntu/+s...er/+bug/558627)

Work Around: Press Alt-F2 and use the pop-up to launch gconf-editor.
Navigate to Apps / gnome-power-manager / general.
De-select the option use_time_for_policy.

No need to restart, just close the config editor


No Start Up Screen/Bootup Screen/Plymouth

Description: At start up there is black screen with flashing cursor and then a very short duration plymouth.

Launchpad Bug Location: [https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)

Workaround:

Code: gksu gedit /etc/initramfs-tools/conf.d/splash

and add this option FRAMEBUFFER=y, save the file.
Then

Code: sudo update-initramfs -u

Thank you - this info was very helpful!

---

### Post by elmaska on 2010-07-22
Thanks a lot!!! That solved my problem with my Akoya E1210 battery!!!

You saved me from buying a new one without need!!!

---

### Post by oakeley on 2010-08-06
Dear all,

I tried the gconf editor option but the tick box for "use_time_for_policy" but it was already deselected. My problem is that my battery has full power and jumps from 7hrs to critically low from one moment to the next. It then hibernates, if I switch the machine back on then once again I see 7hr battery life, I work for 10 minutes and it repeats with the critically low message. If I keep playing this game until the battery level drops below 6 hrs then everything is fine and I can work without hibernation until the battery really is empty six hours later.

Please can you try to fix this as it is a bit annoying.

My computer: Acer Aspire One 532h, 2Gb RAM, 250 Gb SSD disk, Ubuntu 10.04 and Windoze 7.

Obviously this doesn't happen with Windoze and also not with 9.10

Edward

---

### Post by cryptor3 on 2010-08-06
I just installed 10.04 on my u100 earlier this week, and it will randomly lock up after anywhere from 15 minutes to an hour later.  

I don't experience any display corruption.  The machine just stops responding.

I'm dual booting with Windows XP SP3, and the machine is fine when running SP3.  memtest86 comes back passing.


edit: additional info: Currently running kernel 2.6.32-21-generic.

---

### Post by oakeley on 2010-08-07
Dear all,

Well I found a fix for the power management issue on the Asus Aspire 532h netbook under Ubuntu 10.04... First, the things that don't work: don't disable the acpi in grub2 as this will switch off your wireless card as well for some reason...

The solution: sudo apt-get install bum
This will add the option "startup applications" to the system settings. If you select this you can disable "power management" from the startup applications. This makes the computer work perfectly and it will now run for the full 7-8 hours on battery without suspending every two minutes.

Problems with this solution: you no longer get the battery icon so when the battery finally does die it does so rather suddenly but this actually isn't much different from the regular way.

It would be nice to have this bug with the power management solved for the acer as my hack is definitely not the "right way" to fix the problem. But at least it works.

If anyone has a better suggestion, please let me know!

Edward

---

### Post by Sturmeh on 2010-10-12
The splash screen issue still persists in 10.10, and the fix still works.

---

### Post by tjapko on 2011-03-13
I cannot upgrade to Ubuntu 10.10. It doesn't get past a terminal like login screen so gdm is not available. I have tried it several times.

The workaround gksu gedit /etc/intramfs-tools/conf.d/splash doesn't work: no screen appears to enter anything. Therefore a different problem.

A fresh install works but then I can no longer install Google Earth e.g. If I do it seems to install but nothing happens. If I uninstall a message appears that googleearth is not available for this type of computer.

Of course the power issue remains and has to be solved.

---

### Post by dh04000 on 2011-03-23
> **tjapko said:**
> I cannot upgrade to Ubuntu 10.10. It doesn't get past a terminal like login screen so gdm is not available. I have tried it several times.

The workaround gksu gedit /etc/intramfs-tools/conf.d/splash doesn't work: no screen appears to enter anything. Therefore a different problem.

A fresh install works but then I can no longer install Google Earth e.g. If I do it seems to install but nothing happens. If I uninstall a message appears that googleearth is not available for this type of computer.

Of course the power issue remains and has to be solved.

Post it here if you find any solutions.

---

### Post by kychot on 2011-04-01
> **coyogross said:**
> 
 i have notice that the wind fan is really noisy now compare with other OS. Is this normal?


I think this should be NOT normal! It's nerve-racking! Did you solve this problem yet? The processor is cold enough, it's temperature is 50 °C or less but the fan runs forever.__ I can't find any way to reduce it's rpm.  Any help please?  :confused:

---

### Post by dh04000 on 2011-04-01
> **kychot said:**
> I think this should be NOT normal! It's nerve-racking! Did you solve this problem yet? The processor is cold enough, it's temperature is 50 °C or less but the fan runs forever.__ I can't find any way to reduce it's rpm.  Any help please?  :confused:


Change your overclock back to 0%. Any overclocking of the msi wind u100 in the bios causes the fan to never shut down.

---

### Post by psychosibes on 2011-05-07
Thanks. My missus is running the full version of 11.04 on an MSI Wind U100 and had the hibernating problem when unplugging from mains power. Although the low battery message still appears momentarily on the screen after unplugging the machine no longer hibernates and when the battery icon is selected it says the correct charge. Yay!

---

### Post by NeverSage on 2011-08-28
I'm running 10.04 on my Wind U100 (2 gig ram). I'm having a video playback issue and I was wondering if anyone else is having the same problem. Youtube vids play fine in firefox. They're a little choppy in fullscreen but I can live with that. But I noticed that videos on collegehumor.com stutter so much as to be unwatchable, both fullscreen and normal. I'm wondering if I'm the only one who has this issue or if it's a fault with the collegehumor site. Can anyone confirm?  Thanks :)

---

### Post by for_serg on 2012-01-21
Problem with critical battery shutdown on MSI Wind U100 appears again, in Ubuntu 11.10. There is not "general" section in gconf-editor > gnome-power-manager anymore, so the fix published above cannot be applied anymore. 

UPD: Found a solution here - [http://askubuntu.com/questions/70877/battery-critically-low-at-85](http://askubuntu.com/questions/70877/battery-critically-low-at-85)

For 11.10 solution is to run:
```
gsettings set org.gnome.settings-daemon.plugins.power 'use-time-for-policy' 'false'
```

---

