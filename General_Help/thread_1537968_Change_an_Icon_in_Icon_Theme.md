---
title: "Change an Icon in Icon Theme"
date: 2010-07-24
forum: General Help
---

### Post by therealKerb on 2010-07-24
Hello,

I have d/l and am using an icon theme I got from gnome-look.  I like all the icons except for a few, specifically the trash, and would like to change them but I can't figure out how.

I d/l an empty and full trash icon.  I looked in the /home/*username*/.icons/*themename* folder and found the two trash icons that came with the theme (they were in ~/.icons/*themename*/scalable/places).  Changed the names of the ones I d/l and replaced those current ones with them.

No dice.  Anyone know how to do this?  I would also like to change the Menu Bar icon back to the gnome foot.

Any advice will be much appreciated.  Thanks in advance.

---

### Post by fragos on 2010-07-24
Look in /usr/share/icons for a folder with the name of you icon theme. In there you'll see more folders with names like devices, mimes and actions. ev ery icon theme folder will have folders with these same names. Inside them are folders labels by size. Open one of these and you'll see the icons. The icon names are consistent between sizes. Here is where you change the icons you want while keeping the file names the same. There may be multiple icons for the same subject which differ based on the state. you may also find an icon listed twice where the only difference is a "-" or an "_" connecting the words in the icon name. I think you can go on from here on your own. You may need to change an icon in all the size folder for that category.

---

