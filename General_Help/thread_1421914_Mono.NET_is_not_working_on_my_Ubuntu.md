---
title: "Mono/.NET is not working on my Ubuntu"
date: 2010-03-04
forum: General Help
---

### Post by AquaFusion on 2010-03-04
I been trying to load one applcation is using .NET Framework 2.0. I went to Mircosoft to get the .NET 2.0 and attempting to install it but got a error. I look it up in the internet. Many topic point out that I have to install Mono to get it to work. I went to Ubuntu Software Center to get Mono, only one that I am unsure of is "MonoDevelop". But i installed it anyway and it still not helping. So I went to google to find info on how to install Mono on my Karmic. Found this, [http://ruski.co.za/page/Install-Mono-on-Ubuntu.aspx](http://ruski.co.za/page/Install-Mono-on-Ubuntu.aspx)  They point out that Ubuntu do have Mono pre-installed but they are using the old version, So I have to update it. By following those terminal command to get Mono installed. Then I got to the end and it said to check if Mono is installed. It comfirmed that it is there. So I went to install NET. 2.0, it still having error to install. I check what the error signature, it said something about Visual Studio setup.exe

I thought to try to open the applcation that is using .NET 2.0, it still have error. How I able to get it to work?

---

### Post by AquaFusion on 2010-03-05
I am sure anyone know how to get Mono working. It would be nice to get it to work properly

---

### Post by lykwydchykyn on 2010-03-05
You cannot install Microsoft .NET framework on Ubuntu.  It's software designed for Windows, it won't run on Linux (well, it MIGHT work in WINE, but last time I tried it I had no luck).

MONO is an open source implementation of .NET; you can think of it as the .NET Framework for Linux, but it's not 100% compatible.  Just because something uses .NET on Windows doesn't guarantee it will work in MONO.

Mono is installed by default on Ubuntu if memory serves, though you can make sure by using Synaptic to install the "mono-complete" package.

---

