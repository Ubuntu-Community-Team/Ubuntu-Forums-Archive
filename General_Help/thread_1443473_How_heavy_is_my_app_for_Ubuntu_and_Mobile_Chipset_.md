---
title: "How heavy is my app for Ubuntu and Mobile Chipset PC"
date: 2010-03-31
forum: General Help
---

### Post by brain!ac on 2010-03-31
Hi

Im working on a software which i wrote on Delphi (because of my experience),and i plan to run it from wine.

So my application is a multimedia one ,which contains a video player ,flash player ,plays image`s like slide show and a text ticker .

For video player i`m using VLC Plugin because of codec`s support (so i`m talking about VLC running on Windows Enviroment through wine and it uses OpenGL Video Out)

My Hardware is Intel 954 GMA with 1 GB DDR2 and Intel Atom 1.6 Core 2 Duo .

Can this machine handle this app.

---

### Post by 3rdalbum on 2010-03-31
The Atom is an Atom, not a Core 2 Duo.

If you can port the software to Linux, then it should be able to run fine.

Wine is not 100% compatible with Windows software, so there's a good chance that your code will not work. VLC might run on Wine, but depending on the video codec used your Atom might not be powerful enough; they tend to struggle with decoding video even when running native code, so Wine's overhead would probably cause the video to not play fluently.

---

### Post by brain!ac on 2010-03-31
> **3rdalbum said:**
> The Atom is an Atom, not a Core 2 Duo.

If you can port the software to Linux, then it should be able to run fine.

Wine is not 100% compatible with Windows software, so there's a good chance that your code will not work. VLC might run on Wine, but depending on the video codec used your Atom might not be powerful enough; they tend to struggle with decoding video even when running native code, so Wine's overhead would probably cause the video to not play fluently.

Thanks a lot for that feedback

So what you suggest ,can it work if i use to work on C# but using Mono for Visual Studio compile it on a Linux one ?

Does that mean the same like Wine ,or by using Mono it can run on a lower level ?

---

