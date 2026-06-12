---
title: "Matlab 3d figure rendering glitch"
date: 2009-07-20
forum: General Help
---

### Post by plwert on 2009-07-20
I recently began using  Matlab for university work. Everything was somewhat ok until I got to the point where I needed to render 3d plots. I always end up with rendering glitches such as:

[IMG]http://imagebin.org/index.php?mode=image&id=56483[/IMG]


The plot itself is ok (it's a set of 3d lines with their projection also plotted on the x-y plane). However, if you look at the bottom left corner, you can see artefacts from when I rotated. Same goes for the label.

Has anyone else encountered this problem? Any ideas for a solution? I have the strange feeling that this is a graphics driver problem and not an actual problem with Matlab itself.

My video card is an intel 945GM/GMS 943/940GML (came with my Dell inspiron 640m laptop). This is with Matlab 7.7.0.471 (R2008b).

---

### Post by xanderp123 on 2009-10-06
I have a similar problem, except I can't even see my 3D plots at all!! This is not good. I have a physics assignment due tomorrow! Take a look at the attached screenshot.

I have this problem with some other programs as well. I frequently see very similar patterns of distortion/rendering glitches in Eclipse and Kile. In Eclipse, it often happens to the curved edges on the editor tabs. In Kile, the whole window often gets distorted just like the figure in the Matlab screenshot. In Kile, however, if I move my cursor over the distorted areas, they redraw fine.

---

### Post by xanderp123 on 2009-10-06
I forgot to mention in my last post that I'm using Gnome, not KDE. But I do have a Dell laptop, same as you, with an ATI Mobility Radeon X1300 graphics card and I'm using Matlab 7.7.0 (R2008b). I've been putting up with this problem for a while, but I may have found a simple fix!! (I still don't know what it did, but it seems to have worked).

I just visited [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) and did the following steps (as suggested by the guide):

$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

and then add this to the device section for your graphics card in xorg.conf:

        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option        "BusType" "PCI"
        Option         "AGPMode" "1"

then log out and back in of course. Before I did this, I got >400 fps with glxgears (but it flickered A LOT) and now I only get ~100fps but I can see my 3D plot in Matlab!! That's all I care about right now.

Does this look like a vibrating drum head to you?

---

### Post by beastrace91 on 2009-10-06
Maple 13 was having a similar issue on my netbook (intel gfx card) upgrading to the Karmic beta how ever seems to have resolved the issue... If you are feeling adventurous give it a go :)

~Jeff

---

