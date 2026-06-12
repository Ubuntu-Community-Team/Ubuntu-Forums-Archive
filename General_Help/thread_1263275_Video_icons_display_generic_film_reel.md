---
title: "Video icons display generic film reel"
date: 2009-09-10
forum: General Help
---

### Post by Lacho on 2009-09-10
Hi,

I just wiped Windows XP from my PC after trying it out with WUBI for a while, back then all my movie/video icons displayed an image from a seemingly random scene.

Now, after a full Jaunty installation, all my movies display a generic film reel icon, even those residing in USB external drives that display correctly on my Jaunty installed Laptop. You can see in the attached image how it is displayed.

What can I do to correct this situation?

---

### Post by 4Orbs on 2009-09-10
In your personal home folder is a hidden folder .thumbnails and inside that are a normal folder and failed folder. Delete all the images in both those folders. Then log out and log back in and when you open Nautilus where the movies are located, the thumbnails will be rebuilt with the scene outtake images rather than the generic reel icon.

---

### Post by Lacho on 2009-09-12
Tried it, but that did not solve the problem.

---

### Post by dumblebee100 on 2009-09-12
> **Lacho said:**
> Hi,

I just wiped Windows XP from my PC after trying it out with WUBI for a while, back then all my movie/video icons displayed an image from a seemingly random scene.

Now, after a full Jaunty installation, all my movies display a generic film reel icon, even those residing in USB external drives that display correctly on my Jaunty installed Laptop. You can see in the attached image how it is displayed.

What can I do to correct this situation?

you need to enable previews buddy ...
if you enable previews then a specific frame in the movie or the thumbnail of an image will store in the ~/.thumbnails

there are two folders namely NORMAL and FAIL or (FAILSAFE ) 

I dont know much about fail but I do know about normal folder 

when you enable previews the frames of movies or thumbnails are stored into this folder with specific code to map the file ..


so enable previews and give it a try

---

### Post by Lacho on 2009-09-12
dumblebee100,

I did, and do have the Preview option enabled, as shown in the image, so that's not the problem.

I also tried deleting the files in the .thumbnails folder, and the Normal Folder did have a lot of images that somehow do not get paired to the corresponding icon.

---

