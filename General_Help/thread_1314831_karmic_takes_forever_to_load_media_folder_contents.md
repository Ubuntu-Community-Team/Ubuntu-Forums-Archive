---
title: "karmic takes forever to load media folder contents"
date: 2009-11-04
forum: General Help
---

### Post by Lacho on 2009-11-04
I just upgraded to karmic and now the folders where I store media files such as movies or comics take forever to load. As soon as i change the Display Prefs to Never, the process ends and displays all the contents. problem is that last week with jaunty I had no such problem, this is all Karmic.

What can I do?

---

### Post by zeus.jay on 2009-11-18
Hey Yeah I seem to have the same problem, when viewing folders on an external drive once opened the folder contents will not display and you get the circular processing icon.

Where did you change the display prefs (exact setting) to help resolve this issue?

Driving me nuts... 

I've confirmed file permissions and ownership. Terminal can read the folder contents perfectly.

---

### Post by jeffltw on 2009-11-26
I think the setting he's referring to is the "Show Thumbnails" setting under the Preview tab.

---

### Post by OhSoFurious on 2009-11-29
I just installed Ubuntu last night for the first time, and have been finding this problem very frustrating. I came across this thread in a Google search. Although disabling the Thumbnails is not ideal, it is a good speed increase until this issue is fully resolved.

---

### Post by Snyper64 on 2009-11-29
Having the same problem here, and this happening to both my external and my internal hard drive. I have also noticed that sometimes thumbnails will not show for video files if the folder that they are saving to at the time is open while saving them and the only thing I will get is the little film icon. Also reloading the folder does not cause nautilus to recheck check the files for a video clip.

I just tried something in the middle of writing this but try deleting your .thumbnails folder in your home directory and see if it fixes your loading problem(at-least temporarily) like it did with me. Something got seriously screwed up with how nautilus loads, renders, and uses thumbnails.

---

