---
title: "Newly-installed Google Chrome missing after reboot"
date: 2010-07-21
forum: General Help
---

### Post by snuffsez on 2010-07-21
Greetings everyone. I am a newly converted Ubuntu user and for weeks I have tried several Linux distros and I settled for this one. It has been a combination of fascination and struggle, but I really like what I have for now.

Anyways, here is my problem. I was thrilled to know that there is a Google Chrome for Linux, so I installed that right away. Chrome is my browser of choice when I was still using Windows.

The browser worked flawlessly after installation, so I thought everything was good to go. Unfortunately when I restarted my netbook, It was no longer in the Applications > Internet menu (it was there previously.) I did search "Chrome" using the "Search Files" option. I found several "chrome" files but I have no idea if any of those can launch it, since there was no chrome icon. How do I go about this?

Any help would be appreciated :)

---

### Post by snuffsez on 2010-07-22
okay, so it went back after I left my netbook switched off overnight. I hope there's anyone here who might have an idea on why programs sometimes vanish on the menu.

---

### Post by djhvt on 2010-07-22
It may just be that because it is not installed via the Ubuntu software center that shortcuts were not put where they should have been. 

To test to make sure its installed correctly (and to access the program) go into the accessories menu and open the Terminal. When it comes up type in google-chrome and hit enter.

a browser window should open. If this is the case you are simply missing the menu shortcut and you need to manually build it. If that is the case it would be helpful to know if you are using the regular version of Ubuntu or the netbook edition.

---

### Post by snuffsez on 2010-07-23
It vanished only once and thankfully, it's there ever since. I'm using the regular edition because the Netbook edition's graphics doesn't work on my Astone UMPC. Yep, I installed that from a .deb file downloaded from the Chrome site (i'm having problems with the repository, which I believe is worthy of another thread). I can also launch it from the terminal, so I believe everything is a-ok now, thanks.

I'll tag this as solved after 24 hours. :)

---

### Post by buknoii on 2010-10-17
I also encountered this type of problem. What I did are the following

- Go to TERMINAL
- Check if Chrome is really installed by typing google-chrome
- Edit MENUS and under INTERNET I added NEW ITEM. 
- A new window will open and in the command textbox type _google-chome_

I hope this helps :)

---

