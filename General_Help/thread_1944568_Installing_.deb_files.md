---
title: "Installing .deb files"
date: 2012-03-21
forum: General Help
---

### Post by Haximus on 2012-03-21
Hello ubuntu community! I'm new, and I wish to install a .deb file. The file glut.h for OpenGL does not come on my machine, whereas gl.h does. How do I install the glut3.deb file?

---

### Post by HiImTye on 2012-03-21
double click on it in the file browser, it should open software center and then you can click on install (or it will tell you why it can't install)

---

### Post by Haximus on 2012-03-21
It doesn't work. When opening up the software center and clicking Install, the button will fade but no installation will start. Thanks for the reply!

---

### Post by haqking on 2012-03-21
```
sudo dpkg -i filename.deb
```

---

### Post by CharlesA on 2012-03-21
> **haqking said:**
> ```
sudo dpkg -i filename.deb
```
Forgot sudo. ;)

---

### Post by Yellow Pasque on 2012-03-21
Forget the .deb. Do this:
```
sudo apt-get install freeglut3-dev
```

---

### Post by haqking on 2012-03-21
> **CharlesA said:**
> Forgot sudo. ;)

ahh my bad, long day ;-)

edited

cheers

---

### Post by CharlesA on 2012-03-21
> **haqking said:**
> ahh my bad, long day ;-)

edited

cheers
Happens to everyone.

@OP: Try doing what Temüjin posted. If it's in the repos, it's easier to install that way.

---

