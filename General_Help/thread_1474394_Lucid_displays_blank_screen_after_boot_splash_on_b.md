---
title: "Lucid displays blank screen after boot splash on battery power."
date: 2010-05-06
forum: General Help
---

### Post by juniecho on 2010-05-06
Hi all,
I'm on **HP tx2000 Tablet PC**, with **nVidia GeForce 6150 Go** onboard, 4GB of RAM, Ubuntu 10.04 amd64 Desktop.

I keep getting a blank screen after boot splash when **I'm on BATTERY POWER.**
Though I get a blank screen, **the screen comes alive when I SUSPEND the laptop by closing the lid, and then RESUME** the laptop.
Then I can see the logon box and whole desktop.

This **does not happen with AC power**. Very strange.
Usually people get problem by suspending their laptops (usually the screen not coming back after resuming), but now I SOLVE the problem by suspending my laptop. Well like I said I can somehow get the screen right, but I really can't (and don't want to) suspend and resume my laptop every time I boot.

Need assistance.

Problem occurs **REGARDLESS of type of display driver** I use. nVidia proprietary, nouveau... whichever driver I use, I get the same conclusion.

Any help will be greatly appreciated.

---

### Post by KingJeremy on 2010-05-07
Aha! I'm having the exact same problem.  HP tx2110us tablet with the same specs you listed.  I thought maybe it was just me.  I'll keep checking in and monitoring this thread to see if any resolutions are found.

I tried all 3 proprietary drivers (96, 173, version current), along with the nvidia_current driver fix, and nothing's worked.  I hope this gets worked out.

Kudos to you on the suspend trick though.  I hadn't tried that, so I'll check that out if I ever have to go plugless.

---

### Post by cta16 on 2010-05-07
Same problem here. Can't boot up using battery power. I'm not sure if this is a coincidence or not but I'm also on a TX1120us.

---

### Post by juniecho on 2010-05-08
Anyone found solution yet?
I really can't figure it out.

---

### Post by t.h.w. on 2010-05-08
Same problem  here.... but when plugged in...

Did a upgrade on my notebook: no problems...

Did a fresh install on my laptop: Black Screen...
Reconfiguring x does not help.

Anyone?

Thanks!

---

### Post by dino99 on 2010-05-08
go ahead with more recent packages:

into synaptic, repo tab, add this ppa: [COLOR="Blue"]ppa:ubuntu-x-swat/x-updates[/COLOR], validate, update and upgrade

note: some old xorg.conf (from previous release) may cause issues, as lucid dont need xorg.conf it can be removed: sudo rm -f /etc/X11/xorg.conf, then sudo update-initramfs -u, and reboot

---

### Post by t.h.w. on 2010-05-08
> **dino99 said:**
> go ahead with more recent packages:

into synaptic, repo tab, add this ppa: [COLOR="Blue"]ppa:ubuntu-x-swat/x-updates[/COLOR], validate, update and upgrade

note: some old xorg.conf (from previous release) may cause issues, as lucid dont need xorg.conf it can be removed: sudo rm -f /etc/X11/xorg.conf, then sudo update-initramfs -u, and reboot


Hi!
Can you help me with the codes for the terminal? I am not  very familiar with the terminal as a newbie... Thanks!

---

### Post by Catharsis on 2010-05-08
> **t.h.w. said:**
> Hi!
Can you help me with the codes for the terminal? I am not  very familiar with the terminal as a newbie... Thanks!

