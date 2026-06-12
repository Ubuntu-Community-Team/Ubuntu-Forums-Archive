---
title: "Ubuntu freezes AFTER Grub but BEFORE login"
date: 2009-11-06
forum: General Help
---

### Post by uselessness on 2009-11-06
Hello! I have had Ubuntu 9.04 installed for about 2 weeks now on my Compaq Presario V5000. I turned it off, left the house for a few days, came back. Now it freezes after the Grub 1.5 loading thing, but before login. Some weird looking stuff comes up on the screen, no text, just some graphic glitchy looking stuff... lines on the screen and such. It flashes three different things, and then won't work at all.

I can get into recovery mode, and I did all the little things there. I have dual boot XP set up, and I can get into/use XP just fine. I can boot into the Live CD. Let me know if more info is needed... thanks.

---

### Post by uselessness on 2009-11-08
Anyone?? I can't figure out how to research this because it's such a weird problem...

---

### Post by sveterv on 2009-11-08
You can hit ESC on grub menu screen (try to be fast:), then click "e", you will get to edit mode, now edit the line with "linux ..." at it beginning and delete "quiet splash" at the end. than hit "ctrl+x" to boot the system and look at which stage/module/information it hangs, look for error messages or something, than come back here and write what you've seen :)

---

### Post by 88marmon on 2009-11-08
I am having a similar problem with 9.10. First let me prefice this by saying I am a complete noob to Ubuntu. This is my first attempt at escaping the clutches of Bill Gates. 

I installed from a Live cd as a dual boot with xp. (xp still works ok) After installation, Ubuntu was working ok, and after a little playing around, decided I wanted the better window visual effects. It told me to install the nvidia 173 drivers set. After I did that, bootup locks after the grub menu. I get the nifty Ubuntu pulsating icon in the middle of the screen, then nothing. No display and no keyboard. The only exit is the reset button. I tried the above suggestion of using edit mode and it get to where is says something like "starting kernel ops..." or something like that. It disappears too fast to read it.

 I am thinking if I could just get the OS rolled back to before the driver install, I should be in business, but I can't figure out how to do that...

---

### Post by Druke on 2009-11-08
is [this]("http://ubuntuforums.org/showthread.php?t=1316305")  A related issue?

---

### Post by ranch hand on 2009-11-08
What happens if you try just booting to "recovery"?

---

### Post by 88marmon on 2009-11-08
> **Druke said:**
> is [this]("http://ubuntuforums.org/showthread.php?t=1316305")  A related issue?

I tried the steps outlined there, but only got a little farther to the battery state check. (this is a desktop pc.) After that the screen went blank and locked again.

> **ranch hand said:**
> What happens if you try just booting to "recovery"?
I will give that a shot right now.

---

### Post by 88marmon on 2009-11-08
> **ranch hand said:**
> What happens if you try just booting to "recovery"?

I can get to the recovery menu no problem, then I tried to resume the startup procedure and it went through a bunch of stuff, last thing being the battery state check, then finished with a prompt...

---

### Post by ranch hand on 2009-11-08
I would use a few of the options on the menu.  Broken packages for one.  If you are on a different machine and the other is still at the prompt, or if you end up there again, I would log in (user name and then password), and then run;
```

sudo start gdm

```
and see what happens.

---

### Post by 88marmon on 2009-11-08
> **ranch hand said:**
> I would use a few of the options on the menu.  Broken packages for one.  If you are on a different machine and the other is still at the prompt, or if you end up there again, I would log in (user name and then password), and then run;
```

sudo start gdm

```and see what happens.


"gdm start/running process 1737"

prompt.

---

### Post by ranch hand on 2009-11-08
You are going to have to get rid of the /etc/X11/xorg.conf file.  This should stop your driver from working.  9.10 does not have this file by default but generates on need, such as installing drivers, so this should get you in where you can get rid on the driver.  There is probably an easy way to do this from your terminal prompt, but I do not know what it is.  I have an ATI card and the generic is all I use as mine is not supported.

When you get back to the prompt try;
```

sudo remove /etc/X11/xorg.conf

```

---

### Post by uselessness on 2009-11-09
> **sveterv said:**
> You can hit ESC on grub menu screen (try to be fast:), then click "e", you will get to edit mode, now edit the line with "linux ..." at it beginning and delete "quiet splash" at the end. than hit "ctrl+x" to boot the system and look at which stage/module/information it hangs, look for error messages or something, than come back here and write what you've seen :)


