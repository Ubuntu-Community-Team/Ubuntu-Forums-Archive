---
title: "creative xfi driver"
date: 2009-10-15
forum: General Help
---

### Post by craig88 on 2009-10-15
i just downloaded a driver for the creative xfi sound card and i dont know where to go next i opened the readme file and it said this:
====================================================================


  Sound Blaster X-Fi Linux 32/64-bit Driver Source Release Readme File

  September 2008


====================================================================


The purpose of this document is to describe how to build and install the 
X-Fi Linux device driver.






Quick install


=============

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install



Uninstall

=========

In terminal,

1) Goto source directory

2) Execute make command as root

   make uninstall




to me thats useless what goes with this "make" command to install this driver or is there a simpler way?

---

### Post by craig88 on 2009-10-15
bump guys?

---

### Post by akakingess on 2009-10-15
Check out this link and see if it answers your questions, basically you are just compiling, which means from a terminal you go to that directory and type "sudo make" and then "sudo makeinstall", but sometimes it differs, so here is a more detailed how-to [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by craig88 on 2009-10-15
cheers bud

---

### Post by akakingess on 2009-10-15
I just hope it helps, if you still need some assistance after reading through that, let us know :)

---

### Post by craig88 on 2009-10-15
wow that link is hard to follow ive extracted the file and thats about it! dont know what to do now at the moment its in usr/local/src and i dont know where to go from there

---

### Post by akakingess on 2009-10-15
This may go faster if you do any instant messaging, do you use AOL IM or MSN Messanger?

---

### Post by P4man on 2009-10-15
Are you sure you need to do this? Compiling a driver isn't for the faint hearted (or newbies) and it seems highly unlikely a "September 2008" driver would add anything to a current jaunty install.

Are you having no sound, or no sound card detected? Have you googled around for other possible solutions (though I  know the x-fi is very badly supported by linux at this point)

---

### Post by craig88 on 2009-10-15
ive no idea i have no sound at all and i dont know how to check if it has drivers already or even if its detected im a newbie as you guess so i have no idea

---

### Post by craig88 on 2009-10-15
> **akakingess said:**
> This may go faster if you do any instant messaging, do you use AOL IM or MSN Messanger?

didnt see this post no sorry bud dont bother with it

---

### Post by P4man on 2009-10-15
Well, do you have a volume control in the top right? If you right click it, and select properties, do you get anything that seems to indicate you have a soundcard? (im not on jaunty here and I frankly dont know what happens when no sound card is detected, ive never seen it!).

Alternatively, the "CLI" way would be to open a terminal and type

```
aplay -L
```

copy paste the output here.

---

### Post by akakingess on 2009-10-15
I don't want to leave you hanging, but I understand it seems overwhelming as a newbie, but just take it one step at a time and before long you'll be able to do this stuff blindfolded, take it from a 32 year old that just installed Linux (Ubuntu) in the early part of this year, and I think I have come a long way, so stick with it, it will pay off.

---

### Post by craig88 on 2009-10-15
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
theres the output i think it knows its there but not sure and when i clicked preferences it could only find the inbuilt one plus some others which im not sure what they where.

---

### Post by P4man on 2009-10-15
it seems to detect an onboard sound, but not your x-fi. can i suggest something simple and ugly? use the onboard sound, and forget about the x-fi for now. Unless you hook up your PC to a $2000 amplifier and speaker and you are an audiophile, I bet you wouldnt hear the difference.

---

### Post by craig88 on 2009-10-15
lol nah its only hooked up to like £40 speaker and sub thingy from Logitech yeah ill just use onboard eaier in the long run i guess!

---

### Post by akakingess on 2009-10-15
Then I would stick with onboard audio for now, I agree 100% with P4man :)

---

### Post by P4man on 2009-10-15
> **craig88 said:**
> lol nah its only hooked up to like £40 speaker and sub thingy from Logitech yeah ill just use onboard eaier in the long run i guess!

Once you get more familiar with OS, you can try again.. but by that time, I would hope "out of the box" support for X-fi's has come to the point that you don't need to "try" anything, you can just use it.

Anyway, a quick google on the ALC888 reveals a fair amount of problems as well lol, you're not exactly lucky,  I hope the onboard sound works for you.

---

### Post by craig88 on 2009-10-15
yup thanks for your help guys got there in the end ! :P

---

