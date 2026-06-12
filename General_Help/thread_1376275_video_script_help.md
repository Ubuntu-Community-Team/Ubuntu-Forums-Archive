---
title: "video script help"
date: 2010-01-09
forum: General Help
---

### Post by rfrayer on 2010-01-09
was wondering if anyone could help me out im trying to make a video script that will convert a whole directory and do 2pass using mencoder here is the script

```
#!/bin/bash
#
# Convert files for psp

for i in '*'; do

  mencoder \
\
\
$i \
\
-oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vpass=1:vbitrate=384:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 15 -o /dev/null \
&& \
mencoder \
\
\
$i \
\
\
-oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vpass=2:vbitrate=384:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 15 -o \
\
\
"$i.mp4" \
&& rm divx2pass.log

done
```

write after it gets done with the first pass od the first file i get bthis error
[B]
New video file has different resolution or colorspace than the previous one.[/B]

any help would be appreciated greatly

thanks in advance

---

### Post by rfrayer on 2010-01-09
after googling around for a wile i figured it out

[http://ubuntuforums.org/showthread.php?t=1376304](http://ubuntuforums.org/showthread.php?t=1376304)

---

