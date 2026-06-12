---
title: "Having trouble installing"
date: 2011-09-22
forum: General Help
---

### Post by Efoui on 2011-09-22
Hi, I'm fairly new to Linux  but I'll explain a little bit of what I  know before I get started. I've installed Ubuntu on my laptop (version  10.04 I believe) and loved it,  installed perfect and it's been great to  use something other than windows for a change. After my battery crapped  out on my laptop I decided to put Ubuntu on my desktop computer, which I haven't used in a few weeks due to a virus not letting me boot windows. 

My  desktop was running windows 7 64 bit, 8gb ddr3 ram, 3 hard drives ( 1  tb, 2 tb angle a 500 gb) I've tried a CD install of versions 10.04 and  11.04 and both freeze up shortly after clicking install (stays on the  purplish colored screen with nothing on it) But when I try to install  11.04 from a USB key it just goes the same screen then eventually goes  to a black screen with code scrolling through it then stops, sits there  for a few minutes then does the same thing over again. 



The 1 tb drive in the computer had windows on it (has a virus on it that won't let windows boot)
2 tb drives has all my family pics, movies, games, songs etc...
Third  500 gb drive is blank, never hot around to using it, I put it in to  install Ubuntu at a later date a few months ago but never got around to  it. 


I know it's a long shot and I'm probably doing a horrible  job of explaining this but can anyone point me in the right direction  please? I can give any information needed, thanks!

Uploaded are 2 of the screens I'm getting when trying to install from a usb key

---

### Post by Efoui on 2011-09-23
Anyone know if theres another way to try and install Ubuntu besdies the live CD and usb key?

---

### Post by garvinrick4 on 2011-09-23
Yes there is an alternate .iso download that does not use graphic's that I like because it works
everytime for me if the desktop version fails me while doing dailys. Have to focus and no a little
bit more about installing. Unplug the drive with all your personals if possible would be my suggestion
if using alternate for first time and rather new at installing Linux.

---

### Post by Efoui on 2011-09-23
Is there a tutorial on how to do this or anything? Like I said, I'm fairly new to this stuff but I learn quick so if theres a guide of some sort I could get it going. And yeah, I've removed the 2 tb drive completely so I don't risk losing everything on it.

---

### Post by garvinrick4 on 2011-09-23
> **Efoui said:**
> Is there a tutorial on how to do this or anything? Like I said, I'm fairly new to this stuff but I learn quick so if theres a guide of some sort I could get it going. And yeah, I've removed the 2 tb drive completely so I don't risk losing everything on it.
All I had handy, looks Ok.
[http://wheatlandlinux.wordpress.com/linux-instructions/ubuntu-alternate-install-instructions/](http://wheatlandlinux.wordpress.com/linux-instructions/ubuntu-alternate-install-instructions/)

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by Efoui on 2011-09-24
Alrighty, I burnt the iso image for the PC (Intel x86) and booted it up, I get through the setup up untill I'm installing the base system where I get the following error:

---

### Post by varunendra on 2011-09-24
Can you post a complete hardware description of your hardware please? That would be:

[LIST]
[*]Desktop model if it is a branded one.
[*]CPU model
[*]RAM (already mentioned, just repeat here as part of a consolidated detail)
[*]Motherboard/chipset - name and model
[*]Graphics card(s) / adapter(s)
[*]Whether you have ever tried any kind of RAID array on any of the current drives?
[*]Have you tried making any changes to your BIOS?
[/LIST]
You said it freezes when you click "Install". Does the LiveCD work fine when you work in Live session? (That is, when you click "Try Ubuntu..." instead of "Install...)

Your description about the 500GB drive is a bit unclear to me. Do you mean it is problematic, or just that you have not yet tried to install on it. If you have doubts on any of your drives, I would suggest to retry without plugging it in.

Lastly, if the live session also freezes at some point, please describe where.

---

### Post by Efoui on 2011-09-24
It is a Gateway DX 4840-01c desktop from Best Buy that I got a little less than a year ago.

Came with 4gb of ram and just a 1 tb hard drive originally, I've added 4 more gigs of ram that I had kicking around and the other 2 hard drives.


As far as I know there's nothing wrong with the 500gb hard drive. I bought it and put it in with the intent of installing Ubuntu as a 2nd operating system but never got around to it before windows went down on the pc.


Here's the spec sticker that's on the side of the computer:

---

### Post by varunendra on 2011-09-25
You didn't say anything about how it behaves in a live session. If it hangs in that mode too, then at which point. And whether you made some changes in BIOS.

If we can pin-point the reason, a solution may be very simple then.

---

### Post by Efoui on 2011-09-25
Sorry about that, yeah when I try the live session it looks like its about to freeze after I select it (hangs there for about a minute) then goes to the loading screen with Ubuntu and 5 dots that alternate colors from white to red. Then after that it goes to a black screen with an underscore flashing in the top left corner and stays at that. I've left it sit there like that for 2 hours+ and nothing happens at all, still sits there with the underscore blinking on and off on the black screen. Nothing happens when I press anything on the keyboard.

Exact same thing happens when I try to install from the CD or try a live session from the install CD on both 10.04 and 11.04 (both 64-bit). 

Also I haven't touched the BIOS on this computer at all yet.

---

### Post by varunendra on 2011-09-25
As a test, please disconnect all of the hard drives. Then follow this:

[LIST]
[*]boot from the cd, and just as it starts booting, press any key to bring up advance menu.
[*]Select language, then press F6 to pop up "Other Options'" menu.
[*]In that menu, highlight (using arrow keys) and select (pressing spacebar) these options: acpi=off, noapic, nolapic, nodmraid and nomodeset.
[*]Then press Esc key to close the menu and press 'Enter' selecting "Try Ubuntu...." option
[/LIST]
See if this helps you boot normally.

One more thing - you said the desktop "**was**" running Windows 7, is it still working? If it also crashed or is/was causing troubles, then the next step would be to test the RAM from the same above menu (using "Test memory" option).

---

### Post by Efoui on 2011-09-25
All hard drives disconnected, put an X beside acpi=off, noapic, nolapic, nodmraid and nomodeset. 

Went to try the Ubuntu live and it just seems to freeze up on the blank screen after the loading screen with the word Ubuntu and the 5 dots that alternated between white and red.


After no luck with that I did a memory test from the disc and it passed with no errors at all.





And the part about when I said the PC "was" running windows 7 is that I had company over during the summer and after they left my computer would try to do a system restore every time it booted, couldn't get to the login screen or anything, it just keeps trying to do a system restore ont he initial startup. I went along with the system restore and it stops halfway through saying there is an error and needs to restart then when it restarts it goes back and does the exact same thing, its just an endless loop. So I gave up on windows and just decided to go with Ubuntu as the only OS on the computer.

---

### Post by varunendra on 2011-09-29
Hi,

Sorry for such a late response, didn't get time to. Given the way that not only an alternate cd installation, but even restore-to-factory-settings efforts were failing in a similar way, and now the same is happening with even all drives disconnected, it now definitely seems to me a hardware defect issue. Yes it may be your RAM. But may be something else as well. Since you have two RAM modules installed, I would suggest to retry with only one of them installed.

If it fails even with both modules tried separately, you may then try to boot via CD or a live USB with minimum components attached to the motherboard. That is- remove every card & connector from the motherboard without which the PC can just boot, then try a live USB (to avoid even the cd drive) to see if it can boot normally. In this approach, the connected components would include only the power connectors (to the mother board), VGA cable (to the on-board VGA port), keyboard, single RAM module, CPU (obviously), and the Live USB flash drive (to the onboard USB port).

But before going into any kind of "hardware-approach" you should try 'resetting BIOS' to its 'Optimal Defaults'. If that doesn't help, you may proceed with the 'minimal-hardware' thing.

Oh, one more thing.. with this kind of minimum setup approach, I would not rely on just one version of an OS. Firstly, make sure the CD/USB you have works (on other computers). Then, try some other versions as well (like 10.04 and/or variations like xubuntu or lubuntu, even different OS like DSL (it's Linux, but minimal- only 50MB), etc.)

If all these approaches fail in a row in the same way, then perhaps your motherboard has retired immaturely. Although it is a very remote possibility, while the probability of a faulty device/card/connection/RAM is maximum.

---

### Post by volaer on 2011-09-29
I think you can install it in your windows without uninstalling the windows itself. But it will be a dual boot. Nonetheless, you can uninstall it anytime without any effect from Windows.

---

### Post by westie457 on 2011-09-29
Originally by varunendra > But before going into any kind of "hardware-approach" you should try 'resetting BIOS' to its 'Optimal Defaults'. If that doesn't help, you may proceed with the 'minimal-hardware' thing. Just to add that you might have to completely reset the bios using the jumper. Some advice for that is in this link (scroll about half-way down the page) [http://motherboards.mbarron.net/bios.html](http://motherboards.mbarron.net/bios.html) just in case the virus on the Windows drive has somehow infected the bios.

On a side note it sounds like the Windows virus has infected the MBR of the hard drive. That can be removed with a Windows Install or Recovery (NOT a Restore) disc.

---

### Post by varunendra on 2011-09-29
> **volaer said:**
> I think you can install it in your windows without uninstalling the windows itself. But it will be a dual boot. Nonetheless, you can uninstall it anytime without any effect from Windows. Please see OP's post just above my previous one. He says his PC 'was' running windows. Currently, he can't even get to the login screen.

> **westie457 said:**
> 
On a side note it sounds like the Windows virus has infected the MBR of the hard drive. That can be removed with a Windows Install or Recovery (NOT a Restore) disc.
It might be, but he has the same results even with all the hard drives disconnected. That's why I doubt it to be something else.

By the way, the BIOS 'hard-reset' thing seems a good suggestion to me.

---

### Post by westie457 on 2011-09-29
@ varunendra Just thinking along the lines of memory incompatibility. Even though the sticks are passing memtest I presume when installed together and separately that they are conflicting with each other causing the failures.
In an earlier picture where the base system failed to install there was advice to check virtual terminal 4 for the error report, would that have been accessible using Ctrl+Alt+F4 at the time? I wonder if the OP can reproduce that error and take down details of what is in the report. It may provide the correct information to find a solution.

@ Efoui The issue with the Windows drive will be dealt with after we have got Ubuntu installed and running on a hard drive. I am not going to dilute the efforts of those helping by the distraction of detailing a procedure that is not so important.

So try varunendra's suggestion of resetting the Bios to either 'Failsafe' or 'Factory' defaults, either will do. If one does not work then try the other. If neither work then try the 'hard reset' I suggested earlier. Only connect a hard drive once the LiveCD has been booted to a Desktop. Obviously power down before connecting the drive. I do know of someone who tried while everything was powered up - the result was a fried hard drive.

Hope this is helpful to all concerned.

---

### Post by Efoui on 2011-10-03
Alright, sorry I took so long to get back, I was gone to see family for the weekend. I just finished doing a hard BIOS reset and a soft BIOS reset. Took the small battery out, unplugged all cords then held the power button for a few minutes to get rid of any power, left it sit for a while afterwards then rebooted and went into BIOS and restore it back to default. Tried both live CD's that I have (10.04 and 11.04)and they both freeze up in the exact same spot as before. This was all done with no hard drives disconnected and only running with the original 4gb of ram (2 2gb sticks) that the pc came with.

Going to disconnect everything I can right away like you indicated and try to boot witht he USB stick.

Also it doesn't really matter if I get windows back on it, I'm mainly worried about getting Ubuntu to boot. And the extra 2 sticks of ram where added, where installed a few days after getting the pc, it ran for months with them in it

---

### Post by Efoui on 2011-10-04
Alright, I just disconnected everything I could. Hard drives, took out 3/4 ram cards, the CD drive and wireless card. The only thing left connected was the graphics card, 1 ram card and the monitor, keyboard, mouse and usb drive.

When I boot up onto the USB drive and try to run the live version it goes to the screen enclosed in the picture. I've done it twice with 2 different ram cards installed (1 of the original ones and 1 of the older ones both in the first slot). If theres anything I can possibly disconnect or I'm forgettting just let me know, thanks

In your opinion is this just a hopeless case where I should just salvage anything I can out of the machine and save up for a new one?

---

### Post by varunendra on 2011-10-05
> **Efoui said:**
> The only thing left connected was the graphics card, 1 ram card and the monitor, keyboard, mouse and usb drive.

Don't you have an on-board graphics port? Because i3-540 processor does have embedded graphics (Intel HD). If there is, use it disconnecting the ATI card. Or see if there is an option in BIOS to change the graphics in use.

If there is no option for alternate graphics, I guess there is not much left to try except alternate OSes.

Also, as *westie457* pointed out in post #17:
> **westie457 said:**
> In an earlier picture where the base system  failed to install there was advice to check virtual terminal 4 for the  error report, would that have been accessible using Ctrl+Alt+F4 at the  time? I wonder if the OP can reproduce that error and take down details  of what is in the report. It may provide the correct information to find  a solution. can you do the same to see and note down the error report to post here?

For alternative operating systems to try, I would suggest [DSL]("http://www.damnsmalllinux.org/") and [SLAX]("http://www.slax.org/"). Both are linux based, but are minimal, and may circumvent certain odds if possible. Additionally, I would recommend to download Hiren's Boot CD (HBCD- [see contents]("http://www.hiren.info/pages/bootcd")) ([official download link]("http://www.hirensbootcd.org/download/")). Apart from almost every kind of software tools available, it also can boot both into linux and windows (PE) environments. So try it to see if your PC can boot into XP (PE) from the CD. You can also install it onto a USB flash drive if you wish ([see how]("http://www.hiren.info/pages/bootcd-on-usb-disk")).

Unless you try all these things, I won't say it's hopeless. Even if all this fails, maybe a professional motherboard expert (who knows his stuff) can figure out something we are constantly missing, and may find out a solution. I am still hopeful because it is working normally till the boot menu. Although it is not a guarantee of its functionality since most of the hardware probing starts afterwards.

---

