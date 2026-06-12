---
title: "Lost volume control"
date: 2010-10-12
forum: General Help
---

### Post by ThePhysician on 2010-10-12
Someone on the forums had me uninstall pulseaudio to get pSX working, and now I don't have a volume control icon on the panel and when choosing to add stuff to the panel it isn't available.

I re-installed pulseaudio through the package manager, but I have a feeling it didn't install everything that uninstalled with it.

Please help?

---

### Post by Rasa1111 on 2010-10-12
There is no 'Indicator Applet"?
when you right click panel and choose "add to panel"?

 Indicator Applet is the volume control.

---

### Post by ThePhysician on 2010-10-12
> **Rasa1111 said:**
> There is no 'Indicator Applet"?
when you right click panel and choose "add to panel"?

 Indicator Applet is the volume control.

Indicator Applet puts mail and bluetooth back up there so I have 2 of each. So yeah, my volume control is missing from the indicator applet ever since someone told me to uninstall pulseaudio* which has now been reinstalled. 

I just don't know what else it uninstalled when they had me do uninstall pulseaudio* that didn't reinstall with pulseaudio from the package manager. :(

---

### Post by Rasa1111 on 2010-10-12
Dang, Im sorry. :(

 Maybe shoot a quick private message to the one who suggested you remove it?

---

### Post by ThePhysician on 2010-10-12
I did. No luck.

Hopefully somebody knows what all I need to reinstall to fix things back to how they were. Don't want to have to reinstall 10.10 just because of this little thing.

---

### Post by Rasa1111 on 2010-10-12
yeah no doubt. 

 Seems like it should be easy enough to fix with the proper guidance. 

 So,  simply re-installing pulseaudio didnt remedy the issue eh? 

 I really can't think of what else one would need to do. :?:

 Sorry I couldnt help, 
But if I dont see anymore infos in this thread by morning time, Ill come back and give it another bump. 

good luck mate.

---

### Post by ThePhysician on 2010-10-12
Thanks. Yeah, reinstalling it gives me audio, although really very faint audio, and no volume control.

---

### Post by Quackers on 2010-10-12
Might it be the "indicator applet session"?

---

### Post by drhabber on 2010-10-13
Try to remove the indicator applet from the panel, then add it again.

---

### Post by CompyTheInsane on 2010-10-13
Do you have indicator-sound installed? If not, you should install it as it holds the volume control indicator for Pulseaudio.

---

### Post by ThePhysician on 2010-10-13
> **compugeek32 said:**
> Do you have indicator-sound installed? If not, you should install it as it holds the volume control indicator for Pulseaudio.

Thank you. That fixed it.

---

