---
title: "Sleep/Hibernate"
date: 2010-12-25
forum: General Help
---

### Post by j1gs4w on 2010-12-25
I have installed Ubuntu on my laptop, and whenever I close the top and it goes to "sleep mode" and later on when I open the top again, the screen is just blank (black). I don't return to login screen or anything like that. Also, if I hibernate (with top open), is the same thing.

Any help would be great,
thanks :)

---

### Post by dcstar on 2010-12-28
> **j1gs4w said:**
> I have installed Ubuntu on my laptop, and whenever I close the top and it goes to "sleep mode" and later on when I open the top again, the screen is just blank (black). I don't return to login screen or anything like that. Also, if I hibernate (with top open), is the same thing.


Press the Power button.

---

### Post by Dex73 on 2010-12-28
Pressing the power button or maybe just using the mouse pad if the screen is on and is just blank.

---

### Post by francf on 2010-12-28
Which version? 10.04 , 10.10?
VideoCard? Nvidia, ATI, Intel?

---

### Post by j1gs4w on 2010-12-29
I am using version 10.10 (up to date), i have ATI video card (1 gig) and intel quad core.

When I close the laptop top and then reopen, it boots up and i can move mouse, but there is no place for me to login, is just blank black screen.

---

### Post by vanadium on 2010-12-29
Sleep and hibernate in linux unfortunately does not always work well dependent on your hardware.

---

### Post by j1gs4w on 2010-12-29
> **vanadium said:**
> Sleep and hibernate in linux unfortunately does not always work well dependent on your hardware.

unlucky me I guess

thanks for the info

---

### Post by bluebubbler on 2011-01-04
> **j1gs4w said:**
> unlucky me I guess

thanks for the info
Well for me it is not the hardware.
 
 Running a 10.10 64 bit on a P4 3.6 DT CPU and have lost the Hibernate  option in my power button sub-menu in my screen menu bar. It was there  when I first installed Karmic, through 10.4 and a 256 Nivia vid card ..  but now with 10.10 recently installed I have no Hibernate option on my  shut-down menu from the screen menu bar.
 
 Read various threads and I've tried installing 'Hibernate' from  Synaptics, and the 'pm' and 'pmi' power management packages. Can use  term to use pm/ pmi to suspend, but not to Hibernate. Made sure there is  10Gb of linux-swap at the end of the HDD - but still no joy. No  Hibernate option in the power/shut-down menu or success via the command  line.
 
 Has anyone else had (and solved) this problem?

---

### Post by bluebubbler on 2011-01-06
> ** said:**
> 
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by bluebubbler on 2011-01-06
Seem to be having some problems with getting this to post - will try again...
--------
Well - found a solution to my own problem.
I had used GParted to format my swap partition and used the 'swapon'  option to set to be used as swap. However, I later found that on  rebooting, this allocation as swap (and the 'lock' on the GUI) has been  lost.
Reading further - love these forums!! - I found that Taurus in the  thread [http://ubuntuforums.org/showthread.php?t=249307](http://ubuntuforums.org/showthread.php?t=249307) shows a easy way  to ensure that this swap partition is allocated each time on boot by  editing the /etc/fstab file to include the line
/dev/sda4   none   swap   sw   0   0 where sda4 is my swap partition.
Wonderfully, on rebooting I now have a hibernate option in my power off menu!!!!

Thank you again Ubuntu forums!!

---

