---
title: "Flickering when scrolling with fire fox"
date: 2012-04-01
forum: General Help
---

### Post by captainnoobing on 2012-04-01
I am using ubuntu 11.10 and when i scroll up and down websites the page flickers?

Any advice would be appreciated:KS.

I don't have a separate graphics card just the motherboard lol.

I hav'nt installed the drivers because i don't know how to on linux(windows just put disk in and menu comes up and select which drivers to install) 

Thats why my user name is captainnoobing):P

---

### Post by raja.genupula on 2012-04-01
whats your graphics card . 
```
lspci | grep VGA
```
and follow this 


[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by captainnoobing on 2012-04-01
Thanks for reply raja.genupula

I will have a read of the link.

---

### Post by captainnoobing on 2012-04-01
The graphics are part of the mother board.

AsRock p4s61

 Int. Real 256E 3D Graphics
Max. 64MB shared memory


Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by captainnoobing on 2012-04-01
Some info from firefox browser trouble shooting-

GRAPHICS

Adapter DescriptionGLXtest process failed (exited with status 1): X error occurred in GLX probe, error_code=9, request_code=55, minor_code=0

WebGL RendererBlocked for your graphics card because of unresolved driver issues.

GPU Accelerated Windows0. Blocked for your graphics driver version. Try updating your graphics driver to version <Anything with EXT_texture_from_pixmap support> or newer.

---

