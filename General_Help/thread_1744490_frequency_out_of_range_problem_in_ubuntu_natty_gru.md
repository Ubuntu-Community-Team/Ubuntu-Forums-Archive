---
title: "frequency out of range problem in ubuntu natty grub"
date: 2011-04-30
forum: General Help
---

### Post by princeofindia on 2011-04-30
The grub that is installed with ubuntu natty narwhal is not working on my system properly.My monitor(or cpu,I don't know it properly) gives me a message that the frequency is out of range and advises me to lower the resolution.I don't see the grub menu and the monitor turns off and starts again getting me directly into ubuntu desktop.I did a new complete reinstall from maverick.Can someone please tell me how to fix this problem.Any kind of help will be 
appreciated.

---

### Post by JgsDragon on 2011-04-30
I just had this problem too. It happened when I updated from 10.10 to 11.04 so that might be a good place to look for the solution...

What I did was I opened my Grub config in /etc/default/grub (You may need to open this with sudo with the following command: ```
sudo gedit /etc/default/grub
```)
Then find the line with
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640*400

```
Un-comment the last line and change it to a supported resolution for your monitor.
(I used 800*600, and pretty much any resolution below 1024*786 should work.)

Then the last thing you need to do is type ```
sudo update-grub
``` and it will automatically update your Grub configuration files.

---

### Post by heke on 2011-04-30
I met the very same problem when I uppdated from 10.10 to 11.04 yesterday . The monitor, an Acer AL2416W, reports "out of range" at bootstage, and at quitting. 

I will try the proposed solution.

UPPDATE: Thank you, the proposed solution did solve the problem!

---

### Post by ziojimmy on 2011-04-30
you're much more lucky than me if yours is just a chitty chatty annotation: right before entering the grub, my screen (a benq) just leaves me with that out of range message and i can't seem to adjust anything there's mounted on my hd.

---

### Post by perspectoff on 2011-04-30
> **JgsDragon said:**
> I just had this problem too. It happened when I updated from 10.10 to 11.04 so that might be a good place to look for the solution...

What I did was I opened my Grub config in /etc/default/grub (You may need to open this with sudo with the following command: ```
sudo gedit /etc/default/grub
```)
Then find the line with
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640*400

```
Un-comment the last line and change it to a supported resolution for your monitor.
(I used 800*600, and pretty much any resolution below 1024*786 should work.)

Then the last thing you need to do is type ```
sudo update-grub
``` and it will automatically update your Grub configuration files.

This worked for me on my system with an nVidia card only after I installed the proprietary drivers. Now it works ok for me. YMMV, I guess.

---

### Post by m8i9k on 2011-05-07
When I try to boot, monitor tells me something like "out of range". The computer does not shutdown or anything like this, but the message stays on the screen. I tried to chroot from live cd and edit grub settings (as written above). I rebooted it and it stays the same (still nothing happens). Does anyone have an idea what could be the problem?

Edit: Nevermind the above solution seems to have worked after all.

---

### Post by raziel09 on 2011-05-14
Apologies if this seems like a stupid question but how do you uncomment the line. I assume that you just remove the # from the beginning of the line; is that correct?

---

### Post by KIAaze on 2011-05-21
> **raziel09 said:**
> Apologies if this seems like a stupid question but how do you uncomment the line. I assume that you just remove the # from the beginning of the line; is that correct?
Yes, that's exactly what it means. :)

I had the same problem and the solution worked for me too. Thanks a lot. :)

---

### Post by raziel09 on 2011-05-21
Thanks for that - i have been using Linux for a while but only for the internet as i get to grips with it. Never really had to edit any files as everything has worked fine on my machine (see signature)

Thanks for the help

---

### Post by bullwinkle54 on 2011-06-18
> **JgsDragon said:**
> I just had this problem too. It happened when I updated from 10.10 to 11.04 so that might be a good place to look for the solution...

What I did was I opened my Grub config in /etc/default/grub (You may need to open this with sudo with the following command: ```
sudo gedit /etc/default/grub
```)
Then find the line with
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640*400

```
Un-comment the last line and change it to a supported resolution for your monitor.
(I used 800*600, and pretty much any resolution below 1024*786 should work.)

Then the last thing you need to do is type ```
sudo update-grub
``` and it will automatically update your Grub configuration files.

I also had this problem,  thanks for this solution.  I updated from 10.10 to 11.04 and after this fix it works great. I changed it to 1024x768 for my monitor.  It works for me.  :cool::cool:

---

### Post by OkieKnight on 2011-06-23
> **JgsDragon said:**
> I just had this problem too. It happened when I updated from 10.10 to 11.04 so that might be a good place to look for the solution...

What I did was I opened my Grub config in /etc/default/grub (You may need to open this with sudo with the following command: ```
sudo gedit /etc/default/grub
```)
Then find the line with
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640*400

```
Un-comment the last line and change it to a supported resolution for your monitor.
(I used 800*600, and pretty much any resolution below 1024*786 should work.)

Then the last thing you need to do is type ```
sudo update-grub
``` and it will automatically update your Grub configuration files.

I am having the same issue.  The fix above allows me to get to the sign in screen but when I sign in it get the out of range message again. can some one help??

---

### Post by KIAaze on 2011-06-24
> I am having the same issue. The fix above allows me to get to the sign in screen but when I sign in it get the out of range message again. can some one help?? 
And the login screen is ok?
Do you only get an out-of-range message and the screen is ok or is your screen unusable after login?

I think your problem is different than the one of the people here.
Setting the resolution in /etc/default/grub only affects the grub menu.

To change the resolution in Ubuntu itself, try system->preferences->display first:
[http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html)

