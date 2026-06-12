---
title: "Programming Grub to select the right drive"
date: 2012-06-17
forum: General Help
---

### Post by lsemmens on 2012-06-17
Here is the issue: I have  a system that runs Windoze 7 off a SATA drive
I have a drive caddy that is connected to IDE channel 1 with the slave being the optical drive.
I use a bootable USB HDD as a recovery device which uses grub.
So far, so good.

I run into strife when the drive in my caddy is unplugged. I'm certain that the issues are related to drive mapping and I want to make the recovery drive as universal as possible so that when I boot into another computer I can still use a menu entry to boot the native OS.
My menu structure is such that I have several installation options followed by recovery options, followed by a native OS option. What I need to to is to parse the results of the find function to map my drives accordingly, This is where I fall into a heap as I am not familiar enough with grub yet

relevant code here > ...........

title 7 Boot From Hard Drive \nload Windoze 
find --set-root --ignore-floppies --ignore-cd /bootmgr 
# for now I've removed the search for other bootloaders
#|| find --set-root --ignore-floppies --ignore-cd /ntldr || rootnoverify (hd0) && chainloader +1 && boot
# I suspect that the issue is here as (hd0) in some cases should be (hd1), or more
map () (hd0) && map (hd0) () && map --rehook
find --set-root --devices=h /bootmgr 
#|| find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /bootmgr 
#|| chainloader /ntldr

 Am I right in assuming that everything after the || is ignored even when followed by a && or is the && statement universal (i.e. applicable to the whole line)
e.g. a || b && c
if a is true then the rest of the statement does not get parsed
if a is false, c will only occur if b is true?

Have I missed anything relevant?

---

### Post by lsemmens on 2012-06-17
Pseudo code for what I am attempting to achieve

begin:
title 7 Boot From Hard Drive \nload Windoze 
find --set-root --ignore-floppies --ignore-cd /bootmgr 
**IF FOUND THEN STORE  RESULTS OF FIND TO VARIABLE (call it "var")**
map () (hd**var**) && map (hd**var**) () && map --rehook
find --set-root --devices=h /bootmgr 
chainloader /bootmgr 

Is what I propose possible or do I need to run a pile of If Then Else statements to map my boot drive correctly?

BTW: What does "devices=h" mean? 
I stole the code from elsewhere and have modified it so suit my needs, but I can't find reference to this parameter.

Thanks again

---

### Post by lsemmens on 2012-06-17
Just ignore me! Turns out that the drive in the caddy, although not used with an OS for years, still had remnants of Hissta and eXP on it which grub was picking up. Strange that BIOS never picked it up despite having been in the caddy at boot up for years.

The drive mapping thing still intrigues me though, can I a) interrogate the system and store the result to a memvar?
b) can I then map that memvar to a drive?
What does "devices=h" mean?

---

