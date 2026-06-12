---
title: "3d drivers in wine"
date: 2011-08-24
forum: General Help
---

### Post by Mahkoe on 2011-08-24
Since I have no idea what it is I'm looking for, rendering me unable to do a google search, I am forced to ask the good people at these forums.

So I install a game through steam. Everything works fine, everyone is happy, until I start the program. So, to troubleshoot, I run steam through wine through the terminal. Just steam on its own generates quite a few fixmes and errs and stubs, but the game just won't start. From what I can make out from the cryptic error messages from wine, either it doesn't like or doesn't recognize the 3d drivers I'm fairly sure I have, or it's related to directx. Does anyone know if ubuntu 10.10 32 bit has 3d drivers, or maybe any way to get 3d in wine? Pretty much anything would help. Thanks

Additional information:
I have Intel HD graphics, and I have a core i3-370m processor

---

### Post by seawolf167 on 2011-08-24
What is the name and version of the game you are trying to run? You may want to check out [WineHQ ]("http://www.winehq.org/")to see if there are any notes/fixes/information on that particular game.

---

### Post by Mark Phelps on 2011-08-24
A common misconception is that some folks think that Wine uses Windows drivers; it does not.  Wine uses Linux drivers, so if you don't have good video drivers already, there's nothing you can do in Wine to change that.

Some folks may tell you to go to Additional Drivers -- but that generally only includes either Network drivers, or ATI/Nvidia video drivers.  That does not include Intel drivers.

---

### Post by Mahkoe on 2011-08-24
Thanks for the replies. I checked out the game at wineHQ and it was rated as garbage, and now I know that there are no windows drivers, which means that if it doesn't work, don't bother. So, thanks.

---

