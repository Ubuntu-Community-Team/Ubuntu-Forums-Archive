---
title: "Chrome 10 WebGL not working"
date: 2011-04-12
forum: General Help
---

### Post by CootCraig on 2011-04-12
I would like to get WebGL to work with Chrome 10 (and also FireFox 4)

Running 10.04 as VMware guest on windows 7 host.

glxgears displays fine.

 lspci -nn | grep VGA                                                       &#9474;                                                                                  
00:0f.0 VGA compatible controller [0300]: VMware SVGA II Adapter [15ad:0405]      


glxinfo reports:

28 OpenGL vendor string: Mesa Project                                                                                                                                      
 29 OpenGL renderer string: Software Rasterizer                                                                                                                             
 30 OpenGL version string: 2.1 Mesa 7.7.1                                                                                                                                   
 31 OpenGL shading language version string: 1.20      

Any ideas on how to do this?

---

### Post by davidmohammed on 2011-04-12
you need opengl version 2 or better to get webgl to work...

you'll need a better graphics card at a guess

---

### Post by lithopsian on 2011-04-12
A better card or better drivers.  Looking at your lspci output I'd say a better card.

You don't have hardware acceleration anyway from your card.  You are using a software rasteriser which mimics hardware acceleration but actually runs the graphics through your main CPU.  Slow obviously.

You can do the same for WebGL, on Firefox at least.  Not sure about Chrome.  Your need the osmesa library and you need to configure it into a Firefox preference.  Probably not worth the effort though unless you have a fantastically powerful CPU, and even then it won't be as good as a decent newish graphics card.

---

### Post by CootCraig on 2011-04-12
> **davidmohammed said:**
> you need opengl version 2 or better to get webgl to work...

you'll need a better graphics card at a guess

glxinfo reports OpenGL 2.1.  

  OpenGL vendor string: Mesa Project                                                                                                                                        
   OpenGL renderer string: Software Rasterizer                                                                                                                               
 OpenGL version string: 2.1 Mesa 7.7.1                                                                                                                                     
   OpenGL shading language version string: 1.20      

I'm not expecting good performance, but I want to experiment with WebGL
The Mesa library is fine with me.

---

### Post by CootCraig on 2011-04-12
> **lithopsian said:**
> A better card or better drivers.  Looking at your lspci output I'd say a better card.

You don't have hardware acceleration anyway from your card.  You are using a software rasteriser which mimics hardware acceleration but actually runs the graphics through your main CPU.  Slow obviously.

You can do the same for WebGL, on Firefox at least.  Not sure about Chrome.  Your need the osmesa library and you need to configure it into a Firefox preference.  Probably not worth the effort though unless you have a fantastically powerful CPU, and even then it won't be as good as a decent newish graphics card.

The host computer is an HP Envy 17 with ATI Mobility Radeon HD5850.  In this setup I would do perfomance testing on the Windows 7 host side.  I would like to develop and debug in my development VMware host Ubuntu system.

---

### Post by davidmohammed on 2011-04-12
my bad - I saw "1.2" and assumed that that was your opengl version.

[Here]("http://support.mozilla.com/en-US/questions/720087") is an interesting thread - sometips in the comments towards the bottom of the thread on how to force webgl in firefox4.

However I note you are trying to use vmware to run ubuntu ... I think that maybe the key issue - maybe the vmware "graphics card" doesnt have all the functionality to support webgl.  Have you tried to install ubuntu as either a dual boot or via a "wubi.exe" install?  If you do either of these, you can also install the ATI graphics driver which should support webgl correctly.

---

