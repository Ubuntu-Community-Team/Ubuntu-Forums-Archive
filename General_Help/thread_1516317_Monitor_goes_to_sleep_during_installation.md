---
title: "Monitor goes to sleep during installation"
date: 2010-06-23
forum: General Help
---

### Post by ty10r on 2010-06-23
[FONT=Arial]I am trying to install Ubuntu 10.04 on my PC using NVIDIA GeForce 9150LE graphics and HP w2207h monitor. After using the Wubi installer and rebooting my computer, i select the ubuntu boot menu option and it says it is preparing to continue with the installation. after a countdown before it begins, my monitor goes to sleep. i used an eMachine monitor that i used in a previous installation of 9.10 that worked fine and reached the exact same problem. When booting from a live CD and selecting try without installing the screen comes up with a blinking underscore, and both monitors went to sleep. I believe its a problem with the graphics chip, but i dont know how to fix it. Any help would be greatly appreciated.[/FONT]

---

### Post by bcbc on 2010-06-23
From the [wubiguide]("https://wiki.ubuntu.com/WubiGuide#Other boot or video problems"), you can hit ESC when you see that first countdown and then you will 'see a menu with more boot options'. 

I haven't done this myself and the guide doesn't say, so not sure what it offers. But if there is something where you can add 'nomodeset' to the boot options, or choose 'safe graphics', that might get you in at least, and then you can look for a driver for your graphics card.

It seems like nvidia drivers are a bit of a pain in 10.04. Here's a link [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) that might shed more info.

---

### Post by ty10r on 2010-06-23
i believe there is a nomodeset option when booting from the live CD. I'll try it and see if it works.

---

### Post by ty10r on 2010-06-24
used nomodeset when booting from live CD, installed correctly. Could not install drivers while using live CD due to missing drivers for my wireless card. Will copy setup files for driver to a usb and try it again. there is not a nomodeset option using wubi installation process, so i have abandoned it. the safe graphics option didn't work either.

---

### Post by bcbc on 2010-06-24
I'll play around with the wubi install when I have a moment and see what can be done.
However, if you are able to do a proper install (direct to partition) this is definitely better for long term use. So go that route.

For one of my computers that needed ndiswrapper to get the wireless working, I downloaded the drivers on windows, and then mounted the windows partition to get them from ubuntu. USB works too.

---

### Post by bcbc on 2010-06-24
I did a wubi install. You're right there's no nomodeset option. If you hit 'e' on the normal option, you could probably insert "nomodeset" right after where it says "quiet splash". 

But it's not a very user friendly workaround.

---

### Post by ty10r on 2010-06-24
ok. i will try that. the drivers that Ubuntu showed me were for broadcomm, and it couldn't install it.

---

### Post by bcbc on 2010-06-24
OK don't forget to hit CTRL+X to boot once you've edited in place. Hitting ESC will lose the changes.

For your wireless, check out the Networking & Wireless subforum. They have some stickies and knowledgeable users to help out.

---

### Post by ty10r on 2010-06-24
this works great, except i always have to enter nomodeset after quiet splash every single time i boot up until i get the graphics and wireless under control.

---

### Post by bcbc on 2010-06-24
> **ty10r said:**
> this works great, except i always have to enter nomodeset after quiet splash every single time i boot up until i get the graphics and wireless under control.

You can make it permanent until you resolve your graphics...
```
sudo cp /etc/default/grub /etc/default/grub_backup
gksudo gedit /etc/default/grub
```

Add nomodeset after quiet splash as follows:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Update your grub menu to pull in the new default:
```
sudo update-grub
```

Just do the reverse to remove it.

---

### Post by ty10r on 2010-06-24
that worked perfectly. thanks very much. i still can't find a location that has my driver for a linksys wmp54g... some more searching though and i should find it. i may need help actually getting the driver on my computer after i get it though.

---

### Post by bcbc on 2010-06-25
> **ty10r said:**
> that worked perfectly. thanks very much. i still can't find a location that has my driver for a linksys wmp54g... some more searching though and i should find it. i may need help actually getting the driver on my computer after i get it though.

All the links I've found for your wireless card seem to be outdated (e.g. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G) ).

It may be less painful to go out and by a new wireless card that's supported natively.

---

### Post by ty10r on 2010-06-25
i think i may take my computer down to where there is a working ethernet port and try to plug in and download the broadcom driver there. ill get back to this within a few hours when i do.

---

### Post by ty10r on 2010-06-25
so i did what i said i would and it works perfectly. thanks soo much for all your help!

---

### Post by bcbc on 2010-06-25
> **ty10r said:**
> so i did what i said i would and it works perfectly. thanks soo much for all your help!
Cool - you're welcome.

---

### Post by kempy on 2011-04-14
Hey, thanks man! I was having the exact same problem with my HP monitor. I swear I had Ubuntu installed on the same computer with an Acer monitor and didn't have a problem.
I put nomodeset where you said to, and it finally worked! Now I should be able to download the driver I need for it.

---

