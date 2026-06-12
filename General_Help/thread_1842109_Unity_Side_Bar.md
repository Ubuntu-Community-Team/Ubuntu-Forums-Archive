---
title: "Unity Side Bar"
date: 2011-09-10
forum: General Help
---

### Post by Afterlithe on 2011-09-10
Hello everyone,

Brand new to ubuntu 11.04 here.  I have tried to get the side bar to show up on my desktop with no luck.  I have set the "never hide" option in the compizconfig setting manager, and it still doesn't work.  Any help would be appreciated.

Thanks.

---

### Post by snip3r8 on 2011-09-10
Try switching to another setting,logging out and back in again and changing it back to never hide

---

### Post by harlequin_ on 2011-09-10
> **Afterlithe said:**
> Hello everyone,

Brand new to ubuntu 11.04 here.  I have tried to get the side bar to show up on my desktop with no luck.  I have set the "never hide" option in the compizconfig setting manager, and it still doesn't work.  Any help would be appreciated.

Thanks.

Hi, welcome to the forums!

It is not clear to me what exactly you mean by getting the Unity launcher to show up on your desktop. "Never hide" only make it always visible.

---

### Post by Frogs Hair on 2011-09-10
Hello and Welcome 

Make sure you are logging into Ubuntu and not Ubuntu Classic . You will Know if you are in Classic Ubuntu  if  3 menus appear on the top left panel . Some graphics cards require a proprietary driver to run Unity and that can be installed from additional drivers . The first link will show how to switch between Unity and Classic . The second link is useful if you are new to 11.04 .

[http://news.softpedia.com/news/How-to-Use-Classic-GNOME-Session-on-Ubuntu-11-04-200092.shtml](http://news.softpedia.com/news/How-to-Use-Classic-GNOME-Session-on-Ubuntu-11-04-200092.shtml)

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by raja.genupula on 2011-09-10
if you still you got problems 
do ```
unity --reset
``` 

make sure that your not in ubuntu classic 


all the best

---

### Post by Afterlithe on 2011-09-11
Thanks for the help everyone, but nothing seems to work.  After a clean install, I can't even get to the log in screen.  All I see is the default background image and a flashing white box every couple of seconds.

---

### Post by Frogs Hair on 2011-09-11
You may want to try making a new Ubuntu disc burned at a slow speed and preform an MD5SUM . This would rule out the posibility a corrupted disc.[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Afterlithe on 2011-09-11
Thanks for all the help everyone.  After this install I got an error message saying I don't have the hardware to run unity.  Guess all the headache was for nothing.  I was trying to set up Unbuntu on an older computer that I had lying around; guess its not going to happen.

Another failed linux attempt for me.

---

### Post by 3rdalbum on 2011-09-11
> **Afterlithe said:**
> Another failed linux attempt for me.

Well no, not really. There's a 2D version of Unity that works without needing 3D acceleration. Go into Synaptic Package Manager and install the "unity-2d" package. Afterwards, log out and click on your username. In the popup menu at the bottom of the screen, choose "Unity 2D" as the session.

Continue logging in and you'll have Unity. It's not as flashy-looking, but it's still pretty close to the regular Unity experience.

In Ubuntu 11.10, Unity 2D will be preinstalled and will activate whenever your computer doesn't have the graphical grunt to run the regular 3D Unity.

---