It doesn't hang anywhere, it goes through all that stuff really quick, no errors that I can see, and then it freezes up with the weird graphical stuff. I am on 9.04, to all replies...

---

### Post by sveterv on 2009-11-09
Right, 9.04 :) OK I hope you didnt't delete your xorg.conf file as earlier mentioned, as this on 9.04 probably cause X to hang.

First, when you get to the end of boot (strange screen) try to switch to text console by pressing Ctrl+Alt+F1, than login and do a system update, there is a chance that there were some updates in this 2 weeks, and maybe your problem is solved, so type: "sudo apt-get update" and after packages list update type "sudo apt-get upgrade" to install eventually available updates. If there were ones, reboot, check if that helped.

If not, than tell us what graphics card you use? Nvidia, ATI, Intel? And then tell us do you use proprietary (binary) drivers for your graphics card or open source ones?
This look like a graphics card driver problem, so don't panic, system and your data is OK.

---

### Post by uselessness on 2009-11-09
> **sveterv said:**
> Right, 9.04 :) OK I hope you didnt't delete your xorg.conf file as earlier mentioned, as this on 9.04 probably cause X to hang.

First, when you get to the end of boot (strange screen) try to switch to text console by pressing Ctrl+Alt+F1, than login and do a system update, there is a chance that there were some updates in this 2 weeks, and maybe your problem is solved, so type: "sudo apt-get update" and after packages list update type "sudo apt-get upgrade" to install eventually available updates. If there were ones, reboot, check if that helped.

If not, than tell us what graphics card you use? Nvidia, ATI, Intel? And then tell us do you use proprietary (binary) drivers for your graphics card or open source ones?
This look like a graphics card driver problem, so don't panic, system and your data is OK.


Ctrl Alt F1 didn't work... ATI RADEON XPRESS 200M IGPis the graphics card and I did not install any drivers.

---

### Post by ranch hand on 2009-11-09
Darn tootin, 9.10 and 9.04 are different animals.  Do not remove the xorg.conf file from 9.04.

---

### Post by sveterv on 2009-11-09
> **uselessness said:**
> Ctrl Alt F1 didn't work... ATI RADEON XPRESS 200M IGPis the graphics card and I did not install any drivers.

That's bad :) These keys should be always available, it can mean that your system completely hangs. Are you also unable to restart it via Ctrl+Alt+Delete?

You've said you are able to boot in rescue mode, to which point you get there? Are you able to login to gnome?

---

### Post by frederikbjerreandersen on 2009-11-09
I'm having the same sort of problem in 9.10.

The freeze happens after Grub (I suppose - it shows the white ubuntu-logo on a black screen), but when the splashscreen is supposed to appear, the system halts. 

The first couple if times I tried, though, it show a narrow line of the brown splashscreen and a '¨busy' cursor....once I even got a narrow line of my desktop and the top of a message about a third party Google-application that needed to be confirmed (I use the Google sidebar and screenlets, but otherwise have no clue)...

...But for now, the screen just goes black...

I've tried and successed in repairing all packages in recovery mode. But no difference.

I've tried to delete the xorg.conf-file as suggested. But for me, the system says something like 'sudo: remove: command not found' - which I suppose means, that it does not recognize the action (?!)

help...?

---

### Post by ranch hand on 2009-11-09
try;
```

sudo -rm /etc/X11/xorg.conf

```

---

### Post by frederikbjerreandersen on 2009-11-09
thanks, but....I don't know if I should laugh or cry, be happy or dissapointed: when I turned the machine on again - without having made any changes since the last failed boot - the thing just logged in, nice and clean, to my desktop....

btw, the Google thing WAS a notice about a application for my desktop.... so no solution there, I guess...

---

### Post by uselessness on 2009-11-09
> **sveterv said:**
> That's bad :) These keys should be always available, it can mean that your system completely hangs. Are you also unable to restart it via Ctrl+Alt+Delete?

You've said you are able to boot in rescue mode, to which point you get there? Are you able to login to gnome?


Ctrl Alt Delete doesn't work either... I meant recovery mode, with the clean, dpkg, fsck options, etc. I tried all of those, also xfix. I don't know what rescue mode is, or about logging into gnome.

---

