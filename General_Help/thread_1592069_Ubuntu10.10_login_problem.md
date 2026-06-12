---
title: "Ubuntu10.10 login problem"
date: 2010-10-10
forum: General Help
---

### Post by afroze9 on 2010-10-10
hi
i just finished installing 10.10 on my pc. the problem is that i cant login to the desktop
i enter the password, the login sound plays and im stuck looking at the wallpaper. nothing else. i tried logging in safe mode and it worked. how can i get it to work normally?

pc specs in case they're needed

Pentium 4 2.6 ghz
512mb ram
ati radeon 9600 graphics card

and i installed it using wubi

---

### Post by bprins on 2010-10-10
ctrl-alt-f1 and log in. then you have terminal access

check your log-files. there must be an error somewhere.

check /var/log/Xorg.log
check /var/log/messages.log

if recovery mode is working, I'm guessing its a graphics device problem.

you have proprietary drivers installed?

---

### Post by afroze9 on 2010-10-10
let me check the log files
i dont think proprietary drivers are installed cause i just installed it and i think someone in the forum mentioned that ati 9600 driver was not supported after 8.04 or something
but i could at least run 10.04 although without the desktop effects

---

### Post by afroze9 on 2010-10-10
just checked the log files and didnt find anything suspicious and i think you misunderstood
i was referring to safe mode not recovery mode which i think is something different and the proprietary drivers arent installed

---

### Post by bprins on 2010-10-10
weird...

It strange that your PC boots without problems using safe mode, but doesn't boot properly in normal mode without even posting an error in log files.

You also don't have any errors during boot? some lines after grub is loaded but before you enter the ubuntu splash screen?

Alternatively you could try to enter terminal mode, and start gnome from there (sudo gdm start), where gdm is gnome desktop manager. maybe it's also possible to store it's terminal output in a file like:
sudo gdm start > ~/output.txt

Maybe that gives an answer?

Another way is to try KDE instead of gnome, but I don't think that is the path you want to walk.

Maybe others have some advice?

---

### Post by afroze9 on 2010-10-10
yeah there is something about the acpi thing but that exact same thing was present in 10.04 so i guess its not the real problem.
thanks anyway i guess i.ll have to stick with lucid till i get a better pc
the only reason i upgraded was because the chat thing doesnt work with proxy and i heard that it was fixed in 10.10. but thats for another day
thanks again

---

### Post by Tempster on 2010-10-11
I'm getting this same problem on a Compaq Presario 2100 laptop.  I was running ubuntu studio 10.4 lucid, upgraded to 10.10 with no errors.  But, when I login normally, all I get after logging in is the background screen, nothing else works.  I have to shut the machine off and restart and login in safe mode.  I've gone to terminal (from safe mode and in recovery console) and did apt-get check , update and upgrade.  I also went to drivers and found no extraordinary drivers show up.

Can someone suggest some other check to try to figure out what is the hang up with logging in normally?

---

### Post by afroze9 on 2010-10-11
is your graphics card also ati radeon 9600?
is there a way to turn off the desktop effects from the ctrl+alt+f1 thing?

---

### Post by Tempster on 2010-10-11
the specs on the video say "ATI Mobility Radeon"

---

### Post by mistypotato on 2010-10-11
Same problem after installing 10.10 fresh.  Compaq Presario 6300US intel OEM video card.

---

### Post by EndOn9 on 2010-10-12
I'm having the same issue on a ThinkPad R51e.

I find if I login to safe-mode first, then logout and login as normal it works though. What exactly does the system do differently when you login in safe mode? I notice there is no network manager.

---

### Post by ptiloo on 2010-11-07
Hi,

I have the same problem on my Presario 2100. In "normal mode", only the wallpaper is displayed. In "recovery mode", all is ok.

Does anyone have a solution?

---

### Post by Tempster on 2010-11-08
Since I wasn't able to find a solution to this problem, I logged in to safe mode and installed the KDE / Kubuntu desktop.  Kubuntu works fine on my Compaq Presario 2140.  

The only problem is that when I want to shutdown, shutdown only offers to logout of kubuntu.  Logging out of kubuntu takes me to the Ubuntu 10.10 login screen.  The button to shutdown Ubuntu is not always available.

---

### Post by ckomurlu on 2010-11-10
Hi,
   I got the same problem. When I logged in on Ubuntu 10.10 over Ubuntu Gnome Desktop *normal mode*, the top/bottom panels didn't appear at all and the right click menu didn't work, I got only the wallpaper, desktop icons neither. On the other hand, the safe mode was working flawless. I tried a workaround described [there]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html"). However, the cases are not the same. Panels appeared, but the right click menu has no motion.
   The specifications of my environment are such as: Nvidia Geforce4 MX 440 as the graphics card, Sony Multiscan E400 as the monitor, Ubuntu 10.10.
   A working driver for this graphics adapter has been released by Nvidia recently. Until then I had been using nv generic driver which had not been as performant as the original one. (Follow [this thread]("http://ubuntuforums.org/showthread.php?t=1592628") for details)
   Last night, the problem described here occured (several days after upgrading to Nvidia's driver, and I used Ubuntu in the meantime). I switched back to the previous driver via modifying /etc/X11/xorg.conf file. Now, the problem seems solved. I have no idea what is the relation between graphics driver and gnome environment's functions. Nevertheless this may give some clues to other people having the similar problem.

Cheers,

---

### Post by hkphooey on 2010-11-10
Also running a Thinkpad R51e. Fresh install of 10.10. Worked for a week or so but is now hanging at login. 

Safe mode works. 

I've tried disabling all the items in System > Preferences > Startup Items from Safe Mode, and then logging out, but still cannot login in Normal Mode. No errors in .xsession-errors

One thing that does seem to work -- oddly -- is taking the battery out before booting and running it off AC. Then I can boot into Normal Mode. 

So what might this be? My first thought was the Power Manager, so that's the first thing I disabled in System > Prefs > Startup Items. But that didn't fix it. Are there any grub command line alterations I can try?

---

### Post by hkphooey on 2010-11-10
Back again. Just found that adding 
noapic acpi=off 
to my grub boot parameters works. I can now boot in normal mode. 

Not entirely sure what this does, but the other person with the Thinkpad might be interested. 

More detailed instructions ... From a command prompt
```
sudo nano /etc/default/grub
```

Find the line which says 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

And change it to 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic acpi=off"
```

Run 
```
sudo update-grub
```

Reboot. If it doesn't work, then reverse the process.

---

### Post by edsdead on 2011-02-08
I have the same problem with my Compaq Presario 2199US laptop.  Your suggestion to turn off ACPI worked for me but disabled the power saving features for my processor which caused the laptop fan to run continuously at a high speed.  However, your ACPI suggestion steered me toward a better solution.  I'm using the following Linux kernel options in my GRUB configuration:

acpi=noirq pci=noacpi

Now my log in is fast AND my processor fan is quiet.

Thank you for your tip!

-ed.

---

### Post by hkphooey on 2011-02-09
acpi=noirq pci=noacpi

Cool. Thanks for the info. I'll remember that magic incantation. However, after my reply on this thread, it turns out that the next update to the kernel fixed it anyway. 

Unfortunately this has become too common a problem, with kernel updates every week or two. It doesn't matter in this case, as this is a second laptop for trying all this stuff out on, but if I was doing this in a corporate environment I'd probably wait until I hit a kernel that works, and lock it in Synaptic.

---