dino99 showed you how to add the X-Updates PPA by hand, but if you were curious how to do it through the terminal:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
```

For the second part, you just enter the commands into a terminal.
```
sudo rm -f /etc/X11/xorg.conf
sudo update-initramfs -u
```

---

### Post by juniecho on 2010-05-09
Tried updating and it didn't help.
Still getting a blank screen on battery power.

I regenerated xorg.conf with sudo nvidia-xconfig, as nvidia driver uses xorg.conf I had no choice (or of course, drop nvidia driver but I haven't tried that)

*update: wait, please try going with synaptic(GUI). i tried updating with command line and it didn't update the kernel and some important packages. synaptic seems to be updating these. going to try once more with gui and i'll report back. thanks.

*update 2nd: **problem half-solved**, with xorg.conf GONE, ubuntu no longer displays blank screen after boot. however no luck with nvidia driver, and without xorg.conf it DOES NOT detect my screen resolution, which is 1280x800, instead it defaults to 1024x768. need help.

---

### Post by smistad on 2010-05-09
I can confirm this. I have the exact same problems on a similar computer (older version). I have tried the suggested solutions and still no luck.

---

### Post by Catharsis on 2010-05-09
Try booting with "nomodeset".
1) Hold down Shift while booting to get to grub.
2) Type 'e'. Then add "nomodeset" after "quiet splash".
3) Ctrl+x to boot.

---

### Post by jkorp on 2010-05-09
I have the same problem on a hp tx2010. I have tried nomodeset in grub, but it still happens (not sure if it is every time or just occationally.

Workaround for me is to close the lid to go to sleep mode for a few seconds, and then when opening the lid, screen is on.

---

### Post by t.h.w. on 2010-05-09
@ dino99 and Catharsis: Thanks for all the suggestions.

After fresh installing Lucid: a black screen. Finally, I could login to the prompt. 
Starting up in failsafe-X-mode didn't work either, so trying via synaptic was not an option for me... I gave up and installed 9.10 again: Everything worksagain. Maybe I will try to upgrade via the update-manaer and see what happens. I'll post it here if I do so... But for now I am happy 9.10 is working fine...

Greetz!

---

### Post by juniecho on 2010-05-10
Well this is the first Ubuntu to detect my tablet out-of-the-box without losing my USB trackball, so downgrading is not an option for me. (and I use compiz so removing nvidia proprietary drivers is not an option for me either)

Anyone lucky? Or some other suggestions?

Do we have to wait for updates? Perhaps from nVidia?
I believe nvidia drivers use xorg.conf so it uses somewhat different approach from Lucid default, which does not utilize xorg.conf.

---

### Post by comet on 2010-05-11
Hey guys. I'm having a similar problem with my older Gateway M520CS Laptop. It has ran every version of Ubuntu just fine up until now. I've burned about 4 CD's on different computers thinking that the disk was somehow defective. Basically, when I tried to load the graphical installer it simply goes to a blank black screen right after the splash screen.

Turning acpi off and trying various other boot options does no good. 

I was able to use the alternate installer to get Ubuntu to install, however when it tries to boot up for the first time, it goes right back to that blank black screen after the first initial splash screen.

What a bummer :( Never had an Ubuntu install go so bad and I've been using this since way back.

---

### Post by lazyfirecloud on 2010-05-11
Same problem with a TX1400us. Did anyone file a bug report? I don't think it's a coincidence that so many people with similar laptops have the same issue.

---

### Post by juniecho on 2010-05-17
Should I file a bug report?
Actually I've never done so before, is there anything I should consider when filing a bug report? Please advise.

---

### Post by Catharsis on 2010-05-17
Make sure you check launchpad.net first to make sure you're not filing a duplicate bug report. If not:
```
ubuntu-bug xserver-xorg
```

---

### Post by hellobogart on 2010-05-25
I have an HP TX2028au tablet PC and have the same experience. So when I boot on battery, I wait for the drum sound which means it is on the login screen, then hit the suspend button and wake up the computer via the touchpad just to make the screen appear.  :(

---

### Post by brit22 on 2010-07-03
There is a bug filed in Launchpad for this ...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578119)

Anyone find out anything more on this problem?  I also have it on a HP tx2000.

---

### Post by flipg40 on 2010-08-14
Okay... I have a HP tx2110us. I have the same problem but with one difference I do not even get a splash screen. I know it comes to a sign in prompt because it plays the music and i hit enter and sign in it plays the next login music. I have not shut the screen and reopened it. 

One thing I did notice, booting using the USB I have NO issues. It can run on battery and boot directly in to a usable GUI. Like everyone else I've reinstalled the drivers without success.

In my xorg config I do have an unknown monitor. This is strange. Any suggestions or is anyone else seeing this?

---

### Post by flipg40 on 2010-08-15
I put my old HDD back in this laptop. The reason I pulled it out is because of a certain problem with the screen going to a multi color instead of black. I did the following. 
1) Pressed shift to get a grub menu. 
2) Selected the kernel that will allow repair
3) The next menu (I forget what the heading was) I selected to repair using dpkg.
4) After repair I then selected the option to boot using low graphics mode.
This got me in. After I got in I reinstalled the graphics driver using this [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) as my guide.

Now what happens is it will not show a boot splash at all, it flickers and discolors then gives me the signin. I'm going to compare some config files to see what the differences could be.

---

### Post by smartc on 2010-08-15
Glad to see I'm not the only one with this problem.  I have a TX1120us, older version of the same laptop folks seem to have problems with...  I haven't found a solution yet, but I can offer that hitting CTRL-ALT-F7 at the blank login screen is a viable workaround without putting the machine to sleep.

I'll be watching this thread with interest and will post any solutions I may eventually come across if they don't come from here.

---

### Post by juniecho on 2010-10-14
I tried 10.10 and I can confirm that this issue is HALF FIXED.

With default graphic driver (nouveau) it WORKS flawlessly.
However with nvidia proprietary driver I can see this is not solved.

I'm downloading the newest version to try (version 260.19.12), will post result soon.


UPDATE: I can confirm that problem is NOT fixed with nvidia's latest driver either.

Current solution would be... sticking to nouveau.

---

### Post by jkorp on 2010-10-16
I also do not get nvidia proprietary driver to work. Still blank screen on battery boot. 

Are there any limitations using nouveau instead? Haven't tried it yet...

---

### Post by brit22 on 2010-10-28
After some more testing, I got my tx2000 to boot off battery through to the Gnome desktop.

see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578119) for the details.

However this was with a mainline kernel and only for testing, so it's not a solution yet.  But I hope this will move things along a little bit.

---

