---
title: "Help with Graphics driver load"
date: 2012-03-24
forum: General Help
---

### Post by Cr0n_J0b on 2012-03-24
I'm not sure why this has to be so hard...but I have a Graphics chip on my board that isn't being picked up by the X server.  I have to correct driver and I have put them in the xll directory, but I don't have an xorg.conf file to edit.

My issue is that the resolution is 800x 600 right now and I want more.

I'm running a fresh install of 11.10.

any help would be appreciated.

thanks

---

### Post by Mark Phelps on 2012-03-24
Since we're not mind readers, it would help if you told us which graphics chip you have.

IF you don't know, then open a terminal and enter "lspci" -- and look for the line containing "VGA".  That will display the make and model video chip.  Post that information back here.

---

### Post by Cr0n_J0b on 2012-03-25
Sorry, it was more of a generic question like how do you load a graphics driver in general in 11.10.  In the older version I know that you could run an x config command and it would generate a config file, but I don't see that command now, nor do I have the xconfig file.

the graphics card is an XGI Z7/Z9 (XG20 core) chip, which I gather is pretty rare.  I have a sis driver that is supposed to work, but I don't know where to insert the lines that point to it.

---

### Post by collisionystm on 2012-03-25
Have a look at this...

[http://www.linuxquestions.org/questions/linux-hardware-18/getting-an-xgi-volari-z7-working-with-xorg-837500/](http://www.linuxquestions.org/questions/linux-hardware-18/getting-an-xgi-volari-z7-working-with-xorg-837500/)

---

### Post by Mark Phelps on 2012-03-25
> **Cr0n_J0b said:**
> Sorry, it was more of a generic question like how do you load a graphics driver in general in 11.10.

With the removal of the Xorg.conf file, customizing driver installations in Linux got more difficult.

The link provided gives you some info you need for SiS drivers.

---

### Post by Cr0n_J0b on 2012-03-28
thanks for the responses.  I saw the link, but they didn't get it working.   I have a sis driver that i got from another spot but the person there just put it in the conf file.  How do you add a drive in 11.10 if there is no conf file?

---

