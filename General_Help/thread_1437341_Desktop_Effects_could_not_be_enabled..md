---
title: "Desktop Effects could not be enabled."
date: 2010-03-23
forum: General Help
---

### Post by gear.h34d.2012 on 2010-03-23
Hey all, hope everything is well. I know this has been asked a thousand times, but from every thread I've read, I can't find anything to help. I just freshly installed Ubunut 9.10 on my Dell XPS M1530 and I've run into this issue. (I had it once before and fixed it. The fix was somewhere along the line of swtiching to full screen terminal, no GUI, and running a command along the lines of "sudo apt install /home/user/NVIDIA ******. That worked, and I've tried it again and it's a no go. I miss my old Ubuntu book where I had it all working; My cube, my gDesklets, and all that exciting stuff. Any help you guys could offer would be greatly appreciated. Thanks.





~Cheers

---

### Post by cogier on 2010-03-23
If you know which Nvidia card you have there are drivers in the Software Centre (Applications>Ubuntu Software Centre) Type NVIDIA in the search window.

---

### Post by uylug on 2010-03-23
I am guessing that you installed the NVIDIA drivers because you

> had it once before and fixed it
If you haven't then go to the NVIDIA site, download the appropriate driver and then kill Gnome by doing CTRL + ALT + F1

and then running:

```
sudo bash file_you_downloaded
```This way has always worked for me, installing it through Ubuntu recommended ways never worked fine for me.


Assuming that your drivers are fine, what i do is:

```
rm .config/compiz -r
```This removes your current compiz configuration, you'll need to logout and then login again. Sometimes restarting is never a bad idea.

Sometimes this happens because the compiz configuration gets messed up. I have no idea why.


You can rename the folder if you don't want to lose your current configuration.

---

