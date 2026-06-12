---
title: "Ubuntu 10.10 stopped booting"
date: 2011-04-05
forum: General Help
---

### Post by amoeba801 on 2011-04-05
I now have 2 PCs that won't boot Ubuntu - with the same symptoms. One is an old desktop, the other a Toshiba Satellite U500 E5 laptop. The common spec: both running 10.10, both with NVIDIA graphics (almost certainly different GPUs), both running proprietary NVIDIA drivers.  They have been running 10.10 for a while with no issue: 6 months (desktop) and 3 months (laptop).

The machines now halt at some way into the boot sequence  - at the start of the Ubuntu splash screen (when GDM starts?). 

I'll focus on the laptop:
[LIST]
[*]2 days ago, the desktop froze on me, I tried to reboot and that's when the troubles started
[*]It dual boots with Windows 7, which boots and runs ok, suggesting hardware is ok.
[*]Other linux kernels in the grub menu do not boot (including recovery mode) 
[*]A Ubuntu 10.10 Live CD will not boot - freezing at the same place
[*]A GParted Live USB stick also hangs when booting in GParted Live Mode, in GParted Live safe (VGA) mode, and in Failsafe mode
[*]A Ubuntu 10.10 Alternative CD is working, but I stopped the repair when it asked what partition do I want to install grub (which one out of the 7 I have on the disk?)
[/LIST]

I'm downloading 10.4.2 Live to see if that will work, but since GParted isn't working, I'm not optimistic/

Any help in getting these PCs up and running would be appreciated.

---

### Post by Hedgehog1 on 2011-04-05
If you gave a single disk system, you want to install grub on the **/dev/sda** (not sda1 or 2 or 7, just /dev/sda).  This will keep grub as your dual-boot boot loader.

Have you attempted fsk repairs on your Ubuntu partition(s)?

***The Hedge***

:KS

---

### Post by lithopsian on 2011-04-05
The Ubuntu splash screen should appear way before GDM starts.  The splash screen disappears when GDM starts and, fingers crossed, your desktop appears shortly afterwards.  To get more info, you should turn splash off and turn quiet off, then you may see some error messages.

Very odd that even a Live CD hangs at the same place.  That suggests hardware issues, and not just a corrupt partition because that shouldn't stop the Live CD from booting.

---

### Post by Hedgehog1 on 2011-04-05
> **lithopsian said:**
> Very odd that even a Live CD hangs at the same place.  That suggests hardware issues, and not just a corrupt partition because that shouldn't stop the Live CD from booting.

The LiveCD/LiveUSB will try to use the Swap partition on the hard disk if it is there.  But other than that, I agree is it very strange that it also hangs in the same place.

If this second install attempt is not successful, can we ask you to boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Press the '#' button, and then paste the script results between the 'CODE' tags.

***The Hedge***

:KS

p.s. gparted refusing to run is not a promising sign...

---

### Post by 23dornot23d on 2011-04-05
It sounds like its another graphics issue search for this and you will find similar things ....
happening - one just solved recently was to alter 

> 
                                  **Re: Ubuntu 10.10 Installation, in Terminal?**             
                                                                [http://ubuntuforums.org/showthread.php?p=10331367](http://ubuntuforums.org/showthread.php?p=10331367)

That thread solved the issue.

'sudo nano /etc/modprobe.d/blacklist' opened a file and
'blacklist intel_ips' added the intel_ips module to the blacklist. 

It took out the driver for it and it said it was running on a low graphics setting -- I would need to manually change that. 

Thanks all for the help.
Good advice too

> 
  To get more info, you should turn splash off and turn quiet off, then you may see some error messages.
might be similar ..... but check some of the other reports too ......... and **check in your log files** ... 

cd /var/log/

then there may be some clues ......... if you can get to a terminal  ...... !!! ( ctrl+alt+f1 ) 

less kern.log
less Xorg.0.log
less jockey.log

---

### Post by amoeba801 on 2011-04-05
Wow, thanks for a great response guys, I'm a little overwhelmed with info, so it'll take a little with go though some of the ideas.

Some thoughts:

[LIST]
[*]I can access the log files on the Linux root partition from Win7, using ext2explore. I'll organise some info to post to the forum.

[*]I like the idea of using fsck to check the integrity of the partitions, just gotta find a non-graphical linux that will boot.

[*]hedge, not sure what you mean by selecting TRY during LiveCD boot.

[*]Agree that GDM is probably not the issue, more like X (or something else) issue prior to GDM.

[*]Remember that Win7 is working fine, so unlikely a HW issue.

[*]23dornot23d, I could try blacklisting the intel_ips driver, but why has it worked ok up until now? Also, I'm not sure how to blacklist, ext2explore on Win7 gives me read only to the linux root, an
[/LIST]d I haven't yet found another way to access it. 

keep the ideas flowing...

---

### Post by 23dornot23d on 2011-04-05
My thoughts are you probably updated at some point the way the graphics drivers load up got changed or updated .... that's maybe why they worked before but do not work now .....

This sounds like a wubi install too as you are accessing linux from windows ..... so I am out of my depth here as I know very little about windows as I have not used it since XP  ...........

---

### Post by amoeba801 on 2011-04-06
This is not a wubi setup, I have separate partitions for Win7 and Ubuntu & I use grub2 to boot...

During my investigations I noticed that wifi wasn't working in win7 either, not that I use wifi as a rule and the front hardware switch is set to off....

I set up a PuppyLinux LiveCD and I could see it freezing when loading kernel modules. I then set it to loglevel 7 during the boot and low and behold, it froze on loading the wifi module. I then stripped out the physical wifi module from the laptop, and hey, presto, Ubuntu is now working fine.

At least Win7 managed to continue with defective hardware, were as Ubuntu corked it badly.

So now I have to argue with Tosh to replace the module under warranty (and arguing that having Ubuntu on the hard disk does not cause the problem, nor void the warranty...) 

And next job, get the old desktop booting. The desktop doesn't have wifi, so it must be a different problem.

Case closed, for now.

---

### Post by 23dornot23d on 2011-04-06
Sometimes the wifi has to be turned on in the BIOS too ..... just a check before making a return to the shop .....
but if it was freezing then its probably worse than just a switch in the BIOS being set as off ........

Glad you got it sorted though ...... hope you get the wifi sorted too ...

---

