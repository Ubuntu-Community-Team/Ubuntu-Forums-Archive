---
title: "amd Geforce 6600 video install problem"
date: 2006-05-12
forum: General Help
---

### Post by johnwren on 2006-05-12
I am doing a clean load of 5.10 Breezy on an AMD Athlon 64 3000+ with an ASUS A8N-E mobo and an NVIDIA Geforce 6600.  Ubuntu installs but I cannot start X.  I have tried to configure xorg.conf using dpkg-reconfigure xserver-xorg, and manually set things for my BenQ PF71V+ lcd monitor, but have failed.

Help!

dmesg reports something odd with the pcie bus (see attached), and I have also included the output of my Xorg.0.log and my xorg.conf.

If this should be in the install section, please let me know.

Is there any other way I could get my screen up and running, perhaps using vesa??

---

### Post by johnwren on 2006-05-12
didn't see my log file attached -- Ah, it's over the 19Kb limit -- here it is as a zip -- sorry about that.

---

### Post by tseliot on 2006-05-12
```
sudo nano -w /etc/X11/xorg.conf
```
Set the driver to "vesa" in the Section Device of the file.
Save the file and exit (press CTRL+X)

Then type:
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)

Then I warmly recommend you to install the proprietary drivers for your card:
[My guide for Breezy 5.10]("http://www.ubuntuforums.org/showthread.php?t=75074")
OR
[My guide for Dapper 6.06]("http://www.ubuntuforums.org/showthread.php?t=139264")
OR
just use my script to automate the installation of the latest driver:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

