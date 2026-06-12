---
title: "Need Help Setting Up Scanner"
date: 2011-09-10
forum: General Help
---

### Post by johnsmoke on 2011-09-10
I have an All In One Lexmark X2670 printer/scanner. I managed to install a driver for it and I can print with no problems at all now, which is great. But it looks like the scanner is not being recognized. I tried to test it using Simple Scan, and it just says "Failed To Scan" then under that "Unable to Connect To Scanner." Does anyone know how I can get Ubuntu to recognize my scanner? I can print perfectly, but my built-in scanner is not being recognized.

---

### Post by TurtleKing on 2011-09-10
Try doing it via terminal, to see if it gives extra hints of what you need. Might want to visit site manufacturer to see if they have info on this problem (linux drivers).

---

### Post by pqwoerituytrueiwoq on 2011-09-10
run this command
```
scanimage -L
```if it is supported by sane it will show up in there
scanning via command line
```
scanimage -d "$DEVICE" --format=ppm > "/home/$USER/Desktop/scan -`date`.ppm"
```

---

### Post by johnsmoke on 2011-09-11
> **pqwoerituytrueiwoq said:**
> run this command
```
scanimage -L
```if it is supported by sane it will show up in there
scanning via command line
```
scanimage -d "$DEVICE" --format=ppm > "/home/$USER/Desktop/scan -`date`.ppm"
```

This is kind of strange... I started up this morning, tried it out with Simple Scan, and it works now!! Maybe a restart was required or something. YAY! I now have my printer/scanner combo working in Ubuntu :guitar:           Thanks for the advice

---