### Post by frederikbjerreandersen on 2009-11-09
...I was a little to fast there. The system registred the crash(es) and asked me to registrate it for the developers... as the boyscout I am, I did.... and suddenly the system became unstable again, the cursor only partly following my mouse-movement...

...after reboot, I am back to the old problem. I tried to remove xorg.conf with '-rm' as suggested, but after a reboot, there's no change. 

But, I'm able to login in text console and shift to the graphical interface with ctrl+F1 that way...only, the interface is just black with a frozen 'busy'-cursor on...

My graphic driver is an Nvidia Geforce (7600, i think). could that give a different solution?

---

### Post by ranch hand on 2009-11-09
I would get rid of the driver and then do a little research on what works best with 9.10.  I use the generic and have an ATI card to boot so I can't help you with the nvidia.  Get rid of the driver.  Stablise the system.

Then start on the driver issue.

---

### Post by sveterv on 2009-11-10
> **uselessness said:**
> Ctrl Alt Delete doesn't work either... I meant recovery mode, with the clean, dpkg, fsck options, etc. I tried all of those, also xfix. I don't know what rescue mode is, or about logging into gnome.

While in recovery mode, edit file /etc/X11/xorg.conf using text editor you are familiar with (pico, vim, mc), find [COLOR="Sienna"]Section "Device"[/COLOR], than edit the line in that section [COLOR="Sienna"]Driver "something"[/COLOR], and change "something" to "radeon" or "fglrx" depending what is there already, restart system, check if that helped. 

If there was "radeon" already, than simply changing to "fglrx" may not solve the problem, as this driver is not installed by default in the system, so you need to install it with "sudo apt-get install xorg-driver-fglrx" and only then restart system. I'm not a ATI user so it's a little hard to me find correct driver for your card, but what I see these two "radeon" or "fglrx" are most often mentioned. 

You should create a backup of your xorg.conf by simply copying it somewhere, before making any changes to this file, just to be sure if we mess something you'll be able to get back to old configuration.

---

### Post by sounddunk on 2009-11-10
[B]i had this problem a few days ago after i installed some ati drivers, got glitched graphics and a frozen screen after boot.  i found this and it worked ok for me. just uninstalls the drivers. good luck! ps with presario v5000



Re: Jaunty Won't Boot After ATI Driver Install[/B]             
                                                                I'm a brand new Ubuntu user and had exactly the same problem you describe today.

To fix I hit escape at boot up and dropped to command prompt

Then removed all fglrx drivers by typing:

**apt-get remove fglrx***

once removed I used **shutdown -r now** to restart and Ubuntu booted to desktop normally
                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                             [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7730851")                                                                                         [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7730851")

---

### Post by uselessness on 2009-11-14
> **sounddunk said:**
> [B]i had this problem a few days ago after i installed some ati drivers, got glitched graphics and a frozen screen after boot.  i found this and it worked ok for me. just uninstalls the drivers. good luck! ps with presario v5000



Re: Jaunty Won't Boot After ATI Driver Install[/B]             
                                                                I'm a brand new Ubuntu user and had exactly the same problem you describe today.

To fix I hit escape at boot up and dropped to command prompt

Then removed all fglrx drivers by typing:

**apt-get remove fglrx***

once removed I used **shutdown -r now** to restart and Ubuntu booted to desktop normally
                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                             [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7730851")                                                                                         [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7730851")



This worked everyone! Thanks!!

---

### Post by blegs38552 on 2009-11-14
I'm sure that some members of this board will regard this as the worst form of heresy, but I have had far less problems with my Windows 7 partition on my dual boot laptop than I am having with Ubuntu 9.10. These range from not being able to install using the dektop386 ISO (click on install, nothing happens and fails MDI hash test) and having to use the alternate CD instead, kernel panics when starting up, freeze ups ...etc. 

Hopefully, there will be patches that will make this a stable release. Fortunately, it is not my primary O/S - Windows 7 is, and all in all, I am happy with it. No crashes, fairly fast, considering that my laptop is no powerhouse, and my desktop is quite aged too. I have also found user communities that are just a helpful as those for Ubuntu.

Ubuntu is still a great way to learn Linux, and I am continuing to use it - just some more stability and reliability please.

---

### Post by suresnjain on 2009-11-20
same problem here.My system is dual boot.Grub loads o.k.,ubuntu starts,logo comes and goes away and then a focus light appears just like Mr Bean's movie begining.then it freezes.Do not know what to do?.Xp is working fine.Driver is Intel@945G

---

