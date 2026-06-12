---
title: "HDMI to DVI cable for monitor"
date: 2012-02-28
forum: General Help
---

### Post by JoshH54 on 2012-02-28
Need help guys.
Have a HDMI to DVI cable so i can play PS3 on monitor.
My computer supports HDMI so i plug the HDMI to computer and DVI to monitor and the screen does not show. why?
The boot loader (grub) will show but the actuall OS will not display on the monitor. Do i need any drivers? or do i need to select use HDMI for display somewhere?
Thanks

---

### Post by papibe on 2012-02-28
Could you post your /var/log/Xorg.0.log ?

Paste it here [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post the link.

It may be give us some clues about what's going on.

Regards.

---

### Post by JoshH54 on 2012-02-28
Dont understand
1920x1080 monitor.
Hdmi-DVI works with ps3 but not computer

---

### Post by JoshH54 on 2012-02-28
I have a Syncmaster BX2335 LED. [http://www.dooyoo.co.uk/tft-monitor/samsung-syncmaster-bx2335-led/details/](http://www.dooyoo.co.uk/tft-monitor/samsung-syncmaster-bx2335-led/details/)
Why does the hdmi to dvi cause the monitor to go black

---

### Post by dcstar on 2012-03-01
> **JoshH54 said:**
> Need help guys.
Have a HDMI to DVI cable so i can play PS3 on monitor.
My computer supports HDMI so i plug the HDMI to computer and DVI to monitor and the screen does not show. why?
The boot loader (grub) will show but the actuall OS will not display on the monitor. **Do i need any drivers? or do i need to select use HDMI for display somewhere?**
Thanks

[LIST=1]
[*]Possibly.
[*]Probably.
[/LIST]

System-Preferences-Monitors.

---

### Post by JoshH54 on 2012-03-01
ok so i've installed new drivers and. Nothing.
I have searched for switch to HDMI and. Nothing
I have a DL-DVI-D HDMI cable. Does this hold any significance?

---

### Post by JoshH54 on 2012-03-06
Still need help guys I've had no success

---

### Post by Mark Phelps on 2012-03-07
If I understand your problem, when you plug the DVI-HDMI adapter into your PC, you get no video, right? That's most likely because the video drivers you're using are not sending output to the hdmi port.

Since you've not told us your make and model video chipset, this is just a guess.

To find out what it is, open a terminal, enter "lspci", look for the line containing "VGA" and post that back here.

If you're running an Intel video chipset, then you're likely stuck.

---

### Post by zero2xiii on 2012-03-07
Hay,

Also you are not saying if this is a dual screen setup? HDMI is **NOT** a primary display port, you need to set it up as one, thus you might need another monitor connected to a standard VGA or DVI port to configure the second monitor connected to the HDMI port.

This can all be done under your screen setup aplication, or the nvidia control panel (I use a similar configuration with 3 screens on my laptop running a nvidia chipset. Having dual monitors, and then one that clones both on one monitor through HDMI)

Cherz

---

### Post by Mark Phelps on 2012-03-07
Another suggestion ... on my desktop, there are three video output jacks: HDMI, DVI, VGA.  The BIOS limits the use of any two jacks such that HDMI can be used with VGA, and DVI can be used with VGA, but HDMI can not be used with DVI.

If you have a similar setup, check your BIOS to confirm that the HDMI port is enabled for the video.  My guess is it will enable the VGA port by default, and maybe the DVI as well.

---

### Post by grahammechanical on 2012-03-07
Here is a clue

> The boot loader (grub) will show but the actuall OS will not display on the monitor.

If you are seeing the Grub menu then the connection from the computer to the monitor must be working. Right? I think so.

Is this the usual monitor that you have been using but with VGA and not DVI or HDMI?

If it is another monitor and you have a proprietary video driver you could open the video setting utility and click Detect Displays. For the open source video driver you can find a Displays utility in System Settings that will let you do the same thing.

Regards.

---

### Post by JoshH54 on 2012-03-07
Video is being sent throughout the bootloader but stops when i enter the os (windows 7/ubuntu)
I have built in intel chipset.
My computer is acer aspire m3970
It is not a dual monitor setup but i can get another monitor if i need to use that to setup hdmi on the other monitor.
Yes that is right grahammechanical, i am seeing grub but no further.
Yes this is my usual monitor and i have been using vga.
I think i have tried this. Is this the equivalent of using display in windows 7, if so it has not worked.

Thanks guys, getting closer

---

### Post by poikiloid on 2012-06-02
Ever get your HDMI out to DVI in working?

I am having the same issue.

---

### Post by crazyJay648 on 2012-06-03
I'm having nearly the exact problem. I started a thread on it ([http://ubuntuforums.org/showthread.php?t=1991754](http://ubuntuforums.org/showthread.php?t=1991754)), and someone in it tipped me off to this thread.

I know it's not the PC, this is an issue with ubuntu/lubuntu. I've confirmed I can output to other device, just not my viewsonic monitor even though it is detected for some reason. I have full description of my setup in that thread, so maybe some of you might be willing to take more guesses at it? 

I don't see any drivers for the viewsonic I can try though.

---

### Post by TVTrukChik on 2012-06-03
Just a guess, but do the video cards you guys are having trouble with have HDCP?  Depending on the age of the monitor, the HDMI to DVI adapter might not work if that is the case.  With HDCP, the video card needs to check with the device on the other end and verify that it's OK to output the video.  If it doesn't get the proper response, no video.  It's all about licensing and protection of content.   

Wikipedia article: [http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection]("http://en.wikipedia.org/wiki/High-bandwidth_Digital_Content_Protection")

---

### Post by crazyJay648 on 2012-06-03
Thanks for the input. According to my monitors spec sheet, it does support hdcp.

EDIT: I'll have to check the pc.

I have the intel GMA3150 video card. How can I tell if ubuntu supports it?

---

### Post by TVTrukChik on 2012-06-05
If the monitor supports HDCP, it should work whether the video card supports it or  not.  This just sounds very similar to stuff I run across at work, and HDCP is almost always to blame.  Sorry, that was my best guess.  :-(

---

### Post by crazyJay648 on 2012-06-05
I understand, thanks for the help.

---

