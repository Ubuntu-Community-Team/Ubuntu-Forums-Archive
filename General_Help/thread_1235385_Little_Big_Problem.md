---
title: "Little Big Problem"
date: 2009-08-09
forum: General Help
---

### Post by Sticks_uk on 2009-08-09
Ok so after throwing my windows cd's out after a clean ubuntu install I have run into a small problem, my wifes driving theroy test cd requires windows....

Is there any kinda of windows emulator/program to get this to work ?

---

### Post by jasonsjunk on 2009-08-09
Try running it under WINE or you can install virtualbox and run Windows in a virtual machine.  You can download both via Synaptic.

---

### Post by DeMus on 2009-08-09
> **jasonsjunk said:**
> Try running it under WINE or you can install virtualbox and run Windows in a virtual machine.  You can download both via Synaptic.

Virtual machine?? Impossible!!
The OP threw out his Windows CD so he can't install that anymore. :P

---

### Post by Sticks_uk on 2009-08-09
Thanks for the fast replies.
I installed WINE and tried to run the theory test dvd but I get an error message saying this is a "virtual DVD" 

Any ideas ?

---

### Post by DeMus on 2009-08-09
> **Sticks_uk said:**
> Thanks for the fast replies.
I installed WINE and tried to run the theory test dvd but I get an error message saying this is a "virtual DVD" 

Any ideas ?

When you see what is on the DVD, what do you see then? Normal installation files for a windows install, or do you see a .iso file, or a file with a different extension?

---

### Post by Sticks_uk on 2009-08-09
lots of files on the disc but its a standard .exe setup file

---

### Post by P4man on 2009-08-09
Before trying very hard, look it up in wine db. Is it this program by any chance?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6246](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6246)

If so, you'll need a virtualmachine (virtualbox is a good choice) though even that may not work if the app uses 3D acceleration, and you will have to pick up those windows CDs you just tossed out of the window :)

---

### Post by Sticks_uk on 2009-08-09
aye thats it :) I'm gonna drive to my mates house and go get a windows cd. I sure to get some stick for this after telling him I will never use windows again :lolflag:

thanks again all

---

### Post by ad_267 on 2009-08-09
Virtualbox actually supports 3D acceleration now :). I'm not sure about Direct X but OpenGL applications definitely work.

How did you try to run the dvd? Do you get that message if you right click on the .exe file and select "run with wine program launcher"?

---

### Post by Barafu Albino Cheetah on 2009-08-09
The only driving tutor program I've ever seen contains a security system as if it is a 30 000$ per copy project. You can not run most copy-protection progs with wine. 
Solutions I think of: 
Illegal:  
1)Crack your driving program for No-DVD effect. 
2) Install cracked windows into virtualbox.
Half-Legal: 
3) Find any evaluation copy of windows, install it into virtualbox, install your app, use for 30 days, delete virtual machine, repeat. 
Legal: 4) Don't use this app.

P.S. VirtualBox in repositories is always too old, as well as Wine. Both this teams keep their own repositories, use them. Virtualbox supports directx since 3.0.1

---

### Post by Sticks_uk on 2009-08-09
thanks :) got virtual box to run it just have no sound do I need to reinstall my Motherboard CD (has the on board sound card driver) within the windows environment ?

---

### Post by P4man on 2009-08-09
No. You now have a virtual machine, which shares (almost) nothing with your actual hardware. it has a different (you guessed it: virtual) soundcard, your motherboard drivers are highly unlikely to work.

Check if you enabled a sound at all in virtualbox settings. The (virtual) AC97 card doesn't need drivers in windows AFAIK. Perhaps change the host audio driver (that is, the ubuntu driver) in the audio settings page?

---

### Post by Sticks_uk on 2009-08-09
I do not get sound within ubuntu for example start up sounds, when I adjust the sound using the audio settings in the top bar(do not get that bing sound) although my radio works so I guess my sound card is working.

I would just like to say thanks again for helping me out with this

---

### Post by ad_267 on 2009-08-09
Sound is usually disabled by default in Virtualbox. You have to enable it from the virtual machine settings.

---

### Post by Sticks_uk on 2009-08-09
that has been enabled already :)

---

### Post by Sticks_uk on 2009-08-09
> **P4man said:**
>  Perhaps change the host audio driver (that is, the ubuntu driver) in the audio settings page?

Good Job \\:D/

was looking for this inside ubuntu not virtual box hehe

thank you the missus will be over the moon :)

---

### Post by zkriesse on 2009-08-09
Yo it's cool man...it happens to all of us...if we all knew it all there wouldn't be a need for the Ubuntu Forums....

---

