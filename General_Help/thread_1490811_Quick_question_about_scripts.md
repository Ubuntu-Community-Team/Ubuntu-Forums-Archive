---
title: "Quick question about scripts"
date: 2010-05-22
forum: General Help
---

### Post by inameiname on 2010-05-22
Is there any way to associate two (or perhaps more) folders in this way:

imagefolder = "/usr/share/backgrounds/"
imagefolder = "~/Pictures/Backgrounds/"

...I have a random wallpaper script that runs on startup and it would be great if I can have both of these as locations for pictures. Unfortunately how I have it above doesn't work.

---

### Post by bodhi.zazen on 2010-05-22
No, probably the best you could do is write a script to create symbolic links for file in one directory to another.

---

### Post by inameiname on 2010-05-22
Aww, that's too bad. How would I go about doing what you suggested? I'm only a novice with scripts.


UPDATE:  

Right clicking and creating a link for "~/Pictures/Backgrounds/" folder and putting that into "/usr/share/backgrounds/" doesn't work, as it only looks at it and doesnt' seem to look at subdirectories. Thus, the only way that seems to work is to create a link for every picture in the "~/Pictures/Backgrounds/" folder, which is alright, but it'd get old having to do that for every picture I may add later on.

UPDATE2:

I'm gonna reverse the above, and create links for all pictures in "/usr/share/backgrounds/" into "~/Pictures/Backgrounds/", since it's "~/Pictures/Backgrounds/" where I'll be adding and removing backgrounds a lot more than the other one, and there are only a dozen or so in "/usr/share/backgrounds/" anyway. Good enough.

---

### Post by bodhi.zazen on 2010-05-22
> **inameiname said:**
> Aww, that's too bad. How would I go about doing what you suggested? I'm only a novice with scripts.


UPDATE:  

Right clicking and creating a link for "~/Pictures/Backgrounds/" folder and putting that into "/usr/share/backgrounds/" doesn't work, as it only looks at it and doesnt' seem to look at subdirectories. Thus, the only way that seems to work is to create a link for every picture in the "~/Pictures/Backgrounds/" folder, which is alright, but it'd get old having to do that for every picture I may add later on.

Which is why you would script it ...

Is it not easier to keep the pictures in one place ?

---

### Post by inameiname on 2010-05-22
It is but I put my custom DVD on more than one computer, for friends and family and such, and I would prefer using a folder in the Pictures directory as the main one so whomever uses it can just throw pictures inside it and voila, instant revolving wallpaper. However as it's sort of a default custom DVD at first, I like keeping it's size small, so I wouldn't keep any extra pictures in there, which is why the link to the "/usr/share/backgrounds/" folder, so there'd be some already there. 

Anyway, I'm just gonna do what I decided in my Update2.

Thank you for your help. I never thought about the links so I'm greatful. :)

---

