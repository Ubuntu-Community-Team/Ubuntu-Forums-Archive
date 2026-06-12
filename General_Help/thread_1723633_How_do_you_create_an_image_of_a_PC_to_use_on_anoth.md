---
title: "How do you create an image of a PC to use on another"
date: 2011-04-07
forum: General Help
---

### Post by Jonners59 on 2011-04-07
I do not know if this is possible, but I have a laptop in another country that I visit quite frequently.  I wish to re build it in Ubuntu from the image of a mcahine I have here such that when I set it up I need not go on line for updates and installed apps.

A couple of reasons for this.

Internet in this other country is by land line and VERY expensive and slow

It would be useful if it were an image as I am happy with the install on the laptop I have here,, and do not want to spend an age on my hols configuring and installing and playing about...  Just install Ubuntu from my CD and then the image to create the same machine.....

Can this be done and if so how.  PS I have until mid day tomorrow!!!!  I don't ask much:D

---

### Post by seawolf167 on 2011-04-07
Easiest way IMO - create an image of your current hard drive (with installed OS's) using a [Clonezilla]("http://www.clonezilla.org") LiveCD. Then when you get to your other computer (take with you the clonezilla cd & external hard drive containing the image file), write that image onto your other computer. You'll now have an exact duplicate of your first computer.

You'll have to make a couple changes such as:

[LIST]
[*]region settings (since you're in a different country)
[*]computer name (you'll probably want to assign a new computer name)
[*]hardware drivers (unless the computer is exactly the same model, you'll need different drivers - specifically things like video cards &/or network cards - which are available over your slow & expensive internet unfortunately)
[/LIST]

---

### Post by Jonners59 on 2011-04-07
Do I need to install Ubuntu on the machine first or would this CD boot and install automatically.

What I was planning to do was to use my Ubuntu CD to delete the HD, so i have a clean drive, then install, but if there is no OS on there then how does the image and extternal hard drive work...

---

### Post by seawolf167 on 2011-04-07
Nope, you wouldn't need to do any pre-setup on the target machine (no formatting, partitioning, anything). Just ensure that the target hard drive is larger than or equal to your source drive in size.

For example, I have a dual boot system at home, I've had to restore a couple times from an imaged drive, after writing the image (stored on an external hdd from whenever I made it) quite literally everything is the same as when I made the image (MBR, GRUB2, Windows & Ubuntu). I don't have to edit or make any changes.

However, since you are going to write the image to a computer *different* from the one you made the image of, the hardware will necessarily be different which means you'll have to make a few tweaks (as listed above).

Clonezilla has a LiveCD, you can boot directly from it so you don't need an OS on the source or target computers.

---

### Post by Jonners59 on 2011-04-07
OK, seawolf
I think I am there...  1st important question.  The HD of the machine I am copying is 300G, but only 50G is currently in use... of 200G formatted. Screen shot enclosed.

I know the machine receiving the image is only 80G...  Will it work?

In the meantime I am downloading the app and about to burn on to a CD.  When I do so will it also burn the laptop's HD?

---

### Post by seawolf167 on 2011-04-07
You'll write the image to a disk so it's bootable (i.e. don't just write the iso file as a data file on the cd).

Then boot into the Clonezilla LiveCD and follow the prompts (it'll tell you when to connect your external drive, walk you through options, etc.)

That said, to burn an image from a large drive to a smaller one, I only know one way to do it:

[LIST]
[*]Fire up GParted from a Ubuntu LiveCD
[*]Resize your partition so that it will fit on the smaller drive (i.e. so it is <80GB)
[*]Reboot into Clonezilla LiveCD
[*]Write the partition of your now smaller OS onto your external hdd
[*]Boot up your target computer with Clonezilla
[*]Restore your selected (now smaller) partition to the smaller disk
[/LIST]
Edit: Found a how-to with pictures online [here]("http://geekyprojects.com/storage/how-to-clone-hard-drive-to-smaller-drive/")

---

### Post by MBybee on 2011-04-07
Not sure on clonezilla - but I know that I've used Remastersys for this, and the respective drive sizes don't matter (as long as you have enough space for the 'used' portion).

---

