---
title: "I got World of Warcraft working, but... (need help)"
date: 2006-06-06
forum: General Help
---

### Post by darthvivi on 2006-06-06
I got WoW working on Dapper just now using WINE. But it was so slow it's nearly unplayable. When I play from Windows, the game runs smoothly and isn't at all slow. The FPS couldn't have been higher than 3 on Dapper. However, it connects just fine, and everything seems to work except for how slow it is. There's a couple of reasons I think it might be going so slow:

1) I'm running WoW.exe from my Windows XP partition. Would that make it go slower?

2) I'm running it in XGL. I did an automatic script when I got Dapper that installed XGL and apparently deleted everything else...there's no other session for me to choose from. I guess I could install a new one, just for WoW?

3) When I run WoW.exe from WINE, I get a ton of errors in the terminal:

> wine "/windows/Program Files/World of Warcraft/WoW.exe"
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d8c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d8c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbeedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbf448,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbf6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbf6e8,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!

It goes on, but Ubuntu Forums won't let me post the entire thing...

---

### Post by David Corrales on 2006-06-06
I saw a DirectX 9 error in that log... are you running it in OpenGL mode?

---

### Post by MegaBill on 2006-06-06
To put it simply, you cannot run games like that on an XGL server.  It is impossible, as compiz/xgl is not stable enough.  Believe me, I've tried everything, and I've only been able to get it to run on a standard server.  If you don't have that option, then something isn't installed properly.

---

### Post by eqisow on 2006-06-06
Aye, XGL is definitely the issue. There is a thread in the gaming area about getting games to run with XGL, but I'm not sure how well that works. Also, make sure you use the -opengl flag when running WoW.

---

### Post by stimpack on 2006-06-06
Yes WoW runs slower under wine. In the day and for odd groups it suffices. However at night when Im raiding I have to reboot into Windows.

---

### Post by darthvivi on 2006-06-06
I don't think the problem was XGL. All I did was add -opengl and everything worked smoothly. However, the servers are down right now, so I can't test in-game, but the animations on the title screen aren't lagging anymore.

Thanks for your help. I also installed Fluxbox last night, and it worked alright on it. (There was some issues with far off land flickering, but that may have just been because I didn't add -opengl)

Edit: Nevermind, adding -opengl GREATLY improved the framerate in XGL, but it's still is pretty slow and not worth playing on.

---

### Post by .t. on 2006-06-06
DirectX 9 isn't supported well in any version of Wine. It's very hard to a) implement and b) reverse-engineer (ask the ReactOS guys - they're in the middle of an audit!). It's just not documented anywhere.

---

