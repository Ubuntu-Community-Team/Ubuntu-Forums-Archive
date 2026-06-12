---
title: "Installing Ubuntu 9.04 to Dual-Boot with XP Pro"
date: 2009-07-27
forum: General Help
---

### Post by Tetrapod on 2009-07-27
Hello,

I'm new to Ubuntu. Well, actually I don't even have it yet. I'm thinking about installing Jaunty so that I can dual-boot it with Windows XP Professional SP3, which I have currently. I have no idea how to go about doing this. I'm kind of confused if I need to make a CD, have an external hard drive, etc. I know that I have to set up space for the new OS to use, but again, I don't know how. If someone could please link me to instructions on how to do this, or give me a step-by-step, I would be very grateful. Also, any advice on this topic or information about the hard drive space thing would be great. I currently have a little less than 40GBs of free space on my hard drive. If you need any more information about my computer, simply ask or send me a PM.

Thanks,
~Tetrapod

---

### Post by merlinus on 2009-07-27
Useful guide here:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Here is a link with very valuable info:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by thundaraptor on 2009-07-27
I used the apcmag tutorial on how to partition the drives.  I backed up everything that was valuable, then resized the main parition in windows and created a 20gb partition to put ubuntu on.  Once this is done, all of which I did inside windows burn a cd with the intact iso file that you get as a download from ubuntu with whichever system you want to use (this is called a live cd).  Then put that disc in your drive and enter the drive sequence as the computer is booting like F8 or seomthing and it will ask you which drive to boot from.  Choose the cd/dvd/optical drive and then this will initiate the ubuntu load sequence.  It is quite intuitive once you have the partition made.  I think some people use the partition editor inside the ubuntu live cd but I wanted to repartition in windows as I had never worked with ubuntu before and didn't really know if it would workout.  

That was in January of this year and I have since almost entirely abandonded windows on my laptop and built a completely intel/windows free desktop system that has jaunty on it.  Am a huge fan of this move but it can be frustrating in the beginning.  Try to get another computer with internet with you while you do all this so that you can look up problems on the net while working on the other one.  

Happy hunting.

TR

---

### Post by RJ12 on 2009-07-27
I just did this today and felt the way you did all I did was first.
1.Boot into live CD
2.Choose Try Ubuntu...
3.Open up install with the icon on the desktop'
4.Choose Forward and get to the Where would you like to install part or something like that
5.If you are using 9.04 it will say install side by side or something like that
6.Click it and move the slider bar to adjust the sizes
7.Click Forward and enter the details click forward and install when its done reboot and it will spit the cd out at you take out the cd and press enter I choose Windows XP first to make sure it was bootable and it will do a checkdisk since you resized the partition it should come up with no errors then boot into Ubuntu and login and viola! there you have it.

This is assuming you havent partitioned anything yet and installing on the same drive as Windows XP

Dont forget to backup

---

