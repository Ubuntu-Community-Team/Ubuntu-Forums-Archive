---
title: "How Safe is VirtualBox?"
date: 2011-05-03
forum: General Help
---

### Post by Quarkrad on 2011-05-03
Newbie running 10.10.  I have got VirtualBox 4 up and running with a winXP guest and I have itunes/ipod full functionality and TomTom Home working - the two main things that cause me to dual boot Ubuntu and winXP. Looks like I can now dump my winXP partition.  Thing is, I'm nervous about the internet connection via winXP in VirtualBox (VB) re spy/mailware and virus attacks.  I intend to surf the web only in my Ubuntu environment - not VB/winXP, but for my TomTom I will use a net connection to the main TomTom site for updates and it would be nice to access some other GPS based sites for creating things called 'points of interest' to load onto the TomTom.  Should something nasty get into my winXP software how dangerous could it be to my main Ubuntu environment?  I'm thinking VB acts as some sort of shell that winXP sits in - if something gets into winXP can it get out through VB and into my main system?  (I believe that, to a degree, a windows based 'nasty' will not do much damage to a Linux environment as it will not recognise it and not be able to do what it was designed to do - but I could be wrong).

---

### Post by Jouke74 on 2011-05-03
There are several options in Virtualbox and Windows XP that you can use to increase your safety:

1. Make sure that the VM cannot access any folders on your host machine (So no shared folders). 

2. Install anti virus software in the virtual machine like you would on a normal windows computer. Update XP to the latest service pack and do security updates.

3. Use snapshots, so if the VM is infected return to a previous snapshot. This will also undo all other updates you did in the virtual machine.

4. Like 2, make a complete copy of the VM and store it somewhere.

---

### Post by snowpine on 2011-05-03
Snapshots are an awesome feature! You can restore your XP virtual machine to a "virgin" state with a click.

I recommend keeping your Windows partition just in case. I am glad I have mine once or twice a year when I want to run a Windows app natively. If you really need to reclaim the HDD space then you can clone it to an external drive using Clonezilla or similar, a nice little time capsule of your personal computing history!

---

