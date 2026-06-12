---
title: "Trouble with a console based pdf viewer"
date: 2009-07-19
forum: General Help
---

### Post by shredder12 on 2009-07-19
I was recently looking for a console based pdf viewer and found on fbgs which used fbi a frame buffer image viewer to do the job.

and when i used this command to view a pdf ```

fbgs name.pdf 
```

I got the following error
```
### rendering pages, please wait ... ###

GPL Ghostscript 8.64 (2009-02-03)
Copyright (C) 2009 Artifex Software, Inc.  All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
Processing pages 1 through 6.
Page 1
Substituting font Courier-Bold for CourierNewPS-BoldMT.
Loading NimbusMonL-Bold font from /var/lib/defoma/gs.d/dirs/fonts/n022004l.pfb... 2901220 1227351 9422088 8128592 3 done.
Substituting font Courier for CourierNewPSMT.
Loading NimbusMonL-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n022003l.pfb... 2937980 1395333 9458848 8164077 3 done.
Page 2
Substituting font Courier for CourierNewPSMT.
Page 3
Substituting font Courier for CourierNewPSMT.
Page 4
Substituting font Courier for CourierNewPSMT.
Page 5
Substituting font Courier for CourierNewPSMT.
Substituting font Courier-Bold for CourierNewPS-BoldMT.
Page 6
Substituting font Courier for CourierNewPSMT.
using "DejaVu Sans Mono-16", pixelsize=16.67 file=/usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
Open /dev/fd0: No such file or directory

```

The man page of fbi shows that fbi needs to have rw permission to /dev/fbN directories.. 
but the above msg shows that I don't have any such directory or file..
so, what am I supposed to do now..
some help please...

---

### Post by shredder12 on 2009-07-20
well i think may be creating a device /dev/fb0 will do the job...(hopefully)
I have tried MAKEDEV but i m getting some error while creating such a device..

so, any suggestions on how to create a frame buffer device with rw permissions so that it could be used by "fbi"..

---

