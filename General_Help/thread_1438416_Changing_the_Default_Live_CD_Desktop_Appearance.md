---
title: "Changing the Default Live CD Desktop Appearance?"
date: 2010-03-25
forum: General Help
---

### Post by Mirages on 2010-03-25
So recently I have been trying to create the perfect custom ubuntu .iso to write to a usb drive so i could carry around a live cd version of my current desktop operating system. I have 2 problems...

1

 using various tools like Remastersys, Ubuntu Customization Kit, and Ubuntu's own LiveCDCustomization tutorial I have managed to install most of the packages that I want.... Truecrypt is not in the repos and i would very much like it on my custom live cd. while in chroot i tried using wget to download it then extract and install it, but i got a 404 error so it did not seem to be connecting to the place to download it. is there a workaround to getting truecrypt to install into my extracted squashfs? would it be possible to download the packages to my desktop then copy them over to my chroot squashfs to be installed?

2

I have not been able to customize the default appearance of the desktop environment like the background, icons, colors, window border, panels, applets, and so on.... Ubuntu's tutorial states that I need to edit .xmls in /etc/gconf  but i do not understand how to edit those to get what I want. I have searched google for answers on how to do this but I havent found any threads or tutorials explaining how to do it.

LiveCD creates a new user with default settings everytime it is started so its a matter of editing the files that control the settings of a new user.

------------

I rather new to linux so detailed instructions would be nice!

thanks

---

### Post by aysiu on 2010-03-25
In Remastersys, you need to customize your user and copy the appropriate configuration files to /etc/skel

More details here:
[http://psychocats.net/ubuntu/remastersys](http://psychocats.net/ubuntu/remastersys)

---

### Post by Mirages on 2010-03-25
oh ok thats a good solution to both my problems! I overlooked the fact that remastersys makes an image of my current OS so that means I can have truecrypt!

things were easier than i thought

thank you for the prompt response

---

