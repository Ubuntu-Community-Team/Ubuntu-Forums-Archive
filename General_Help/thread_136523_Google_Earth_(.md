---
title: "Google Earth :("
date: 2006-02-26
forum: General Help
---

### Post by qb4ever on 2006-02-26
A few days ago I followed the gentoo wiki article and got it working then shutdown my computer for the night. Now I boot it up and get this from google earth:



> 
fixme:atl:AtlModuleInit SEMI-STUB (0x466920 0x4658f0 0x400000)

fixme:secur32:GetUserNameExW 2 0x3a0e87d0 0x7fa9f944
f
fixme:imm:ImmGetContext (0x1003a): stub
fixme:imm:ImmReleaseContext (0x1003a, 0x7fd44780): stubfixme:imm:ImmReleaseContext (0x10088, 0x7fd44780): stub
fixme:imm:ImmGetContext (0x1008a): stub
fixme:imm:ImmReleaseContext (0x1008a, 0x7fd44780): stub

Intrinsic Alchemy  v3.0 Beta-0928 (Dynamic/Release)
Built by Brent on Tue Sep 28 19:29:53 PST 2004

INFO: Using igOglVisualContext.
fixme:imm:ImmGetContext (0x20086): stub
fixme:imm:ImmReleaseContext (0x20086, 0x7fd44780): stub

err:rpc:RPCRT4_OpenConnection protseq mswmsg not supported
err:rpc:RPCRT4_OpenConnection protseq mswmsg not supported
err:rpc:RPCRT4_OpenConnection protseq mswmsg not supported
fixme:rpc:I_RpcServerStartListening (0x10022): stub

fixme:imm:ImmGetContext (0x1022c): stub
fixme:imm:ImmReleaseContext (0x1022c, 0x7fd44780): stub

QPainter::setPen: Will be reset by begin()

fixme:imm:ImmGetContext (0x10282): stub
fixme:imm:ImmReleaseContext (0x10282, 0x7fd44780): stub
QPainter::setPen: Will be reset by begin()

fixme:imm:ImmGetContext (0x10284): stub
fixme:imm:ImmReleaseContext (0x10284, 0x7fd44780): stub
QPainter::setPen: Will be reset by begin()

fixme:imm:ImmGetContext (0x10296): stub
fixme:imm:ImmReleaseContext (0x10296, 0x7fd44780): stub
**X connection to :0.0 broken (explicit kill or server shutdown)**.


I have tried everything from different nvidia drivers and kernels and wine versions to reinstalling ubuntu to no avail. :cry:

---

### Post by Stinger on 2006-02-26
Why even bother with google earth ? :p 

Look what Jamesh has put together for ya !

[Gnome World Wide]("http://www.gnome.org/~jamesh/maps/gnome.html") :mrgreen: 

Hope it helps.

---

### Post by emuman on 2006-02-26
I can confirm this error. Google Earth does not work with Wine 0.9.8 on Ubuntu.

---

### Post by qb4ever on 2006-02-26
Well after some more searching I found that automatix updated my display driver to the newest version, oops [-( , So after 10 more hours of fighting I found the 1 nvidia driver that actually worked last time that I forgot about.
[**Nvidia 1.0-7667**]("http://www.nvidia.com/object/linux_display_ia32_1.0-7667.html")

But now every other program has opengl acceleration but google earth go figure.  :rolleyes: It's really slow and studdery. Oh well, time for another reinstall.


Gnome world wide ain't 3d :p

---

### Post by Stinger on 2006-02-27
[QUOTE=qb4ever]
Gnome world wide ain't 3d :p[/QUOTE]

Does it need to be ?

---

### Post by muted on 2006-03-13
> **Stinger]Does it need to be ?[/QUOTE]
oh yes it does  said:**
> fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (15000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SEND_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
10.476613: LayerWindow::start() end
fixme:imm:ImmGetContext (0x104f6): stub
fixme:imm:ImmReleaseContext (0x104f6, 0x7fe4bfe0): stub
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithHandleData
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpFilterMemory


---

