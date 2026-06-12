---
title: "Convert Command Not Working"
date: 2009-12-29
forum: General Help
---

### Post by adam22 on 2009-12-29
I just installed 64 bit Karmic Koala and am trying to use terminal to convert a screenshot from .png to .jpg. However, it won't work (I had no problems in 9.04).

```
adam@adam-laptop:~$ cd ~/Desktop
adam@adam-laptop:~/Desktop$ convert Screenshot.png Screenshot.jpg
The program 'convert' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
convert: command not found
```

---

### Post by x33a on 2009-12-29
yes you first need to install imagemagick.

try
```
sudo apt-get install imagemagick
```

---

### Post by adam22 on 2009-12-29
Thank you very much. I should've realised it from the output but I don't remember ever installing it before. Everything is fine now.

Cheers.

---

