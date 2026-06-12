---
title: "WebGL GPU Acceleration Issue"
date: 2012-05-10
forum: General Help
---

### Post by vandorjw on 2012-05-10
Hey Everyone,

WebGl does not work for me. According to firefox support page its because of "Blocked for your graphics card because of unresolved driver issues."

Is it really an unresolved Driver issue or is my GPU just too old? This tower might be old, but it is really not that bad. 

What is the proper Ubuntu method to check for and remove conflicting drivers?

Also, what is the prefered driver for this card?

Cheers

> 
basement@Presario-6350CA:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 (RV280 5960) x86/MMX/SSE2 TCL DRI2


From about:support
> 
Application Basics
**Name:** Firefox
**Version:** 12.0
**User Agent:** Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:12.0) Gecko/20100101 Firefox/12.0

Graphics
**Adapter Description**: Tungsten Graphics, Inc. -- Mesa DRI R200 (RV280 5960) x86/MMX/SSE2 TCL DRI2
**Vendor ID:** Tungsten Graphics, Inc.
**Device ID:** Mesa DRI R200 (RV280 5960) x86/MMX/SSE2 TCL DRI2
**Driver Version:** 1.3 Mesa 8.0.2
**WebGL Renderer:** [COLOR="Red"]Blocked for your graphics card because of unresolved driver issues.[/COLOR]
**GPU Accelerated Windows:** [COLOR="Red"]0. Blocked for your graphics card because of unresolved driver issues.[/COLOR]
**AzureBackend:** skia


---

### Post by idoitprone on 2012-05-10
> **cc7gir said:**
> Hey Everyone,

WebGl does not work for me. According to firefox support page its because of "Blocked for your graphics card because of unresolved driver issues."

Is it really an unresolved Driver issue or is my GPU just too old? This tower might be old, but it is really not that bad. 

What is the proper Ubuntu method to check for and remove conflicting drivers?

Also, what is the prefered driver for this card?

Cheers




From about:support

yep your card is too old
webgl uses opengl 2.0 specs while your card support only 1.3 
All i can say is upgrade your
 outdated card
> 
**Device ID:** Mesa DRI R200 (RV280 5960) x86/MMX/SSE2 TCL DRI2
**Driver Version: 1.3 Mesa 8.0.2**
WebGL is a cross-platform, royalty-free web standard for a low-level 3D  graphics API based on OpenGL ES 2.0, exposed through the HTML5 Canvas  element as Document Object Model interfaces. Developers familiar with  OpenGL ES 2.0 will recognize WebGL as a Shader-based API using GLSL,  with constructs that are semantically similar to those of the underlying**  OpenGL ES 2.0 API**. It stays very close to the OpenGL ES 2.0  specification, with some concessions made for what developers expect out  of memory-managed languages such as JavaScript.
[http://www.khronos.org/webgl/](http://www.khronos.org/webgl/)

---

### Post by vandorjw on 2012-05-10
Thank you. This is what I thought the issue was. Thanks for confirming.
I may upgrade to this. [http://www.newegg.ca/Product/Product.aspx?Item=14-500-228](http://www.newegg.ca/Product/Product.aspx?Item=14-500-228)
[Solved]

---

