---
title: "customise the desktops in different ways..."
date: 2010-02-06
forum: General Help
---

### Post by bulls_eye on 2010-02-06
hi all...

i just want to know weather it is possible by some means to set different preferences for the two desktops that are available in ubuntu??

for eg: different backgrounds, shortcuts etc...

---

### Post by hawthornso23 on 2010-02-06
> **bulls_eye said:**
> hi all...

i just want to know weather it is possible by some means to set different preferences for the two desktops that are available in ubuntu??

for eg: different backgrounds, shortcuts etc...

The short answer is no. Not without a fair mount of hacking anyway. The long answer is ...

**_Changing the background_**
Different wallpapers can be set in compiz, however nautilus will overwrite them with its own wallpaper when it draws the desktop so you won't see them. There is a setting to stop nautilus from doing this - but unfortunately it turns off the desktop altogether. Nautilus will then stop treating the desktop as a folder - you won't see icons and you won't be able to drag and drop to it etc. For me the loss of functionality was not worth the minor cosmetic improvement.

_**Different shortcuts etc**_
What you need for this to work is multiple desktop folders. Nautilus won't do this. However I did see a scripted hack once that involved detecting when the desktop changed, switching links to link the Desktop to a different folder, and then forcing nautilus to redraw the desktop to make it show up. The guy who wrote it claimed it even worked! But we are talking a serious hack here. Not recommended unless you can read the code and debug the thing when it crashes.

---

### Post by bulls_eye on 2010-02-06
wow...

thanks for the post...

i like to play only with the programs not with their codes...

:)

---

