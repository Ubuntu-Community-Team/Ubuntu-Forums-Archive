---
title: "Jaunty Jackalope install failure"
date: 2009-07-17
forum: General Help
---

### Post by FuzzyFeat on 2009-07-17
I have repeatedly tried to install Jaunty Jackalope. No luck. I get to the screen where the partition app looks for partitions and the system hangs. Once I received a notice that it wanted to remove my active partitions. I said NO and that was it. 

I prepared a partition for Jaunty Jackalope and would like to install it there, but I do not get the opportunity. I experienced this problem before creating the partition too. Thought making a partition would solve it, but no such luck.

Installing from Ubuntu CD
I have windoz ME and Ubuntu in separate partitions and dual boot.

---

### Post by utnubuuser on 2009-07-18
Is the partition you created an "unused space"? 

An unused space on the hdd seems to be the easiest way of doing the install unless you choose manual partitioning.

Also, if you're installing from the live desktop rather than the "Install Ubuntu" menu option, you might have to turn off your swap partition before starting the installer.  (swap _might be_ an issue if you're installing from the desktop).
In gparted (System >> Administration >> partition editor. Select your "swap" partition, then right-click and select Swapoff.

---

### Post by Tman5293 on 2009-07-18
How old is this hard drive your using cause it might have bad sectors.

Any info you can give us about your computer would be helpful.

---

### Post by FuzzyFeat on 2009-07-18
Computer is a Dell Inspiron 8000. Hard drive is two years old. There were no bad sectors before partitioning. 
I am running Ubuntu 8.04 LTS which does not show Gpart in the System/Administration menu. 

I have tried to install from the Ubuntu desktop and from the CD. 

Have checked the HD for errors. None
Checked memory for errors. None
Turned off swap partition.

I receive no options for partitioning- the system hangs after I select the keyboard (step 3)and I click 'Forward'. The partitioner activates and shows the progress bar. One time I got the alert message that the installer detected partitions on /dev/sda, dev/sdb and asked to remove my active partitions. Also said that there was an active partition to which Ubuntu could be installed. I carefully read the ambiguous message, and clicked 'NO' to removing active partitions. That was it.
Just the little busy icon spinning away for hours on end.

The next two times I attempted to install from the CD that Alert box did not come up - Just the spinning icon merrily drilling a hole to nowhere on my screen.

---

