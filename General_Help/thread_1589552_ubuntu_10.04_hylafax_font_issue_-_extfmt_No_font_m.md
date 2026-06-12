---
title: "ubuntu 10.04 hylafax font issue - extfmt: No font metric information found for &quot;Couri"
date: 2010-10-06
forum: General Help
---

### Post by Nemus on 2010-10-06
Hi I am having an issue with the hylafax package 

I keep getting this error which I normaly can fix with editing the font path in /etc/hylafax/hyla.conf in older version of ubuntu like 8.04 but with 10.04 that doesn't work 

#this is my ghostscript path
/usr/share/ghostscript/8.71/lib

ubuntu 10.04 2.6.32-25-generic-pae


this is the error I get

textfmt: No font metric information found for "Courier-Bold".
Usage: textfmt [-1] [-2] [-B] [-c] [-D] [-f fontname] [-F fontdir(s)] [-m N] [-o #] [-p #] [-r] [-U] [-Ml=#,r=#,t=#,b=#] [-V #] files... >out.ps
Default options: -f Courier -1 -p 11bp -o 0
Error converting document; command was "textfmt -B -f Courier-Bold      -Ml=0.4in -p 11 -s default >'/tmp//sndfaxAYqzQG' <'new.txt'"

any help on this would be awesome thank yo0u

---

