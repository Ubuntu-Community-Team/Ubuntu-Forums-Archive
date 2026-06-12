---
title: "custom login screen won't show up?"
date: 2012-01-22
forum: General Help
---

### Post by Kuroc on 2012-01-22
I need some help.
I just installed ubuntu 11.10 on my laptop and I'm in the process of tweaking it.
I've tried: Ubuntu tweak, I've tried manually editing several text files, and I've tried editing the pic in several different ways but nothing has worked.
All I get is a black image as background on the login screen.

What am I doing wrong?

---

### Post by Double.J on 2012-01-22
Hi there!

Login is handled by lightdm.

the configuration file you need to change is /etc/lightdm/unity-greeter.conf 

Before you edit it, back it up:
```

cd /etc/lightdm && ls
sudo cp unity-greeter.conf unity-greeter.conf.old
```

You also may need to shrink your image - I like to use gimp (you will need root privilages to save the image to the backgrounds directory) you may also have to install gimp.
```

gksudo gimp
```

in gimp open your image, click on image>scale image... and use the box to shrink it down to a much smaller size - mine is 1.1Mb 

Save the picture as type .png in the /usr/share/backgrounds directory. Do not use special characters- this just makes it more complicated.

then back in the terminal (in the light dm directory), open your unity-greeter.conf
```

sudo nano -w unity-greeter.conf
```

change the line
> background=/usr/share/backgrounds/warty-final-ubuntu.png
to
> 
background=/usr/share/backgrounds/[COLOR="Green"]yourimage.png[/COLOR]


press CTRL+X, then Y, then ENTER to save the document...

That should be it!

Hope it helps!

---

### Post by Kuroc on 2012-01-23
I already tried what you suggested. didn't work.
Then I ended up reinstalling ubuntu and then tried it again and it worked. I don't know what was going on?

Thanks for the help anyway:D

---

