---
title: "Corrupt image file just nuked my whole folder"
date: 2011-12-28
forum: General Help
---

### Post by cabdolla on 2011-12-28
Help! Ubuntu newbie here. I was messing with a jpg in ink scape. I saved it as over ride and hit OK. Then Ubuntu messed up and the file got hosed. Now I cant open the folder the file was in because Ubuntu hangs and turns gray. I cannot access anything within the folder and I need those images :(

---

### Post by lisati on 2011-12-28
**Before** you do anything else, *stop and have a break*. That way, the chances of overwriting anything else important will be reduced.

Are you able to boot from a Live CD?

---

### Post by cabdolla on 2011-12-28
I might have the live CD laying around somewhere, but it is not clear to me why I would use it. Can I delete the file using the "DOS" equivalent command? If I can nuke that one image file, then the folder should work fine for the rest of the files. Or are you suggesting there is a way to repair the damaged image file?

---

### Post by hansdown on 2011-12-28
Welcome to the forum,cabdolla.

lisati speaks wise words.

If you "truly" wish to save these particular files, (they "may" be corrupted, or "DRM").

Use a "live" disk, and open a terminal.

Enter

```
gksudo nautilus
```

You should be able to drag and drop the file, or folder, to, desktop, or your preferred location.

---

### Post by cabdolla on 2011-12-28
If I just want to nuke the file, how do I go about doing that?

---

### Post by hansdown on 2011-12-28
> **cabdolla said:**
> If I just want to nuke the file, how do I go about doing that?

Right click the file> move to trash.

Remember, to empty your trash.

---

### Post by cabdolla on 2011-12-28
not possible. I cant even open the folder because Ubuntu goes gray on me due to that one jpg file. I have to delete it, some how, via the terminal.

---

### Post by hansdown on 2011-12-28
> **cabdolla said:**
> not possible. I cant even open the folder because Ubuntu goes gray on me due to that one jpg file. I have to delete it, some how, via the terminal.

Your graphics capabilities are not enough, for this project.

Are you able to get to the file in inkscape, and delete it?

---

### Post by cabdolla on 2011-12-28
Nope, cant do that either. When I click on the image to save it, it goes gray again and hangs.

---

### Post by hansdown on 2011-12-28
> **cabdolla said:**
> Nope, cant do that either. When I click on the image to save it, it goes gray again and hangs.

lisati's advice holds true.

Check post #4, for more info.

---

### Post by cabdolla on 2011-12-28
Well, here is what I did. I looked into how the terminal works. I was able to rename the corrupt file from the terminal. Then and only then was I able to now go back into the folder and recover the other files. Ink Scape totally $&&$& that file, it's lost forever. All I see are the circles I drew in Ink Scape. The image that was behind it is now lost. :(

---

### Post by hansdown on 2011-12-28
Glad you fixed it,cabdolla?

---

