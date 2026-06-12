---
title: "How can i stop the xsession reporting errors?"
date: 2010-04-13
forum: General Help
---

### Post by dgrafix on 2010-04-13
.xsession-errors  at 45 Gig!!!!!!

I delete the file and within about a week i am back to a "out of space error"

I have tried root owning the file with no permission to write, but it still gets written, just with a number on the end :(

the system appears to be working fine otherwise. I could set a cron remove but that seems a bit more hacky than telling it to shut up.

---

### Post by duanedesign on 2010-04-14
Seems this is a popular request with not many solutions. my first thought is:

ln -s /dev/null .xsession-errors

I am trying it now to see what i get. Unfortunately i do not get a lot of writing to the file. Ill post results after a bit.

EDIT:So far so good
EDIT2:Nope it eventually moved the link over to .xsession-errors.old and wrote a new .xsession-errors

Also a few things on the subject. You might find it interesting what others have tried.

[http://ubuntuforums.org/showthread.php?t=1301062](http://ubuntuforums.org/showthread.php?t=1301062)
[http://forum.nginx.org/read.php?23,13345](http://forum.nginx.org/read.php?23,13345)
[http://ubuntuforums.org/showthread.php?t=415662](http://ubuntuforums.org/showthread.php?t=415662)

---

### Post by dgrafix on 2010-05-07
Damn happened again tonight, run out of space and sure enough a 45 gig xsession errors.

---

### Post by dracayr on 2010-05-07
in /etc/X11/Xsession, there is this (at least on my system):```
# truncate ERRFILE if it is too big to avoid disk usage DoS
if [ "`stat -c%s \"$ERRFILE\"`" -gt 500000 ]; then
  T=`mktemp -p "$HOME"`
  tail -c 500000 "$ERRFILE" > "$T" && mv -f "$T" "$ERRFILE" || rm -f "$T"
fi
```
maybe that's broken somehow.. of course this only works if you periodically restart X/your computer..

dracayr

---

### Post by dgrafix on 2010-05-18
In the end i just got chron to delete the file every hour :D

Still bit of a pain, it must spew out tonnes of info if it can get that big in just a few days.

---

