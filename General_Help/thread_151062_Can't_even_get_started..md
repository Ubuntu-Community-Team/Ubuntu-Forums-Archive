---
title: "Can't even get started."
date: 2006-03-27
forum: General Help
---

### Post by Keptin on 2006-03-27
Just received my Ubuntu disks and have spent the last 2 hours trying to get started. I have 27 years experience programming but have never used Unix/Linux. I feel really stupid.
I can read the CDs in XP but when I boot from  the Live CD 32 bit or 64 bit I get a series of installs ending with line-
[4294677.430000] ohci_hcd ... using the wrong IRQ
I am still black screen and can type anything with no effect. Function keys do not work.
Please help.
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)

---

### Post by gnu2tux on 2006-03-27
Very odd indeed.

ohci is the usb system, so it sounds like a fairly low-level failure.

Try unplugging any usb devices and/or disabling usb on the system via bios just to see if you get past this issue.

What specifications does your system have? Especially pertaining to usb/motherboard.

---

### Post by jerrykenny on 2006-03-27
Try going into your BIOS, turn the Legacy usb support OFF,

and change your plug-n-play OS to YES, . . . 

Failing that, try loading failsafe defaults into your BIOS.

---

### Post by Keptin on 2006-03-28
Thanks for the help guys.

I removed all USB devices (interesting situation as my mouse is the only device) and deleted them from the device manager. I also turned USB legacy support off in the BIOS.
One of them worked! I suspect it was the legacy support.
Now...
The install now continued until it reported "Failed to start X server"
Waited a few minutes and then C+A+D
It said X server was bypassed (or something like that) and continued until
* Checking battery state
Then it hung.

---

### Post by Keptin on 2006-03-28
Oops. Forgot to post my hardware.
AMD 3400+ 2.2 gHz
1600 mHz FSB
ATI Radeon Xpress 200

Keptin

---

### Post by gnu2tux on 2006-03-28
Hi,

 You certainly seem to have had your fair share of problems!

Sounds like you may have a flaky version of BIOS on your machine. If there is a firmware update from your motherboard manufacturer's website, I'd reccomend upgrading it to the latest version.

The problem is probably related to one of two things:

1) The X server isn't starting because somethings wonky with the graphics card driver.
2) The ACPI/Power controls arent working right (as per my statement about getting latest firmware). 

You may be able to check for (2) by setting the noacpi option at boot time. To do this, when you see the grub menu info at boot time press ESC to get into the grub bootloader menu. You will see listed Linux and any other os you have. Select the most recent linux kernel (you probably only have one), and press the E key. You will be able to edit the kernel options for this entry (line starting linux). Add the word noacpi to the end of the line, press return and press b to boot the system. If it is acpi thats causing the problem, try firmware upgrade or messing around in your bios with regards power management (pnp os etc).

If you suspect ATI graphics driver problems, try pressing Ctrl+alt+f2 at this point, can you get a login prompt (text mode)? what happens if this is not the case? Anything?
If you can't get a login prompt then try a single user login, go back to the grub menu like in the last paragraph and add the word 'single' instead of noacpi. Can you boot to the text mode prompt? If yes, then the problem is quite far down the list of things that the machine does on startup, still likely the X server/graphics driver. Search this forum for ATI graphics driver issues and /  or hanging on checking battery state and see what other ATI users are having problems with.

Lastly, can you just confirm you are using Ubuntu 5.10 - not dapper (6.04) or anything else like that?

Hope this gets you started. Sorry to hear you are having such problems. Believe me, it's not usually like this. Keep trying and it'll all spring into life when you least expect it!

Regards,

Ali

---

### Post by Keptin on 2006-03-30
Ya, I do seem to have my "fair share of problems" but I am used to it. 27 years of building computers, installing networks writing a few thousand lines of code and they still happen.
As far as Linux goes, I am green as grass. It took me a couple of hours to find out what a grub screen was! Now that I know (I think), I don't got one.
I have tried Boot: live acpi=off, I have changed to BIOS ACPI suspend from S3(STR) to S1(STR) which are the only options.
I complete the GUI installation and get the colour screen showing many OK's. I then go back to a black screen with several screen refreshes and then a bunch of successes. I then get a colour screen saying X could not be installed and do I want to view results. At this point the 32 bit locks with garbage on the screen and the 64 bit closes everything and exits.
I am using straight 5.10 off disks that were sent last week.
My computer (specs above) is only a couple of months old and I have seen _no_ video problems.
Any other ideas?

Kirk Out! Keptin Kirk that is.

---

### Post by gnu2tux on 2006-03-30
Ahh! No wonder you don't have a grub screen! You're using the live CD, as opposed to the install cd.

I've never used the Ubuntu Live CD (only Knoppix), but I believe there is a similar menu with which you can provide these parameters.

I have had less success with Live CDs than their installer counterparts, simply because the installer usually does a better job of probing your hardware.

It's sounding very like graphics at the moment. Have you tried downloading a live CD snapshot of 6.04 beta/flight? It'll have the latest drivers and might just solve your problem in one!

Regards,

Ali

---

### Post by Keptin on 2006-03-31
Hi Ali,
Ya, I thought of it being the Live CD when I was supposed to be sleeping.
I did boot the disk on another computer and it worked fine. It is only a 32-bit machine so I didn't try the 64 bit one. It also has an ATI card (slightly different model) and both are eMachines.
I will try the download you suggested. I went to ATI and found the driver which is 25 MB! I live in a benighted area which only has 28.8 kps access. That's a 3 hr download.
BTW, I see you are in Paisley. My grandmother comes from there. She is a Royal Stewart.
Kirk Out!

---

### Post by Keptin on 2006-03-31
Oops again. She is from Paisley. Her husband is from Gasgow.
Kirk Out!

---

### Post by gnu2tux on 2006-03-31
Lol. I live in Glasgow, but I also know paisley and surrounding areas. I'm a Ross (stewarts and ross clan have good history way back!).

Where are you that you only get 28.8kbps you poor soul!

I can burn it to a CD and post it to you if you are in the UK, just give me the URL of the driver and any other bits and bobs you want (I will download latest Dapper Drake CD for you too just in case that fixes the problem).

Cheers,

Al.

---

