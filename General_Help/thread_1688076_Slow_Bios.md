---
title: "Slow Bios"
date: 2011-02-14
forum: General Help
---

### Post by Fire_Fist on 2011-02-14
ALRIGHT

Here's my problem.

I'm not sure if this is the right place to post for this sort of problem, but this place seems to be the best place for answers

MY SET UP

an HP Slimline, Don't know the model at the moment but if it's needed I'll look it up.
I know it has a DVD Drive and 2GBS of DDR2 Ram along with a 500GB Hard drive
And is duel booting Ubuntu (10.10 Maverick Meerkat) And Windows 7

MY PROBLEM

Firstly, when I try to boot
it stays t bios for seemingly 5 minutes
After the Five minutes has passed it will try to boot into whatever is set
as the First boot device set. and it won't switch to the second boot device if 
the first one isn't present

IE If I set the DVD drive to boot first, it will give me a Blank screen with a single blinking line

And whatever it tries to boot into, it takes about 4 minutes to boot into it
IE if I set it to boot into the HDD it gives me the same blank screen
only difference being that it will enter the grub after 4 minutes

And once I get into the Grub (Grub2) It lets me boot into ubuntu just fine
And if I try to boot into Windows 7 it Starts to boot then in the middle it freezes
(While the light's are still moving in the windows logo)

Now I've tried booting into the Windows 7 Install disk
but it won't boot into the disk, it just shows the same blank screen forever.

Hope you guys can help with my problem.

( I Need Windows 7 For Various things that ubuntu doesn't support, Netflix, Multi Touch Touchpad, xPadder, ect. )

---

### Post by ahsan101 on 2011-02-15
Go to your BIOS and set the Optimal Defaults from Exit menu, or Load Setup Defaults, try to check the cables of your HDD or CD-ROM. Boot again.

---

### Post by Fire_Fist on 2011-02-15
No dice, but I Did notice going into settings was normal speed, as apposed to trying to enter the boot menu.

---

### Post by matt_symes on 2011-02-15
Hi

Take the side panel off and make sure there are no loose connectors. Make sure all the boards are seated correctly. Have a general look over all the components in the PC.

What version of the BIOS are you using ?

Is this a recent problem ? When did it start happening ? Did you change something and then it started happening ? I take it you did not buy the PC that way ? Can you remove cards, peripherals one at a time until it boots correctly ? Just trying to eliminate a hardware issue.

More background might be useful.

Kind regards

---

### Post by Mark Phelps on 2011-02-15
Several minutes is insane!!  But ... it might not actually be that long, it may just appear to be that long.

You should have your BIOS set to display progress messages, not some slick advert screen.  That way, you can watch as it steps through various actions.

If you have it set to a fancy splash screen, then the actual delay is most probably NOT in the BIOS or POST, but in launching the OS and getting to a login screen.  And, a delay that long implies serious hard drive problems.

This is further supported by your claim that you can go into the BIOS setup screens very quickly.  So, it's not taking a long time to execute the BIOS stuff -- that is contained in a chip.  Instead, it's taking a long time to run stuff off the hard drive.

You might also check with HP and see what they have in terms of BIOS updates.  Not booting into the CD/DVD, even when you have it set to do so, is a serious BIOS problem.

---

