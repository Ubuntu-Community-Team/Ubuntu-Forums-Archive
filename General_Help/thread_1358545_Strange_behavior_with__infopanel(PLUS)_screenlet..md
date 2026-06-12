---
title: "Strange behavior with  infopanel(PLUS) screenlet."
date: 2009-12-18
forum: General Help
---

### Post by nikolais on 2009-12-18
About two days ago I downloaded and ran a portable game, meaning, out of the folder, doesn't need to be installed. Well, when it started up...the video went all strange, and I could see my desktop through the game and such. Upon closing the game, most everything went back to normal, except two of my screenlets. Impulse, which fixed with a reinstall, and infopanel(PLUS). The infopanel will NOT back to normal now, I've reinstalled several times. What it does, is flashes back and forth halfway between my infopanel, and the default. It's like the two are stuck together, and when I right click on it, two menus come up as one big one, but trying to close one only, makes it act like one screenlet and it all closes...leading me to believe that somehow they got morphed together or something. I love this screenlet, so please help! :P


[IMG]http://i50.tinypic.com/atqetf.jpg[/IMG]


those screenshots show the two panels that it keeps switching between every few seconds. each one has a few of the properties I set on mine, and the rest are default. I don't get it.

I'm running a dell inspiron 1545 with ubuntu 9.10 - 64bit.

---

### Post by Darent on 2011-01-14
Go to:

/home/darent/.config/Screenlets/InfoPanel/default

where you have the .ini for the infopanel. If there are two files, delete the newest and log out. When you log on again you should have only one infopanel.

---

