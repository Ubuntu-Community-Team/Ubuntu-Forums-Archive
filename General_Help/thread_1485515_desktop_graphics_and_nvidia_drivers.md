---
title: "desktop graphics and nvidia drivers"
date: 2010-05-16
forum: General Help
---

### Post by unplugged23 on 2010-05-16
Hi all,

When re booting my system today, before the gnome log in screen appeared, I received a small window notifying me that ubuntu was going to boot into safe graphics mode. I thought this was strange, but ignored it and booted up. I've had desktop effects set to normal, and soon realized that they had been disabled. I went to double check that the nvidia driver was activated, 'system > administration >  hardware drivers' and it said that my nvidia driver was running. However when I go to 'system > administration > nvidia x server settings' a window loads telling me that I am not using the nvidia driver and that I need to 'sudo nvidia-xconfig'. So I popped open a terminal and ran the command, which returned a normal output with no errors informing me that the new x file and been saved in the proper x directory. After this I re enabled the ctrl-alt-backspace keybinding, and restarted x. I am still un able to use the desktop graphics, the nvidia x server settings program still says that the driver is in active, and the hardware drivers program still says that the driver is active.

Any thoughts as to what this is? Could this be a kernel problem? (I've been a little worried about those since 10.04)

Thanks for any responses!

---

### Post by Oasu4g on 2010-05-16
Reboot your computer into normal graphics mode? I don't know how you would do that though.

---

### Post by unplugged23 on 2010-05-16
Let me reboot so I can get all of my options. They include something along the lines of 'boot into safe graphics mode','terminal','restart x'. Let me check again so I can be more precise.

---

### Post by cbbnewbie on 2010-05-16
please post the output of

lspci

---

### Post by unplugged23 on 2010-05-17
As much as I would love to post the output of 'lspci' I am now locked out of my system. When I powered down to get a more specific description of the menu, I got sidetracked and left my computer for about half an hour. I came back and booted up, and got a description of the menu's, but I cannot log in to ubuntu. My password will not work and always results in 'authentication failure'

Does anyone have any ideas about this? It dosent even seem related to the graphics issue.

Sorry if I sound a little upset, but I'm getting tired of trouble shooting my ubuntu installation every time I come home :P Hopefully I'll feel better after a cup of coffee, and we can get this resolved :D

---

### Post by Oasu4g on 2010-05-17
Did you get any other errors besides "authentication failure"?

Try booting into the "Terminal" option and see if you can log in that way.

---

### Post by unplugged23 on 2010-05-17
Well I went through the 'ubuntu is running in low graphics mode' thing again. But other that that, no. I don't think the two are realted, but I'll be happy to give you a more detailed description of the 'low graphics' window if you wanted.

---

### Post by unplugged23 on 2010-05-17
Sorry, I must have missed the last part of your post. It dosen't matter if I'm on the terminal screen, or the gnome log in screen. It will not accept the password.

---

### Post by Oasu4g on 2010-05-17
Then it sounds to me that you're literally locked out of your system. Unless someone here has a better suggestion, I think you'll need to do a clean install. Use the LiveCD to save/backup any of your data, and reinstall Ubuntu.

---

### Post by unplugged23 on 2010-05-17
Thanks for your time :)

I've been using arch linux since ubuntu intreped ibex, I came back to try the big 10.04 release, but it seems buggy to me. Strange considering ubuntu has one of those 'it just works' reputations.

Hopefully within the next 6 months or so we'll get a new release in which all of these bugs are fixed, untill then, I'm back to arch.

The one thing that I always miss about ubuntu that no other distibution can offer, is the community! You guys are the best!

See you with the next release :)

---

### Post by Oasu4g on 2010-05-17
Hahahah. But that's what the Karmic users said back in '09! :p

Sorry I couldn't help you more unplugged23. Hopefully with the next release you won't have any trouble at all.

Regards,

Tim

---

