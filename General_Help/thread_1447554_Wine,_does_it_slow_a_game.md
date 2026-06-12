---
title: "Wine, does it slow a game"
date: 2010-04-05
forum: General Help
---

### Post by Joe Bloggs1 on 2010-04-05
Hi, first post and is a simple question for some on here.
If I install a game using wine , will it/does it have any deteramental effect in it's running speed and stuff ie will it be using the wine enviroment to run the game whilst playing it?.  Or should I find a different method to install it directly into ubuntu 9.1?

---

### Post by KeyserSoze93 on 2010-04-05
You mean does it make the game slower running it on Wine instead of natively?

I have had very mixed results - some stuff works fine, some stuff seems FASTER than Windows, and some stuff is a lot slower.

In general, one thing to look for is whether the game is based on Direct3D or OpenGL, since OpenGL apps seems fine, whereas Direct3D, especially without the native Windows libs, seem quite slow.

Which game is it?

---

### Post by djoxyk on 2010-04-05
Depending on game it can run fast (like Diablo does), but usually it run slow and some features are lost. You can check wineHQ base for particular game reports to determine if it's worth running under wine.

---

### Post by mickObrian on 2010-04-05
I've also had mixed results, I recommend visiting the WineHQ ([http://appdb.winehq.org/](http://appdb.winehq.org/)), it lists games and applications and how well they've worked for others so you know what problems may occur.

---

### Post by Joe Bloggs1 on 2010-04-05
Thx for the quick replies :)
I'm trying to install ut99 which can use both openGL and 3d3.

I'm not sure wether to start another thread on this but I'm a complete nood atm with ubuntu.

On the ut99 disc there are .sh files which can be used to install the game in ubuntu , the permissions are greyed ouit and most of them have a lock thingy on them.
I have no idea atm as to how to run these files from the cd or even how to copy the disc onto the desktop first.


here is some info I found -
**1.4. Is Wine an  emulator? There seems to be disagreement.**

 There is a  lot of confusion about this, particularly caused by people getting  Wine's name wrong and calling it WINdows Emulator. 
When users think of an emulator, they tend to think of  things like game console emulators or virtualization software. This is  the wrong way to think about Wine - Wine runs Windows applications in  essentially the same way Windows does. Wine is just a native Unix  substitute for the components of Windows; there is no inherent loss of  speed due to "emulation" when using Wine, nor is there a need to open  Wine before running your application. 
That said,  Wine can be thought of as a Windows emulator in much the same way that  Windows Vista can be thought of as a Windows XP emulator; both allow you  to run the same applications by translating system calls in much the  same way.  Setting Wine to mimic Windows XP is not much different from  setting Vista to launch an application in XP compatibility mode. 
There are a few things that makes wine more than just  an emulator. 

[LIST]
[*]Sections of Wine can be  used on Windows. Some virtual machines use Wine's OpenGL-based  implementation of Direct3D on Windows rather than truly emulate 3D  hardware. 
[*]Winelib can  be used for porting windows application source code to other operating  systems that Wine supports to run on any processor - even processes that  neither Windows nor the Emulator bit of Wine supports. 
[/LIST]
"Wine is  not just an emulator" would be a more correct name.  Thinking of Wine  as just an emulator is really forgetting about the other things it is.   Wine's "emulator" is really just a binary loader that allows Windows  applications to interface with the Wine API replacement.

---

### Post by Mark Phelps on 2010-04-05
You didn't mention your make/model video card.  

If you're running one of the "legacy" ATI cards (i.e., cards that are no longer supported with ATI Linux drivers), you will be using the default open source drivers, which, when trying to run 3D games, will work a LOT slower.

SO, what make/model video card are you using?

---

### Post by Joe Bloggs1 on 2010-04-05
Hi, I'm on  Fujitsu Laptop Amilo pi3560 dual core with a GT240M card. It has win7 on the other partition.

---

### Post by KeyserSoze93 on 2010-04-05
> **Joe Bloggs1 said:**
> Thx for the quick replies :)
I'm trying to install ut99 which can use both openGL and 3d3.

I'm not sure wether to start another thread on this but I'm a complete nood atm with ubuntu.

On the ut99 disc there are .sh files which can be used to install the game in ubuntu , the permissions are greyed ouit and most of them have a lock thingy on them.
I have no idea atm as to how to run these files from the cd or even how to copy the disc onto the desktop first.


here is some info I found -
**1.4. Is Wine an  emulator? There seems to be disagreement.**

 There is a  lot of confusion about this, particularly caused by people getting  Wine's name wrong and calling it WINdows Emulator. 
When users think of an emulator, they tend to think of  things like game console emulators or virtualization software. This is  the wrong way to think about Wine - Wine runs Windows applications in  essentially the same way Windows does. Wine is just a native Unix  substitute for the components of Windows; there is no inherent loss of  speed due to "emulation" when using Wine, nor is there a need to open  Wine before running your application. 
That said,  Wine can be thought of as a Windows emulator in much the same way that  Windows Vista can be thought of as a Windows XP emulator; both allow you  to run the same applications by translating system calls in much the  same way.  Setting Wine to mimic Windows XP is not much different from  setting Vista to launch an application in XP compatibility mode. 
There are a few things that makes wine more than just  an emulator. 

[LIST]
[*]Sections of Wine can be  used on Windows. Some virtual machines use Wine's OpenGL-based  implementation of Direct3D on Windows rather than truly emulate 3D  hardware. 
[*]Winelib can  be used for porting windows application source code to other operating  systems that Wine supports to run on any processor - even processes that  neither Windows nor the Emulator bit of Wine supports. 
[/LIST]
"Wine is  not just an emulator" would be a more correct name.  Thinking of Wine  as just an emulator is really forgetting about the other things it is.   Wine's "emulator" is really just a binary loader that allows Windows  applications to interface with the Wine API replacement.

UT99 works fine with both native and Wine for me.

The advantage of using Wine is that it is easier to integrate with addons, like the Chris Dohnal's OpenGL renderer, etc.

Unreal Engine 1 stuff generally works fine with Wine, especially using OpenGL. (DeusEx,UT99, Unreal1 etc.)

It's great to actually HAVE a native Linux port, but to be honest, running the Windows version with Wine is better all round, since I can use Windows specific dlls and stuff.

---

### Post by Joe Bloggs1 on 2010-04-06
Ah , I have found out that the servers I play on have UTDC as the anti-cheat which is not compatible with a wine install.
I am trying to get hold of the server admin to get some assistance in seeing if there is a different way to install this and if I need a ccertain patch or summit.

---

