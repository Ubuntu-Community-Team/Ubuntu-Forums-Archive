---
title: "Help: wget REGEX for PBASE Picture Download"
date: 2009-10-09
forum: General Help
---

### Post by samichx on 2009-10-09
I'm looking to use Regular Expressions with wget to download some images from PBase - specifically [http://www.pbase.com/nparc](http://www.pbase.com/nparc) my local HAM radio clubs photos.

I would like a copy so that I don't have to constantly go online. But PBase lacks a "Download All" option, despite the fact that it could save bandwith (even though it could hurt it, I'm looking to NOT have to load the same hi-res image 100+ times)

The technical details:

Download any image found after (2) links from the top. 
  -- First link is into a gallery, second link into the images. 
Download ONLY JPG images.
  -- Gif/PNG files are used for logos/unnecessary images
Maintain Hierarchy 1 Gallery ~ 1 Folder
  -- This part may be optional, but preferred

wget --?? [http://www.pbase.com/nparc](http://www.pbase.com/nparc)

---

