---
title: "Plymouth splash has weird (low) colors on startup but normal colors on shutdown"
date: 2010-06-08
forum: General Help
---

### Post by tropicalfish on 2010-06-08
Hello!

My Plymouth splash screen has weird colors on startup, but when I shut down, the colors are normal.

I've searched around but only found fixes for low resolution, which I've set for 1024x768 (instead of my monitor's 1280x1024 in case I ever need to use my computer on a different lower res monitor).

Pics: (pardon the darkness, don't have an editor installed yet)

Startup (weird colors): Click -> [http://i144.photobucket.com/albums/r183/mrairplaneman777/DSC_4320.jpg](http://i144.photobucket.com/albums/r183/mrairplaneman777/DSC_4320.jpg)

Shutdown (normal colors): Click -> [http://i144.photobucket.com/albums/r183/mrairplaneman777/DSC_4318.jpg](http://i144.photobucket.com/albums/r183/mrairplaneman777/DSC_4318.jpg)

EDIT: I forgot to add that it happens on other splash screens. The Ubuntu Studio splash has a green box around/behind the "ubuntu studio" text, and the logo is a cyan (255-blue 255-green) color.

---

### Post by tropicalfish on 2010-06-09
Bump...

---

### Post by dino99 on 2010-06-09
try:

sudo dpkg-reconfigure plymouth

---

### Post by tropicalfish on 2010-06-09
Nope, didn't fix it :(


EDIT: In fact, that has increased the time that a black screen appears and reduced plymouth to only a quick "blink" on startup.

---

### Post by tropicalfish on 2010-06-09
Solved:

[http://ubuntuforums.org/showpost.php?p=9014050&postcount=450](http://ubuntuforums.org/showpost.php?p=9014050&postcount=450)

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u

sudo sed -i "/splash/s/splash/splash vga=795/" /etc/default/grub
sudo update-grub
```

---

