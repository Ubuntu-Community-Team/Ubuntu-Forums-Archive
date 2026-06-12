---
title: "Karmic freeze in suspend - can't resume"
date: 2009-11-01
forum: General Help
---

### Post by HPEliteBook6930p on 2009-11-01
After upgrading to karmic and resolving my wifi issues with wicd, I've encountered ANOTHER problem - when I suspend, I cannot resume. the laptop comes out of suspend but the screen is blank (but with backlight) and I have to force a shutdown to use the computer. On restart, I am informed of a 'serious kernel error' during suspend.

I'd be happy to provide any logs if you want

Thanks in advance!!

---

### Post by MC707 on 2009-11-01
It's sad these problems still exist. My desktop computer, which actually *never* had suspend/hibernate problems, is now having that problem. ](*,)However, my laptop and netbook computers have actually been rid of that problem with karmic, my lappy and netbook actually previously having that problem with jaunty #-o

---

### Post by zsenike on 2009-11-03
Same probleme here :( Until Karmic Koala everything was OK . After a clean install don't know what is the problem. If I select suspend is working fine, but when I leave the system to go in sleep because of the power settings the system hangs. After that HDD and fans are working but the system doesn't recover. Keyboard and mouse is not responding. I need to reset/restart the system. Anybody ? :confused:

---

### Post by tseckler on 2009-11-03
Same problem on my desktop. I must do a hard quit.

---

### Post by mitchellcipriano on 2009-11-04
Same problem here. When I try to suspend my ThinkPad R51 it appears to go OK, but then the sleep LED starts flashing rapidly and I can tell the display never completely shuts down. Then when I try to resume nothing happens. At that point it requires a hard reboot and I get the kernel error message.

Prior to doing the upgrade on this notebook, I tried a clean install of 9.10 on a different machine and it worked flawlessly. This gave me the confidence to do the upgrade on my notebook that was running great with 9.04.

---

### Post by lelamal on 2009-11-04
> **mitchellcipriano said:**
> Same problem here. When I try to suspend my ThinkPad R51 it appears to go OK, but then the sleep LED starts flashing rapidly and I can tell the display never completely shuts down. Then when I try to resume nothing happens. At that point it requires a hard reboot and I get the kernel error message.

Prior to doing the upgrade on this notebook, I tried a clean install of 9.10 on a different machine and it worked flawlessly. This gave me the confidence to do the upgrade on my notebook that was running great with 9.04.

I have a Thinkpad R50e, and what you describe is partially familiar to me. I say *partially* because my laptop never actually suspends. It tries to, indeed, but then I see the flashing sleep indicator (the half moon) which is already weird per se, for it usually just lit and stay so throughout sleep mode. However, as anticipated, it won't sleep: instead, the fan will continue to run, and overall I can tell all applications are still running there, behind the black screen. Only, I can't access them, and the computer never responds to anything but a cold reboot. So, I can't actually resume anything. It may be for this reason that I have not received the kernel error warning as yet.

---

### Post by w1ntermute0 on 2009-11-08
I have this same problem on my thinkpad R50e on 9.10.  Suspend worked fine in 9.04 on same hardware.  I get the quickly flashing moon LED on suspend and system becomes totally unresponsive.  I haven't checked over the network yet to see if the system is still up, but that doesn't really matter, it's still unusable locally.  Have to hard boot the laptop to recover.  Really annoying - anyone find a fix yet?

---

### Post by smoosh on 2009-11-08
No suspend on Sony Vaio VGN-FW139E either.  arrrrg.

---

### Post by QuimO on 2009-11-08
Same problem for me after installing a fresh ubuntu 9.10: suspend can't resume.
Suspend was working good with ubuntu 8.04 until the installation of karmic in another partition. So the problem has relation with grub.
Fixed uninstalling grub2 and installing old grub. [Instruccions here]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")


Now my netbook can resume after suspend.

Good luck

---

### Post by lelamal on 2009-11-18
Hi all! I have just reported a bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/485108") on this issue. If you feel to be affected by the same bug, please feel free to add any relevant information that may lead to a quicker fix and a final solution.

---

### Post by RandyRandola on 2009-11-18
I had 8.04 on my machine and everything worked great. 

An update came and it looked good. Then a few more and when I tried Devede, it didn't work anymore. Around and around I went with no joy. I then thought I would wait on 9.10. It was only a few more weeks...

So I installed 9.10 and my Vista computer has now become my computer of choice.

9.10 hangs whenever it feels like it. There is no rhyme or reason and requires me turning the computer off at the switch. Devede still doesn't work and I am near to saying so long to Ubuntu. 

I hope they figure this out soon. Vista sucks but at leaat I can work on it.

---

### Post by karmakowski on 2009-11-20
I have the same problem with my Inspiron 600m, hibernate (suspend to disk) works like a charm but suspend (suspend to ram) results in a freeze when resumed.

---

### Post by monjope on 2009-11-23
Same problem on my Aspice 3690. I think it's the new kernel, because in Juanty the suspend/hibernation function works fine with 2.6.28, but in other distributions with kernel 2.6.31 (like Mandriva 2010 or Fedora 12) the system freeze too.

---

### Post by lelamal on 2009-11-23
> **monjope said:**
> Same problem on my Aspice 3690. I think it's the new kernel, because in Juanty the suspend/hibernation function works fine with 2.6.28, but in other distributions with kernel 2.6.31 (like Mandriva 2010 or Fedora 12) the system freeze too.

That's interesting. Let's hope the developers are aware of it!

---

### Post by linfidel on 2009-11-24
> **QuimO said:**
> Same problem for me after installing a fresh ubuntu 9.10: suspend can't resume.
Suspend was working good with ubuntu 8.04 until the installation of karmic in another partition. So the problem has relation with grub.
Fixed uninstalling grub2 and installing old grub. [Instruccions here]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")


Now my netbook can resume after suspend.

Good luck
I'm sure it's nothing to do with grub.  It's the kernel that grub boots.  The old grub boots the old kernel.  If you update the old grub to the new kernel, I'll bet you will have the same problem.

FWIW, I've never had any luck with suspend with any computer using Ubuntu.

---

### Post by smoosh on 2009-11-25
I had the same issue and I compiled a custom kernel using KernelCheck, and now it suspends every time with no issues. 

[http://launchpadlibrarian.net/35212126/kernelcheck_1.2.5-3_all.deb](http://launchpadlibrarian.net/35212126/kernelcheck_1.2.5-3_all.deb)

The above link is the version of KernelCheck that worked for me. Check it out, and hopefully it will work for you, too!

---

### Post by smoosh on 2009-12-07
Well, an update: I had other problems that I could not fix with the custom kernel like dropped wifi connections and no brightness control for my laptop. I even tried compiling a 2.6.32 kernel, and still no suspend. SO here's what works: Reinstall Jaunty. Everything is working great for me now with 9.04; suspend, brightness, AND wifi. Just sayin.

---

### Post by skalra63 on 2010-01-04
Just to let you know how my suspend/resume issue was resolved. Hopefully it will help others:

I had Karmic installed previously. I had the suspend/resume issue whereby on resume, all keyboard features become active but i only got a blank screen. I first followed the advice on this link [http://ubuntuforums.org/showthread.php?p=8434074](http://ubuntuforums.org/showthread.php?p=8434074) but it didn't seem to fix it. I couldn't find a resolution to this so gave up.

I then tried to update the ATI drivers but failed. I ended up without a GUI and had to use terminal. I did some research, installed ENVYNG-CORE and ran envyng -t and chose to uninstall the ATI driver. After this i had no resume issues from suspend. 

I recently reinstalled Karmic and had the same issue. I couldn't remember how i fixed it before so i had to start again. This involved following the link again. Again it didn't fix it. Then I remembered that one thing I did do was to use ENVYNG to uninstall the ATI driver.

I installed ENVYNG and used it to uninstall ATI driver. Now i can resume from suspend again.

I am not sure how and why the suspend issues were resolved by uninstalling the ATI driver. Maybe following that link also contributed.

it does mean that you cant enable desktop effects though

Hopefully this will help someone else. Also it might help developers to fix this bug.

---

### Post by lelamal on 2010-01-04
> **skalra63 said:**
> I installed ENVYNG and used it to uninstall ATI driver. Now i can resume from suspend again.

Thanks for sharing, and hopefully your workaround will help others, too. Unfortunately, no proprietary drivers are in use on my system, so I still can't use the suspend mode.

---

### Post by jamesisin on 2010-01-04
If the OP has seen resolution, please mark this thread as SOLVED (under Thread Tools above).

To those who are still seeing issues, I can suggest trying Hibernate as an alternative to Suspend (or vice versa) as this has worked for me in the past.

---

### Post by skalra63 on 2010-01-05
> **lelamal said:**
> Thanks for sharing, and hopefully your workaround will help others, too. Unfortunately, no proprietary drivers are in use on my system, so I still can't use the suspend mode.

Ielamal, I was using the default driver that Karmic installs for the xpress 1150, i think it is the radeon driver

---

### Post by lelamal on 2010-01-05
> **skalra63 said:**
> Ielamal, I was using the default driver that Karmic installs for the xpress 1150, i think it is the radeon driver

Sorry, skalra63, I didn't know much about the radeon driver, so I misunderstood. After researching, I wonder: if you uninstall the ATI driver, what will your system use for your video hardware? Is it safe to uninstall default drivers? I am not much concerned about not being able to run the desktop effects, I'm already on Metacity, but am uncomfortable in tweaking Ubuntu deviating from the default settings for I personally wouldn't know how to tackle unpredictable consequences or a drop in performance.

---

### Post by mammothx on 2010-01-07
Same issue here:

Conditions:
OS: 9.10 Karmic Koala (kernel(?) build 2.6.31-14 and/or 2.6.31-17) 
Video card: ATI RADEON XPRESS 200M IGP
Laptop: Compaq Presario v5101US

I downloaded and installed this distribution just 3 days ago. Suspend recovered just fine following password prompt after very brief OS testing. I ran Update Manager and updated everthing...now neither Suspend nor Hibernate works.

Issue:
Both Suspend and Hibernate fail to "recover." Suspend fails to recover after latest update. Power light flashes in suspend state. I hit the power button to recover, the power light fully illuminates...nothing happens...it fails to recover. Hibernate just fails to recover. It "kills" pc. I hit the power button to recover, the power light fully illuminates...it says "Waking up. Please wait..." then goes away...and nothing happens...it fails to recover.

Only a hard reset recovers from either state. :( Both occur upon manual execution  and lid close execution (power mgmt).

I also attempted **skalra63**'s suggestion of installing ENVYNG in a attempt to resolve, but the program does nothing. No execution, no process visible via "top"command...nothing.

---

### Post by linfidel on 2010-01-07
I didn't want to do away with the proprietary video driver and Compiz, so I set the lid close event to simply blank the screen, and I shut down the computer instead of suspending when on battery.  

Fortunately, Karmic starts up fairly quickly.

---

### Post by Jugney on 2010-01-10
The Launchpad bug report listed above had the fix for me - an SD card in my computer slot was preventing standy or hibernation. Go figure.

---

### Post by jamesisin on 2010-01-12
> **linfidel said:**
> I didn't want to do away with the proprietary video driver and Compiz, so I set the lid close event to simply blank the screen, and I shut down the computer instead of suspending when on battery.

Be careful with that as a solution because a laptop running with its lid down will produce more heat than it was designed to dissipate effectively.

---

### Post by llawwehttam on 2010-01-24
> **mammothx said:**
> Same issue here:

Conditions:
OS: 9.10 Karmic Koala (kernel(?) build 2.6.31-14 and/or 2.6.31-17) 
Video card: ATI RADEON XPRESS 200M IGP
Laptop: Compaq Presario v5101US

I downloaded and installed this distribution just 3 days ago. Suspend recovered just fine following password prompt after very brief OS testing. I ran Update Manager and updated everthing...now neither Suspend nor Hibernate works.

Issue:
Both Suspend and Hibernate fail to "recover." Suspend fails to recover after latest update. Power light flashes in suspend state. I hit the power button to recover, the power light fully illuminates...nothing happens...it fails to recover. Hibernate just fails to recover. It "kills" pc. I hit the power button to recover, the power light fully illuminates...it says "Waking up. Please wait..." then goes away...and nothing happens...it fails to recover.

Only a hard reset recovers from either state. :( Both occur upon manual execution  and lid close execution (power mgmt).

I also attempted **skalra63**'s suggestion of installing ENVYNG in a attempt to resolve, but the program does nothing. No execution, no process visible via "top"command...nothing.

This just happened to me on thursday. Suspend has been fine until now with 9.10 but when I ran updates on thursday I can suspend but cannot wake from it. I am just left with a blank screen.

Bit of a shame really as I just thought I was in the clear with computer problems.

EDIT: also since that update every time I boot up I now get a GRUB message saying that the / is not ready for a couple of seconds then It boots up. This never happened before.

---

### Post by BurgerKing on 2010-02-03
Anyone who's got the problem with the flashing half-moon when trying to go (not to resume) to suspend-to-ram or suspend-to-disk feel free to add his description/signing to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516294]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516294")

---

### Post by nhatmeister on 2010-03-17
I spent almost a week trying to get this to work ! I have a Dell Studio running ubuntu 9.10...I managed to get everything else working, except waking up from suspend... then someone on this forum said something about an SD card...AND that was IT !  thanks

---

### Post by vldmrrr on 2010-06-06
I had freeze on resume on dell inspiron 600m. The problem appears to be caused by radeon kernel module - once I switched Xorg to "vesa" driver, and blacklisted radeon module in /etc/modprobe.d, the laptop goes to sleep and wakes up fine. This laptop failed to get out of sleep with ATI proprietary driver as well

---

### Post by lelamal on 2010-06-07
> **vldmrrr said:**
> I had freeze on resume on dell inspiron 600m. The problem appears to be caused by radeon kernel module - once I switched Xorg to "vesa" driver, and blacklisted radeon module in /etc/modprobe.d, the laptop goes to sleep and wakes up fine. This laptop failed to get out of sleep with ATI proprietary driver as well

In my case (Thinkpad R50e) the issue was solved, when I tried Lucid, right after its release. I didn't change anything from the default install.

---

### Post by vldmrrr on 2010-06-08
> **lelamal said:**
> In my case (Thinkpad R50e) the issue was solved, when I tried Lucid, right after its release. I didn't change anything from the default install.

Hm, I actually was talking about lucid as well. This was the first ubuntu release i installed on this laptop

---

### Post by vldmrrr on 2010-06-13
Well, here is even better way to resolve the sleep problem on inspiron m600. It turns out that it is KMS (kernel mode settings) which is enabled by default in radeon module, that caused all weird problems, including failure to wake from sleep, and xorg segfaulting (that could be induced by entering long enaough text into firefox search field [IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]).

Anyway, all is fixed and good after adding the following text:
radeon.modeset=0
to entries GRUB_CMDLINE_LINUX_DEFAULT= and GRUB_CMDLINE_LINUX= in /etc/default/grub and running `sudo update-grub` after that. So now I have accelearted graphic, sleep works, no more xorg crashes (thus far).

And once again, all this is happening on lucid, despite this thread subject referring to karmic, its just so happen that the problem first happened for people with karmic, so probably the solution should be applicable to that as well

---

### Post by a_hippie on 2010-06-13
> **vldmrrr said:**
> Well, here is even better way to resolve the sleep problem on inspiron m600. It turns out that it is KMS (kernel mode settings) which is enabled by default in radeon module, that caused all weird problems, including failure to wake from sleep, and xorg segfaulting (that could be induced by entering long enaough text into firefox search field [IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]).

Anyway, all is fixed and good after adding the following text:
radeon.modeset=0
to entries GRUB_CMDLINE_LINUX_DEFAULT= and GRUB_CMDLINE_LINUX= in /etc/default/grub and running `sudo update-grub` after that. So now I have accelearted graphic, sleep works, no more xorg crashes (thus far).

And once again, all this is happening on lucid, despite this thread subject referring to karmic, its just so happen that the problem first happened for people with karmic, so probably the solution should be applicable to that as well



Thank you for posting this advice.  On my IBM Thinkpad X31, this release brorked my system for suspend/wake-up but fixed my stupid lib failure on several applications I use:
[http://ubuntuforums.org/showthread.php?t=1447155](http://ubuntuforums.org/showthread.php?t=1447155)

So now the beginning of grub looks like this:
cat jaye@IBM-laptop:~$ cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
GRUB_CMDLINE_LINUX="radeon.modeset=0"


Thanks again!  Much better being able to suspend/resume.

Regards,

---

### Post by cespinal on 2010-07-19
> **Jugney said:**
> The Launchpad bug report listed above had the fix for me - an SD card in my computer slot was preventing standy or hibernation. Go figure.

+1 here...

Spent the whole day yesterday attepting to suspend to ram without sucess. I just pulled out the SD card on the slot and everything went ok..... WHAT THE....

---

### Post by kellymartinv on 2010-07-21
+1 for the SD card.  Pulled out the SD card, no more problems.  This should probably be filed as a bug.

---

### Post by Boomerkuwanga on 2010-07-28
Indeed. I was having this exact issue with Lucid. Removing the sd card has stopped the issue completely. It's a little annoying though, since I use a 16g card as a hard drive expansion. After leaving an sd in my last 3 laptops pretty much full time, it's a pain in the *** to remember to remove it before I close the lid. Could any one point me to a fix for the card issue, if there is one.

---

