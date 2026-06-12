---
title: "Graphics Problem 10.10"
date: 2011-03-31
forum: General Help
---

### Post by Samdroid on 2011-03-31
Hey guys, Ive been searching for a solution for this problem for a while and I haven't found anyone with the same problem so I thought i should ask for help here. I have a Hp Touchsmart Tx2 with AMD processor and ATi graphics. I installed Ubuntu 10.10 (64 bit) last night for the second time, the first time i had this problem so i thought maybe another download and another install would help, and i have dual boot setup with windows vista on the other partition. So the install went fine but when i am at the home screen in Ubuntu and i click something like the wireless icon at the top, or the time at the top, or any of those icons the dropdown menu is displayed at a 45 degree angle or something. Also the drop down menus in firefox will do it too, i'm sure others will as well. It is really wierd and i already installed the flxgr Ati driver (i think thats what its called) via the additional drivers application. Also when i open the terminal it is displayed at this same angle. The outline is perfect put the content inside is skewed. Also I should mention overall its just slow and laggy and the wifi cuts in and out. I took some pictures with my camera cause when i took a screen shot the menu for that was slanted and i couldn't see what the options were. It is hard for me to explain so here are the pictures please help. Thanks in advance.

---

### Post by ivanovnegro on 2011-03-31
Are you sure you installed 10.10 or is that the netbook version of Ubuntu?
It could be also 11.04 with Unity what I see on your screenshots.

---

### Post by realzippy on 2011-03-31
Did this also happen before installing the ATI graphics driver?

---

### Post by cubeist on 2011-03-31
Unity/Compiz with ati restricted drivers are not fully compatible right now.

So, you could disable unity, continue using restricted ati, or use open source ati drivers and keep unity. Or, if your ambitious, there is a PPA for daily unity builds that should work.

---

### Post by Samdroid on 2011-03-31
I am using 10.10 netbook remix to the best of my knowledge. I downloaded it for ubuntu.com and the file says 10.10 so Im pretty sure it is 10.10. Before installing the ati driver i had some weird yellow lines on the screen, but this didn't happen. So you think i should disable unity? Thanks for your quick responses

---

### Post by ivanovnegro on 2011-03-31
> **Samdroid said:**
> I am using 10.10 netbook remix to the best of my knowledge. I downloaded it for ubuntu.com and the file says 10.10 so Im pretty sure it is 10.10. Before installing the ati driver i had some weird yellow lines on the screen, but this didn't happen. So you think i should disable unity? Thanks for your quick responses

Ok, when it says its 10.10 netbook, it is indeed what you say.
Now, you just heard about some problems regarding the ATI card, maybe you should test Gnome classic, I mean not the netbook interface to see it you have better results.
Log out and log in again but choose at the login window, desktop session, not netbook.

---

