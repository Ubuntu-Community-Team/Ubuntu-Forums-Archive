---
title: "Bad Install?"
date: 2012-08-03
forum: General Help
---

### Post by Mingan on 2012-08-03
I installed Ubuntu 12.04 on a 150GB Partition with Windows 7SP1.  The total Disk size is 960GB.  4GB RM but only 3GB read.

The install seemed to go well but now when I log into the Ubuntu, I have to wait for the unity icons to light up.  They are first grey and white.  Then they light up, then back to grey/white, then light up again.  I click on an icon (firefox) and it is like 20 secs latter before it shows the name, and at least another 20 secs or more before it loads a page.

Same thing for all other Icons.  I cant even shut the computer down.  I have to hold down the off button.

Is it a bad install and if so how do I fix it?   Could it be a driver conflict?  Could I try reinstalling on the same partitions?  Please help I hate Microsoft and think of it as a Virus Magnate. 

Please ask for other info if you can help.

---

### Post by ventrical on 2012-08-03
What kind of video adapter card are you using?

---

### Post by Mingan on 2012-08-03
Nvidia duel monitor (HDMI)

---

### Post by howefield on 2012-08-03
Thread moved to "*General Help*" forum.

---

### Post by Mingan on 2012-08-03
Do people think its a video card thing?  I want to get away from Windows 7SP1 as it makes me peeved.

---

### Post by Dylan1473 on 2012-08-03
Nvidia is generally pretty well supported in Linux so it's probably not the graphics card. Have you tried going into Unity 2D when you log in? I'm not using Unity right now but if I recall correctly there should be a drop down box that lets you switch between desktop environments when you log in.

EDIT: Another interesting note - you have 4GB RAM but only 3GB is read? Are you using 32 bit Ubuntu? Most modern computers run on 64 bit, especially if they have 4GB of RAM (you need 64 bit to properly support 4GB or more of RAM). You might end up reinstalling anyway if you want to make use of all your RAM.

Also yes, you should be able to reinstall Ubuntu on the same partitions. You might even be able to keep your old home partition if you made a separate one when you installed or if you're willing to go to a bit more effort to transfer it over. I'd recommend this only if you've actually been using it long enough to have anything worth saving in there though.

---

### Post by Mingan on 2012-08-03
Except for having to keep Windows 7SP1, I dont have anything on the Linux side I have to keep.   What is the first step to reinstall?

---

### Post by Dylan1473 on 2012-08-03
Same way you installed it in the first place, just pop in the disc/flash drive. You might want to get the 64 bit version if you didn't already though (of course make sure you're using a 64 bit processor but it'd be really weird if you had 4 gigs of RAM and a 32 bit one). I really recommend trying out the LiveCD first if that's what you're using to install just to make sure the same problem doesn't occur. 

If I recall correctly at some point in the installer you'll get a choice about where you want to install Ubuntu and one of the options will be to replace an old Linux install, that's what you want to do.

---

### Post by Mingan on 2012-08-12
I reinstall about a week ago.  It worked. But this time I didnt install the video drivers from Nvidia, and used what came with the Ubuntu install.  so far no problems.  Thank you Everyone!

---

