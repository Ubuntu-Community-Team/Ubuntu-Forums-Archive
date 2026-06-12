---
title: "changing default destination for setting images as desktop backgrounds"
date: 2010-04-17
forum: General Help
---

### Post by autonomy on 2010-04-17
Hello, when I set images as desktop backgrounds, Firefox or Nautilus saves them in my home folder. Does anyone know how to change this to ~/pictures/backgrounds?

---

### Post by zvacet on 2010-04-17
Let say you have picture named image.png .In terminal

```
sudo cp image.png ~/pictures/backgrounds
```

This command will copy picture,so if you copied it to the desired folder you can delete it.

---

### Post by autonomy on 2010-04-17
Thanks, but that doesn't work. If I remove the picture in my home folder, my desktop background disappears. That's the point - to remove random files from my home folder, not to have the image in my pictures directory. I'm just wondering and admit this isn't crucial. I'd like to set Firefox or Nautilus so that the pictures are saved into my backgrounds folder by default. In case this is a Firefox issue, I've asked there as well b/c the pictures are saved as Firefox_wallpaper.png, so it looks like it might be a Mozilla issue.

---

### Post by Maciejl06 on 2010-04-17
when you go to Google; to find a wallpaper, you can right click on the image, save as, and choose where you wish to save it.

Another option, you can go to edit->preferences->main tab and change the "save files to:" directory, though this will save all downloaded content to that directory. I don't think Firefox would support downloading pictures exclusively into a different directory aside from everything else.

---

### Post by autonomy on 2010-04-17
Thanks, but that really doesn't have anything to do with the "Set as Desktop Background" option on the context menu, and this doesn't have anything to do with where I save my downloads b/c they go to the Desktop; and I don't want all of them to go to my pictures/backdrops folder. I'm just trying to make this menu option work better for me.

---

### Post by Maciejl06 on 2010-04-17
oh sorry, i misunderstood the question. 
At the time, i do not think you have that option, but you are not the only person to have thought of this: [http://brainstorm.ubuntu.com/idea/4047/](http://brainstorm.ubuntu.com/idea/4047/)

---

