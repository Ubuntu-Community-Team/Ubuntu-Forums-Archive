---
title: "Blank screen when Ubuntu starts"
date: 2010-09-30
forum: General Help
---

### Post by Aardappelschijfje on 2010-09-30
Dear users,

This week Windows Vista on my laptop got totally messed up. I couldn't find a way to repair it, so I decided to clean my whole hard disk and to get a new OS. Ubuntu seemed like a nice alternative and I decided to give it a try.

So I downloaded the Live CD v10.4 and tried to install. This didn't work, as my monitor would lose signal when I would press "install Ubuntu". Immediately I consulted Google and I found out about the alternate CD. This helped: I could install Ubuntu without any problems. However, after the installation was done and my laptop rebooted, the screen went blank again. I can't do a thing!

I have searched on this forum and I have looked on Google, but I couldn't find anything which would solve my problem. I have to tell you that I am a complete newbie: I don't know anything about Linux and my knowledge about computers is also minimal. However, it seems like that my** ATI Radeon HD 3470** might be the problem, as Ubuntu doesn't seem to like ATI-cards.

So, the bottom line is:** My monitor gets in standby mode when Ubuntu starts. **

Is there anyone out there who could help me step by step to solve this problem? I would really appreciate any effort. 

Kind regards,
Aardappelschijfje

---

### Post by thesaheb on 2010-09-30
**Register Dumps for -ati (pre-r5xx chips)**

 radeontool in Jaunty* can be used to assist in debugging these kinds of issues on pre-r5xx [ATI GPUs]("http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units") where the screen blanks on start. After installing it, you run it like this: 

    radeontool regmatch '*' > regdump_good.txt

    radeontool regmatch '*' > regdump_broke.txtRun it two times. Once when you have a good, working screen (for any driver including -vesa), and once in the broken case (either from the tty console or logged into the sick box remotely). 
* - Earlier versions of Ubuntu before Jaunty have too old of a version of radeontool.  You can try using the Jaunty version from [http://packages.ubuntu.com/jaunty/radeontool](http://packages.ubuntu.com/jaunty/radeontool), or else you can obtain and build it from the upstream git tree at [http://cgit.freedesktop.org/~airlied/radeontool/]("http://cgit.freedesktop.org/%7Eairlied/radeontool/")]
 Might be this thread can help you out.........

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by alphaamanitin on 2010-09-30
When did your screen go blank?  I have had this happen when the locatoin the boot loader was pointing to was not correct.  I solved this by hitting 'e' in GRUB and editing the /dev/sdXX to what I knew XX should be.  After that it booted fine and I used the sudo grub update command to fix it perm.  

Not sure if that info will help though.

AlphaA

---

