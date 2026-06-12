---
title: "Picture darkness problem?"
date: 2012-05-10
forum: General Help
---

### Post by bbno3 on 2012-05-10
I have a few pictures on my computer that i have taken with my camera. On the camera the pictures appeared to be perfect, but on my shotwell photo viewer the pictures are extremely dark?
Any ideas?
I'm using ubuntu 12.04.

---

### Post by Version Dependency on 2012-05-10
Is it just Shotwell that darkens these pictures?  Does Image Viewer or Gimp or Firefox or anything else you can view images in also show them darker than they should be?

---

### Post by eric-yorba on 2012-05-14
Are these images RAW, by any chance?   Shotwell's RAW developer is known to produce dark-ish results on many cameras.   

If this is the case, you can set the RAW developer in the preferences to "Camera."  Future imports will be set to use the camera development (RAW+JPEG or embedded JPEG) by default.  For existing images, you can set the RAW photos to Camera development manually.

---

### Post by clifford junior on 2012-05-14
what does your histogram show

---

### Post by engineer on 2012-05-26
Thanks for that hint!

In addition to the darkness problem, this also solves the issue, where black and white images suddenly show up in color in shotwell.

However, if I set the developer to camera, the orientation information isn't interpreted correctly. All photos seem to show up as landscape.

---

