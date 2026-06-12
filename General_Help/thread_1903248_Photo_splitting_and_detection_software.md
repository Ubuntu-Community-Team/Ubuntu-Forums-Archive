---
title: "Photo splitting and detection software"
date: 2012-01-02
forum: General Help
---

### Post by rnelson0 on 2012-01-02
I have been scanning all my old pictures so that I can have digital copies and toss out the old ones.

I have been laying about 3-4 photos on my flatbed scanner and then manually splitting the image into separate photos.

Does anyone know of any software that will automatically detect photo edges and crop/cut the photos out? This would be a huge time saver.

Let me know if you know any software that exists for Ubuntu.

Thanks

---

### Post by hwttdz on 2012-01-02
Sounds like you could do pretty well with imagemagick by first cutting the composite image into pieces and then performing a trim on each section.  This assumes that you put down the images in the approximately the same location every time.  Specifically it requires that there is omitted space which is never covered by a photo. Namely assume that your photos behave the same way as the tiles here
[http://www.imagemagick.org/Usage/crop/#crop_spaced](http://www.imagemagick.org/Usage/crop/#crop_spaced)
and the trim operator will take care of the fuzz factor for you.

They even have some notes about trimming noisy background in scanning: [http://www.imagemagick.org/Usage/crop/#trim_noisy](http://www.imagemagick.org/Usage/crop/#trim_noisy)

---

