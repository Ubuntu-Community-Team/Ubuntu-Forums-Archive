---
title: "Please help!"
date: 2011-04-02
forum: General Help
---

### Post by OxCxPunk on 2011-04-02
I have been trying to burn a iso for a couple days now and don't know where else to turn. I have tried the brasero way, but it gets stuck at this creating checksum thing for 8 hours and does nothing. I don't know how to do it on acetoneiso. I think I installed poweriso but don't know how to bring it up. I also tried the cd dvd writer and clicked write disk but it went away and did nothing. I am still a noob at Ubuntu and I am going a little crazy with this. So my question is how do I burn a iso on Ubuntu 10.10? What is the noob way?

---

### Post by TeoBigusGeekus on 2011-04-02
Cd or dvd?

---

### Post by OxCxPunk on 2011-04-02
Dvd

---

### Post by TeoBigusGeekus on 2011-04-02
Open terminal and give
```
growisofs -dvd-compat -Z /dev/dvd=/path/nameofimage.iso
```
Replace path with the path of your iso and nameofimage with its name.
If the above doesn't work, replace /dev/dvd with /dev/sr0 or /dev/scd0 or /dev/cd, etc.
Post back with results.

---

### Post by Shibblet on 2011-04-02
I had this problem a few months back.  This was with a double-layered DVD. 

I found that I didn't have my drives current firmware.  And as most firmwares are only upgradable via Windows, you may have to have a virtual machine set up to do that.

Once I updated the firmware for the DVD-RW drive, everything worked great!

---

### Post by Topsiho on 2011-04-02
Brasereo works well on my system: burn image file (lowest option). In fact it is the most simple and robust burning application I know.

I don't remember it calculating a checksum (such as K3B does), but maybe your .iso file is corrupt. Please check it in a terminal:

md5sum nameoffile.iso

just to see it does this, and compare result to correct result if you know it.

Topsiho

---

### Post by OxCxPunk on 2011-04-02
I keep getting errors I am not sure how to put in the path but I am putting it /Desktop/nameoffile.iso I put the iso file on my desktop. I am getting this error 
-( unable to open64("/Desktop/Mine.iso",O_RDONLY): No such file or directory

---

### Post by OxCxPunk on 2011-04-02
I don't know what it was but after I restarted, I tried write to disk again and brasero is writing it. No creating image checksum so I am good. Thank you so much.

---

### Post by TeoBigusGeekus on 2011-04-02
Make it
```
~/Desktop/Mine.iso
```
~: shortcut for /home/yourusername

---

### Post by madmax75 on 2011-04-02
You can also try the **Xfburn** cd/dvd burning program. I think it's  the default burner for the XFCE dekstop environment, but of course you can run it in Gnome as well. It's in the repositories. Simple, fairly lightweight, does the job.

---

### Post by lisati on 2011-04-02
You might want to have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Note: although the page is aimed more at preparing an installation disk using different OSes, much of the information is still relevant.

---

### Post by Topsiho on 2011-04-03
"I don't know what it was but after I restarted, I tried write to disk again and brasero is writing it. No creating image checksum so I am good. Thank you so much."

Glad you finally succeded in burning your .iso, using Brasero.

I never had any trouble using Brasereo. Used to use K3B, but though it looks much nicer than Brasero, Brasero works when K3B doesn't (for me).

Good luck, and thanks for reporting back.:D

Topsiho

---

