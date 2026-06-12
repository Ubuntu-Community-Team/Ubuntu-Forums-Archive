---
title: "BASH variable from zenity?"
date: 2009-07-12
forum: General Help
---

### Post by fraser_m on 2009-07-12
First script, so bear with me...

I'm trying to write a bash script that downloads a 16×16 favicon.ico for a site, and converts it to a 256×256 PNG. I'm having trouble getting output from zenity though.

This is it so far:
```
$SITE=`zenity --entry --text="Which favicon to download?"`
wget $SITE/favicon.ico
convert favicon.ico -filter Point -resize 1600% $SITE.png
rm ./favicon.ico
```

I want to get a $SITE from the entry box, but I seem to be incapable.

What am I doing wrong?

Feel free to point out any other improvements, too.

---

### Post by fraser_m on 2009-07-12
Bump, s'il vous plait.

---

### Post by sisco311 on 2009-07-12
```
SITE=`zenity --entry --text="Which favicon to download?"`
wget $SITE/favicon.ico
convert favicon.ico -filter Point -resize 1600% $SITE.png
rm ./favicon.ico
```;)

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html")

---

### Post by fraser_m on 2009-07-12
Thanks a lot!

---

