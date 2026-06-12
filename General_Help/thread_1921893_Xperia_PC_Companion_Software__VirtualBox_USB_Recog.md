---
title: "Xperia PC Companion Software / VirtualBox USB Recognition"
date: 2012-02-07
forum: General Help
---

### Post by Stu15 on 2012-02-07
(Please note im still having trouble updating my phone, due to the boot method during preparing)

This may not seem like a big deal, but ive literally spent days trying to find a working way to update my phone in Linux.

Trying to get my phone recognised, or what was the best way. I was hoping to find a way of installing Sony's PC Companion via Wine, but it has issues with running and Drivers dont really work with wine.

Anyway, So i have gotten USB to work with Virtual Box, following the simplest guide, after a few basic steps it finally worked.

Its simple but there arent really any answers on forums and the web telling of the working method so hopefully this will easily guide the half a dozen or more people to setting this up on their machine.

Ok, So;

1) Install Virtual Box - [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

2) Setup a Virtual machine, plenty of guides on this, but you create a new environment based on the OS you wish to use, i advise windows XP, as its light, still very stable, supported and easy to use. And took me 10 minutes to install. (VB works as a boot sequance, so have the ISO or CD loaded ready for when you boot up to install, you can mount the iso in settings > Drives)

3) Run windows xp in Virtual Box, once you've got it loaded, will probably take 10 minutes to install, you need to get the PC Companion software and install that, in the meantime install all your automatic updates.

4) Follow this simple guide to allow USB detection in Virtual Box, [http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

So once you've made sure youve updated XP, you should now be able to load your phone in the companion.

In virtual Box there is a filter system for USB input, and when you hold down the back key when the phone is off to prepare it (similar to device recovery mode when jailbreaking an iphone) I think because is technically not on it cant recognise the back holding for boot unless you have to add the filter for it, which you can do in the background.

So next is trying to get it to recovery boot for the upgrade, I'll have a play around and see if i can get it working. I may try the usb 2 feature that you need the expansion for, however it wouldnt load the virtual machine with this enabled...

Any suggestions would be helpful, as i am a noob :)

---

### Post by Cookieh on 2012-02-07
Does Ubuntu 12.04 support UNIX/Linux based mobile devices such as android Xperia Mini Pro, because mine can not install PC Companion....

---

### Post by Stu15 on 2012-02-07
Probably not, the software is Windows and Mac only, hence why you have to use a Windows OS running in virtual box, however the phone is 3 weeks old old im using, so im having trouble updating it, i dont know if its the fact im running virtual box, or if its sonys method of preparing it, turning it off and holding a button, apparently people have loads of trouble trying to do it... lots of people annoyed at sony for making it so hard. but the software is working on Virtual Machine version of WindowsXP... so i guess its a start...

---

### Post by Stu15 on 2012-02-07
So its working now, basically... after retrying it over and over.. managed to get it to work, i didnt even do anything different, intact i didnt even hold back key and reconnect... very strange, i think the sony method is clearly flawed. but this is definitely doable :)

---