Or use xrandr:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Your problem might also be driver-related eventually.
If you can boot into safe graphics / VESA mode from a live CD correctly, it's most likely driver-related.
You can enable/disable proprietary drivers (if any are available) in "system->administration->restricted drivers manager":
[http://cybernetnews.com/install-and-enable-restricted-drivers-in-ubuntu/](http://cybernetnews.com/install-and-enable-restricted-drivers-in-ubuntu/)
Non-proprietary drivers come with the various xserver-xorg-video* packages. If you had/have no problems with previous versions of Ubuntu, you might be able to fix the problem by downgrading to older versions. But report a bug on launchpad about it in this case.

_Tips to be able to use Ubuntu when having graphics problems:_
[LIST]
[*]You can choose recovery mode from the grub menu to get command-line access to your system.
[*]If you missed the grub menu, you can still hit ctrl+alt+Fn (Fn=F1,F2,etc) to get a terminal.
[*]Boot into safe graphics mode from a Live-CD: [https://help.ubuntu.com/community/BootOptions#Changing%20the%20CD%27s%20Default%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Changing%20the%20CD%27s%20Default%20Boot%20Options)
[*]And there should be a way to force vesa mode by default, but I couldn't find anything except the xforcevesa option mentioned here:
[http://www.piotrkrzyzek.com/enter-safe-graphics-mode-in-ubuntu-or-kubuntu-10-04-lucid-lynx-live-cd/](http://www.piotrkrzyzek.com/enter-safe-graphics-mode-in-ubuntu-or-kubuntu-10-04-lucid-lynx-live-cd/)
i.e. either edit the GRUB2 line from the menu or edit the grub2 config files to make it permanent.
[/LIST]

---

### Post by jpoblocki on 2011-09-14
I am having this same problem.  I have 10.10 installed do i update and then edit the grub BEFORE i reboot or what?

Linux newbie here sorry.

---

### Post by KIAaze on 2011-09-17
What do you mean by update? Upgrade from 10.10?

If you mean "sudo update-grub", then no, you first edit /etc/default/grub, then "sudo update-grub" and then when you reboot, the grub resolution should be ok.

Just follow the instructions here:
[http://ubuntuforums.org/showpost.php?p=10744804&postcount=2](http://ubuntuforums.org/showpost.php?p=10744804&postcount=2)

And obviously you have to reboot after that to see if it works.

As I said previously: This only solves resolution problems with GRUB, the boot menu, not with the login screen or after login.

---

### Post by zanaz on 2011-10-16
How is one supposed to fix this if they can't see anything? I sent my daughter a nice PC with Natty loaded on it. It ran great here during load and test on a 1400x900 resolution. She recievd it and it worked great on a 1280x1024 resolution on a different LCD. Then all the sudden the monitor just displayed the same "monitor out of frequency" problem.
 
Before I had read this thread I had her disconnect the monitor and try another monitor between reboots. Then I sent her another monitor that supported a much broader frequencey range and still the same problem.
 
The biggest delimea for me is that she lives 2000 miles away and It is not possible to connect through VPN because she is in a rural area that does not support high speed internet with any reliancy.
 
So without being able to see the screen, how would she fix the problem? 
 
All I can think of is reloading....

---

### Post by KIAaze on 2011-10-16
If the display problem is just with GRUB (i.e. the boot menu), she should be able to use Ubuntu normally after boot and fix the issue as specified earlier.
Otherwise, the problem is different and you should create another thread.

Also, the VGA mode (safe graphics mode) and recovery mode should still work I think.

Did the problem appear after an upgrade? In that case, downgrading the corresponding package (xserver something probably) might solve it and then you should report a bug at launchpad.

---

### Post by pvkarthik on 2011-11-01
> **m8i9k said:**
> When I try to boot, monitor tells me something like "out of range". The computer does not shutdown or anything like this, but the message stays on the screen. I tried to chroot from live cd and edit grub settings (as written above). I rebooted it and it stays the same (still nothing happens). Does anyone have an idea what could be the problem?

Edit: Nevermind the above solution seems to have worked after all.

Im also getting like this plz tel me any one how to fix this problem im waiting for your answer.....

---

### Post by DMcCunney on 2011-12-04
I'm having a different but related problem.  I have Ubuntu 11.10 installed on an old Fujitsu Lifebook p2110.  It was installed originally from an older version Minimal CD and upgraded in place.

The Lifebook has an 867mhz Transmeta CPU, 256MB RAM (of which the CPU grabs 16MB off the top for code morphing), and a 40GB UDMA 4 HD, multibooting Win2K Pro, Ubuntu, Puppy 4.31, and FreeDOS.  Video is handled by an onboard ATI Rage Pro Mobility chipset with 8MB video RAM.  Ubuntu properly recognizes the chipset's maximum 1280x768 resolution in 16bit color, and the GUI uses it.

The problem is character mode screens _not_ using the GUI.  I get a screen that is black text on a white background, and the text is garbled and unreadable.

If I go into the grub menu entry at boot time, and manually specify the boot commands including "set GFXMODE=1280x768", I see the character mode screen I expect, and I can switch to another display using Ctrl-Alt-F1 or the like and have a usable character mode session.

I followed directions elsewhere to update /etc/default/grub to uncomment the GRUB_GFXMODE line, and set the resolution the 1280x768, then did an update-grub operation to regenerate the grub.cfg file.  All appeared to work as expected, but when I rebooted and selected Ubuntu from the grub menu, I saw the same garbled character mode screen display I was trying to fix.  It works manually changing the boot options form the grub menu, but fails when it does it automatically.

Am I missing something, or have I been bitten by an 11.10 bug?
______
**Dennis**

---

### Post by isa.dsouza on 2012-09-15
Too Many Bugs with Ubuntu. Sure this fix gets rid of the black screen at login in, but the resolution on my system just goes berserk. everything is magnified, including the bootloader.

---

