---
title: "ATI Drivers 8.24.8"
date: 2006-04-23
forum: General Help
---

### Post by buttari on 2006-04-23
Hi,
I have a thinkpad t60p with an ATI FireGL v5200 graphic card. Dapper is installed on this machine. The 8.24.8 ATI drivers don't officially support this graphic card but there is a trick to make it work like described here:
[http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200]("http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200")
I did it and X is working so the graphic card has been detected correctly. BTW 3d acceleration doesn't seem really good. 
fglrxinfo says:
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5755 (8.24.8)

What does it mean that rendere=Pentium4? does it mean that the rendere is the main processor and not the graphig card processor?
glxgears doesn't return any number and gears spin almost slow (smooth though).
Finally screensaver "ant spotlight" is choppy.
Any suggestion?

Thanks in advance

Alfredo

---

