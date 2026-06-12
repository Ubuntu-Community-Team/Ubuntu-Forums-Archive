---
title: "Need help on custom launcher icons"
date: 2009-11-05
forum: General Help
---

### Post by dfro on 2009-11-05
For a long time it has bothered me that I can't figure out how to attach custom icons to Launcher buttons in the Launch panel.

What seems to be the standard method does not work for me. 

I go to the launcher and right click 'Properties'. When I am in the 'Launcher Properties' window, I click on the existing icon, which puts me in a 'Browse icons' panel. The default folder that shows up usually has some choices, but there are many other locations for .svg and .png icons to use. When I hit the 'Browse' button to search these other folders, I only get blank/light blue folders showing that there is nothing there. The only folder that shows any icons to choose is the default folder.

Does anyone know what I am missing. It is a directory/file permissions issue?

Thanks,
Dave

---

### Post by MrGrumpyArse on 2009-11-06
I believe ive been having the exact same problem, someone kindly posted a simple solution that worked for me, 

[http://ubuntuforums.org/showthread.php?p=8257686#post8257686](http://ubuntuforums.org/showthread.php?p=8257686#post8257686)

Hope that helps

Regards

MrGrumpyArse

---

### Post by dfro on 2009-11-06
Ha! I tried the same thing and was going to post my solution, but you beat me to it. To save others the click, here is what I did:

I open a file browser and navigate to the folder that contains the icon I want. I right click on the launcher button and choose 'Properties'. I click-drag the icon image from the file browser folder and hover it over the default 'spring' image - and voila! - the icon shows up on the panel. 

If I click-drag the icon image up to the launcher button on the panel, it doesn't work. It only works when you are in the 'Launcher Properties' dialog box.

This one has been bugging me for years.

Thanks,
Dave

---

### Post by dfro on 2009-11-06
Okay I figured out a few more things. There have been several bug reports on this. Here is one of them. I did not read the duplicates:

[https://bugs.launchpad.net/ubuntu/+source/libgnomeui/+bug/116443](https://bugs.launchpad.net/ubuntu/+source/libgnomeui/+bug/116443)

Here is what is up. If you right click on a launcher button and and choose 'Properties' you open up the 'Launcher Properties' window. Click on the default icon and you go to the 'Browse icons' window. If you click the 'Browse...' button you go into a window that browses FOLDERS, NOT icons. So, you have to know exactly which folder your icon is in, because the browser is browsing folders, NOT icons or anything else, only folders. If you have navigated to a folder that has 100 icons in it, but no folders, then it show the blank/light blue screen. 

So, if you are clairvoyant and know exactly what folder the icon is in - then you navigate to that folder and click the 'Open' button. The 'Browse icons' window chugs for a few seconds and loads the icons in that folder. Now you can choose the icon and attach it to your launcher. VERY counterintuitive, IMHO! 

This should be fixed.

Dave

---

### Post by MrGrumpyArse on 2009-11-07
Thank You for the info. as you say its all abit counterintuitive, but at least there is a couple of ways to get around it for the time being.... I suspect this thread will prove useful to others too.

Regards

MrGrumpyArse / Mark

---

