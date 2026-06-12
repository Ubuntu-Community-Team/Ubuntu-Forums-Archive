---
title: "emeral themes dissapear on startup or restart"
date: 2011-03-08
forum: General Help
---

### Post by yargdraeb on 2011-03-08
I have recently reinstalled Ubuntu 10.10 with Compiz and emerald themes. I've replaced the default window manager in Compiz with emerald and everything works fine until I shut down and restart. The I have no window theme at all. If I go to the window decorator and reinstall the default manager and then once more enter emerald --replace everything is fine until the next time I restart. I guess that I could just leave everything running but that's not the kind of guy I am. can you give me a hand here?

     AMD 965 quad core 
     4 gigs RAM
     Navida Gforce GTX 260

---

### Post by mcduck on 2011-03-08
What exactly have you done to configure Compiz to use Emerald as it's default decorator?

The correct way to do that would be setting the "Command"-field in the Window Decoration"-plugin's settings to "/usr/bin/emerald".

---

### Post by yargdraeb on 2011-03-09
Now the problem has gotten worse. I am unable to get Emerald to work at all. When I go to system>preferences>appearance>visual effects and select and select extra everything seems right until I go to compiz to make changes. when I select desktop cube, rotate cube,reflection and deformation everything works a it is supposed to until I close the window. then everything reverts back to to no visual effects at all. when I reopen system>preferences>appearance> visual effects I find that no effects are selected. When I reopen compiz Desktop cube ,rotate cube and cube reflection and deformation are no longer selected. As far as the window decorator is concerned I can no longer get Emerald to work at all. I've tried Emerald --replace and /usr/bin/emerald decorator. I do however get the default compiz theme.

---

### Post by yargdraeb on 2011-03-09
I may have solved my own problem. I started a terminal and under sudo entered emerald --replace. The the problem seems to be fixed. I restarted and everything work as it should. I don't understand why I had this problem in the first place. When I had Ubuntu 10.10 install before everything worked just fine then My hard drive went south and when I reinstalled the problem reared it's head. I hope this may help others solve similar problems in the future.

---

### Post by mcduck on 2011-03-09
> **yargdraeb said:**
> Now the problem has gotten worse. I am unable to get Emerald to work at all. When I go to system>preferences>appearance>visual effects and select and select extra everything seems right until I go to compiz to make changes. when I select desktop cube, rotate cube,reflection and deformation everything works a it is supposed to until I close the window. then everything reverts back to to no visual effects at all. when I reopen system>preferences>appearance> visual effects I find that no effects are selected. When I reopen compiz Desktop cube ,rotate cube and cube reflection and deformation are no longer selected. As far as the window decorator is concerned I can no longer get Emerald to work at all. I've tried Emerald --replace and /usr/bin/emerald decorator. I do however get the default compiz theme.

You shouldn't use the visual effects options in the Appearance-dialog if you have made any custom settings in Compiz, those options toggle between Metacity (the no effects -option) and two pre-configured Compiz configurations.

So if you select the Normal- or Extra-option in the Appearance-dialog, it will load that preset and clear whatever custom Compiz settings you have made.

(And in the same way, if you selct the Normal option there, for example, and then make any settings of your own in CompizConfig Settings Manager, the selected option in Apperance dialog should change into "Custom" instead of any of the three normal settings.)

What comes to you having to run "emerald --replace" with sudo, you really shouldn't need to do that, your normal user should have all the permissions required to select his own window manager/decorator. The only reason I can think of which could result in needing to use sudo to do that is you running some graphical tool with sudo (instead of gksudo) or using sudo with some tool that doesn't require it, resulting in some of your user's setting files becoming owned by root. You might want to search through your home directory and make sure that all the files belong to your user account.

---

