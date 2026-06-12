---
title: "Help with bcm4313 wireless card"
date: 2011-03-21
forum: General Help
---

### Post by ald3n3 on 2011-03-21
i have a dell inspiron 15r and i installed ubuntu 10.10 side by side with windows. But ubuntu can't read my wireless driver. How do i make this work? please consider me a newbie with linux. 

P.S. i don't have access with a hardwire internet but i do have another laptop incase i need to download anything

Thank you so much! i've searched the net but the instructions are all so confusing :/

---

### Post by mikewhatever on 2011-03-22
Here is how to install the driver without internet access.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

---

### Post by ald3n3 on 2011-03-22
but that tutorial doesn't say it supports bcm4313 drivers... would that still work?

---

### Post by TeoBigusGeekus on 2011-03-22
Oh hai thar!

---

### Post by ald3n3 on 2011-03-22
> **TeoBigusGeekus said:**
> Oh hai thar!
 
 
haha sorry... i already spent about 3 hours before i posted this so i was laready burnt out... funny coz it was the easiest thing when i installed the wifi driver on my hp dv9000 with bcm4312... and i did the same thing with my inspiron15 with bcm4313 it didn't work... but i will try the tutorial you posted later when i get home and give you guys an update... Thanks a lot i hope this will work

---

### Post by ald3n3 on 2011-03-22
I'm so sorry please bare with me... that tutorial will work for 10.10 version right?

---

### Post by mikewhatever on 2011-03-22
Perhaps you should take a break and finish it tomorrow. I'm having serious doubts you can follow the steps in this state of concentration. ;)
The howto is good for any of the following - 9.10, 10.04, 10.10.

---

### Post by ald3n3 on 2011-03-22
> **mikewhatever said:**
> Perhaps you should take a break and finish it tomorrow. I'm having serious doubts you can follow the steps in this state of concentration. ;)
The howto is good for any of the following - 9.10, 10.04, 10.10.
 
 
Will do... i'll do it first thing after i get home from work. Hopefully i'll be able to concentrate by then and get it to work. Thanks!

---

### Post by nothingspecial on 2011-03-23
The easiest way is if you have a live cd.

If you installed from the cd, pop it back in the drive, then in your menu go System > Administration > Synaptic Package Manager.

Click the Settings tab and choose Repositories.

Check/tick the little box in the cd-rom box at the bottom. Close the settings window and click reload at the top left.

In the search box type *bcmwl-kernel-source*

Click search then choose to install it.

Restart :popcorn:

If you don't have the cd, post back.

---

### Post by s.fox on 2011-03-23
Post [#9]("http://ubuntuforums.org/showpost.php?p=10591880&postcount=9") merged into thread at [nothingspecial]("http://ubuntuforums.org/member.php?u=491516")'s request.

---

### Post by ald3n3 on 2011-03-24
> **nothingspecial said:**
> The easiest way is if you have a live cd.
 
If you installed from the cd, pop it back in the drive, then in your menu go System > Administration > Synaptic Package Manager.
 
Click the Settings tab and choose Repositories.
 
Check/tick the little box in the cd-rom box at the bottom. Close the settings window and click reload at the top left.
 
In the search box type *bcmwl-kernel-source*
 
Click search then choose to install it.
 
Restart :popcorn:
 
If you don't have the cd, post back.
 
 
I did it this way but it was giving me an error about post install, something like that. So i finally remembered that i do have internet access (MY PHONE via usb=D) so i just downloaded bcmwl-kernel-source not from the cd but straight from the http source. then it's up and running.
 
Now my next step is enabling the HDMI port because ubuntu is not reading it at all. any tips? i have the new Inspiron 15r laptop

---

