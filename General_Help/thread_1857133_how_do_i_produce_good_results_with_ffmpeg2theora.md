---
title: "how do i produce good results with ffmpeg2theora?"
date: 2011-10-09
forum: General Help
---

### Post by voldar on 2011-10-09
i want to convert high resolution .wmv files to .ogv without noticeable loss i tried "ffmpeg2theora -v10 -a3 sample.avi" but the out put file was 30% larger then the original. so i thought maybe adding a soft target would work "ffmpeg2theora -V 3000k --soft-target -v 9 -a 3 sample.avi". But that made the file 110% larger then the original. Does anyone know of some good options to pass that will keep quality but not produce a much larger file?

---

