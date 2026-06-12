---
title: "having trouble formatting hard drive"
date: 2012-05-26
forum: General Help
---

### Post by Gatorade on 2012-05-26
hi guys,

I'm having problems formatting a hard drive that came out of a HP 6640c desktop pc. 

The guy I got it from said it was giving him problems, and asked if I could reformat/re-install windows for him. I tried using the recovery discs which came with the pc and it looked like everything was going good. Then it stopped loading and the cursor just sat there. 

I tried it again several times but wasn't successful in re-installing windows for him. I also tried Ubuntu , Mint, Puppy but I couldn't get any of them to install. It would start up and look like its going to install , but then it crashes every time.

I also tried removing the drive and connecting it to an external usb enclosure, which I then tried to format using linux but got errors stating that the drive has operations pending. 

I guess its from the times when I was trying to format and it failed.

Can anyone suggest a course of action that will solve my problem?

I can post some screenshots or some video if it helps.

---

### Post by irv on 2012-05-26
Boot up Ubuntu from live CD and try running gparted and do a check on the drive and see if you can delete all partitions if there are any. Then setup everything new on the drive. Hopefully you will be able to do a clean format on the drive.

---

### Post by Jimmyfj on 2012-05-26
I would suggest that you download Gparted (you can find it at distrowatch.com) Boot it up and see if that does the trick.

---

### Post by Gatorade on 2012-05-26
I've tried booting from the cd but it doesn't work. I get to the screen where it asks which language I want, I choose english, then I try install , or run without making changes. it takes forever, the cursor just sits there flashing in the top left corner. I then have to shut it off by holding the power button.

---

### Post by Mark Phelps on 2012-05-26
You should download and burn the GParted LiveCD -- which you can get from distrowatch.com. That doesn't come with the graphics overhead of Ubuntu.  It will load much faster -- and then, you can see what's on the drive.

---

### Post by Gatorade on 2012-05-26
thanks for the suggestions everyone. I stuck the hard drive in  different pc and it loaded everything without a hitch.

I don't know why it wasn't working in the other one. I'm going to try it again in the computer I was originally trying to get it to work with and see if I can now get it working.

I'll post my results when done.

---

### Post by irv on 2012-05-27
If it is just this one PC you are having problem with make sure you can see it in the BIOS first. Most desktop computer come with two plugins for HD/CDs so try them both. If you have a problem seeing it in the BIOS, it could be a problem with the HD controler on the motherboard. Make sure you don't have any bent pins on the drive also. That's if it is IDE drive.

---

### Post by jmore9 on 2012-05-27
For the partitioning part i use a program called gparted live.  It is a cd system which you boot into run like any other os.  Here is the link to the download and some docs for it.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

