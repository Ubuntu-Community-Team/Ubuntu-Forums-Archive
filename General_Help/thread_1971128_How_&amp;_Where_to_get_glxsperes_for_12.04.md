---
title: "How &amp; Where to get glxsperes for 12.04 ??"
date: 2012-05-02
forum: General Help
---

### Post by bogan on 2012-05-02
Hi, **All,**

I get widely varying figures of Frame-Rates running glxgears, depending on whether logged in to Gnome Classic, Ubuntu 2D, or 3D; in 12.04 LTS they vary from 2500 to 1200, with, surprisingly Ubuntu 2D being the lowest.

In 11.10 I had figures as high as 6000. Does this really reflect the additional GPU load of 12.04 Unity5??

I would like to try glxspheres - although I see in one thread that 12.04 compiz causes falsely low figures due to a bug - would someone please Post where I can download the glxspheres test program, as apt-get cannot find it, and a Google search revealed no source.
 Ubuntu Software Center only shows Mesa-Utils, which does not include glxspheres.

Chao!,** bogan**.

---

### Post by brainwash on 2012-05-02
1. Download VirtualGL (.deb) from:
```
http://www.virtualgl.org/Downloads/VirtualGL
```

2. Navigate to the folder containing the deb package and install it with:
```
sudo dpkg -i VirtualGL_*.deb
```

3. Run glxspheres:
```
cd /opt/VirtualGL/bin/
./glxspheres

**OR**

/opt/VirtualGL/bin/glxspheres
```

---

### Post by bogan on 2012-05-02
Hi! & Thanks,** Brainwas**h,

Does that mean it can not be run with a simple cmd line command, as I see quoted in BumbleBee user's Posts??

Chao!,** bogan**.

---

### Post by brainwash on 2012-05-02
Ah my fault, you don't have to use exec. Simply run it by specifiying the absolute path or add /opt/VirtualGL/bin to your PATH variable and run it likes this:
```
glxspheres
```

---

### Post by hextler on 2012-08-01
try to use following  command to install it

apt-get install virtualgl-libs libgl1-mesa-glx

---

### Post by bogan on 2012-08-01
Hi!, hextler,

Thanks for your Post, however, it gave me:```
sudo apt-get install virtualgl-libs libgl1-mesa-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package virtualgl-libs
```I also tried with upper case V & G, but it gave the same result.

' libgl1-mesa-glx ' is already installed but there is no match for ' virtualgl-libs ' in either Synaptic or Software center.
 
Did you mean to use that command after adding a ppa? if so, would  you please  Post its name?

[ I only just realised I miss-spelt the title of the thread.]

Chao!, **bogan.**

---

