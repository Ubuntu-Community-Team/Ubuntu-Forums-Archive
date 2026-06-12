---
title: "F-Spot import problem"
date: 2010-11-21
forum: General Help
---

### Post by jl.junked on 2010-11-21
I've used F-Spot to import a set of pics, it creates the folders I expect, but not all the pics are there.

When I open F-Spot the pics are there, I can copy the  location, but it's not really there.

For example, here's the path of one picture
/home/john/Pictures/Photos/2010/11/12/IMG_0431.JPG

from the cmd line I can run
ls /home/john/Pictures/Photos/2010/11/12/

but the dir is empty

any ideas?

---

### Post by nickleboyblue on 2010-11-22
Are you able to find the picture graphically through your file manager?

When importing, it's not always going to work perfectly if you import pictures from, say, an SD card, directly into F-Spot.  What I ended up with once was a bunch of thumbnails that F-Spot generated and links to picture files that didn't exist.  To avoid this, if you are putting pictures on your computer from some external media, manually copy them into your computer.  Then you can import them with F-Spot and check if they are in the right place.

Can you open the picture in question from within F-Spot?  Does it show you anything more than the thumbnail?  Are you able to find the photo graphically?  Just to make sure you don't enter things wrong, you might try cd'ing to the right file and once there, running ls.  Again, I strongly recommend that you manually copy your pictures to your computer instead of relying purely on F-Spot import.

---

### Post by jl.junked on 2010-11-22
Thanks for the reply nickleboyblue.

No, I cannot find the picture graphically through the file manager, the folder has been created, but it is empty.

I was trying to get them from an SD card, but because they images never seemed to be there I copied them all to another folder, then I've tried several times to import from that folder.

I'm not at the computer right now so I cant see if fspot is holding more then just a thumbnail, but I'll check that out later.

I have also cd'ed to the dir and ls'ed there, still empty.

Thanks for your help

---

