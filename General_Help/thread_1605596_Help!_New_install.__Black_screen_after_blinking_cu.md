---
title: "Help! New install.  Black screen after blinking cursor"
date: 2010-10-25
forum: General Help
---

### Post by gatorbrit on 2010-10-25
Hi, just did a dual boot install on a brand new DEll T1500.   The machine has win7 on it.  I booted off the live CD and all looked well.  Installation went well.  

When I reboot, I get grub, select the top linux option and then see a small black blinking cursor for a few seconds, then nothing.  The screen reports no signal.   

Ubuntu is installed in the sda4 partition.

Thanks

Rich:(

---

### Post by rajeevisonline on 2010-10-25
clearly grub is having difficulty locating your installation.but it could also be a graphical problem.probably try a different bootloader..repartition and try to follow the guide on

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

also dell t1500 is ubuntu 64 certified.. so its gotta be a problem with your installation methodology.

I suggest doing things the other way around.. a little longer but more convenient...linux first and then windows...linux is a better OS anyway:)

i am sorry i am only a noob..only can help u so much..also check ure disk for error or other memory problems

and last but not the least your bios and try ure best to leave it in its original condition[COLOR=#000000][FONT=Times New Roman][COLOR=#465584][FONT=Courier][/FONT][/COLOR][/FONT][/COLOR]

---

### Post by gatorbrit on 2010-10-25
> **rajeevisonline said:**
> clearly grub is having difficulty locating your installation.but it could also be a graphical problem.probably try a different bootloader..repartition and try to follow the guide on

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

also dell t1500 is ubuntu 64 certified.. so its gotta be a problem with your installation methodology.

I suggest doing things the other way around.. a little longer but more convenient...linux first and then windows...linux is a better OS anyway:)

i am sorry i am only a noob..only can help u so much..also check ure disk for error or other memory problems

and last but not the least your bios and try ure best to leave it in its original condition[COLOR=#000000][FONT=Times New Roman][COLOR=#465584][FONT=Courier][/FONT][/COLOR][/FONT][/COLOR]


I don't really want to install windows after linux as I don't have the install disks - this was a factory install machine.   I think you are right that it is prob a boot loader issue.

---

### Post by cholericfun on 2010-10-25
Well, since grub is loading i doubt that theres a problem with the bootloader, if there was there should be an error message and not a turned of monitor (i think... not an expert either)

id try recovery first (in grub)
then search for various graphics related boot modes and try them out

---

### Post by gatorbrit on 2010-10-25
> **cholericfun said:**
> Well, since grub is loading i doubt that theres a problem with the bootloader, if there was there should be an error message and not a turned of monitor (i think... not an expert either)

id try recovery first (in grub)
then search for various graphics related boot modes and try them out

I actually tried installing 10.04 on it instead to see if it was a maverick issue, but no, same problem.   


I booted in recovery mode and I could see the commands going by.  It all seemed to work well, until, the last thing that is says is 
```
running scripts 
init boot bottom
done
```  or something like that.

I wonder what it is getting hung on.  As immediately after this the screen reports no signal.

---

### Post by cholericfun on 2010-10-25
well then that sounds like a graphic issue, put headphones on and boot up and see if you get the login sound.
theres other ways to check whether your computer is otherwise responding normally
try this to (normally) reboot the computer:
CTRL+ALT+PRINT
having those three pressed, slowly consecutively press 
R
E
I
S
U
B

if your computer is shut down and reboots now i'd be rather confident that its really only the video.

i saw that once, very annoying issue as one cannot really do anything while your computer is running

unfortunately theres not really an out of the box solution, i searched long threads with titles like "black screen of death" for a long time to try and solve this at a friend who i was semi-interested in linux for a while.

once its fixed though it shouldnt come back to bother you again though (although i'd keep some bookmarks to the things that helped you fix it, i didnt)

---

### Post by gatorbrit on 2010-10-25
> **cholericfun said:**
> well then that sounds like a graphic issue, put headphones on and boot up and see if you get the login sound.
theres other ways to check whether your computer is otherwise responding normally
try this to (normally) reboot the computer:
CTRL+ALT+PRINT
having those three pressed, slowly consecutively press 
R
E
I
S
U
B

if your computer is shut down and reboots now i'd be rather confident that its really only the video.

i saw that once, very annoying issue as one cannot really do anything while your computer is running

unfortunately theres not really an out of the box solution, i searched long threads with titles like "black screen of death" for a long time to try and solve this at a friend who i was semi-interested in linux for a while.

once its fixed though it shouldnt come back to bother you again though (although i'd keep some bookmarks to the things that helped you fix it, i didnt)


OK, thanks, I did  the headphone thing and heard the little hand drum sound for when the login menu appears.  Of course the screen is black.  Pretty sure it is a graphics driver issue.   

Is there a way to 
1. login in to just a prompt, 
2. update the graphics drivers from there?


Thanks

---

### Post by gatorbrit on 2010-10-25
OK this helped

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

I edited the boot line to add nomodoset after "splash" and then I booted.  

display is clearly not full resolution, but I am working on that..

---

### Post by gatorbrit on 2010-10-26
OK - SOLVED.  

The problem is that ubuntu isn't loading a graphics driver.

Solution.
Edit boot line command and add the word ```
nomodoset
``` after the word ```
splash
``` in the boot command.  Then boot up into ubuntu.

The graphics will look pretty crappy.

Next, update the graphics driver to the latest nvidia driver as recommended.

Reboot.

---

