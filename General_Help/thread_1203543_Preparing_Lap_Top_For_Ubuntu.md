---
title: "Preparing Lap Top For Ubuntu"
date: 2009-07-03
forum: General Help
---

### Post by james.brantley on 2009-07-03
[SIZE=2]Hello all, I am preparing to install Ubuntu 9.04 in a Dell Inspiron running Vista. The machine is failing to recognize the optical drive. I have went to device manager and uninstalled the driver and rebooted but am then told that the driver was not properly installed. After doing this several times I am beginning to assume that the optical is bad. It is getting power, the green led flashes when you first insert a disc but then stops. The drive also does not show up in start/computer at all. Does anyone have any input that could help me verify the drive is bad?

The drivers are the most current
[/SIZE]

---

### Post by wpshooter on 2009-07-03
1) Make sure that the firmware (not to be confused with driver) on the CD drive is on the latest and greatest version.

2) Is CD drive being detected and properly displayed in the BIOS.  

3) Are the parameters for the CD drive set correctly in the BIOS.

4) Go to Dell website and download and run the diagnostics on your computer, particularily the test that checks the integrity/function of the CD drive.

P.S. - How long has it been since you cleaned the heads on the CD drive ?

Good luck.

---

### Post by Joe88 on 2009-07-03
If the drive is not detected by your BIOS (the software you see working when your computer starts up) then its either broken, or its not properly connected to your laptops motherboard. 

The power connection for the drive sounds like its connected(green power LED is on), but the drives data connection possibly isn't.

---

### Post by james.brantley on 2009-07-03
[SIZE=2]Thanks for all of your input folks. What I ended up doing was going into the registry and removing the upper and lower filters of the cd rom entries. I've learned that sometimes Vista Service Pack 2 can cause this issue. So off I go to transform another machine into a beautiful work of art! (ubuntu!)

[http://support.microsoft.com/default.aspx/kb/929461](http://support.microsoft.com/default.aspx/kb/929461)[/SIZE]
[SIZE=2]
 


[/SIZE]

---

### Post by moster on 2009-07-03
Or you could just boot Ubuntu from USB stick. It would be faster and more quiet :)
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

