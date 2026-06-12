---
title: "WoW Error - 11.04"
date: 2011-04-30
forum: General Help
---

### Post by -tr on 2011-04-30
Hello all. Just updated to Ubuntu 11.04 this morning, and was immediately overwhelmed. The new panel layout and sidebar thingy looks pretty sweet at first glance, but I can't find a durn thing. :s

But to the point, went to run World of Warcraft after the update and the launcher starts, then after hitting play a fatal error pops up. 

```
This application has encountered a critical error:
Fatal Exception!
Program: Z:\home\tim\Games\World of Warcraft\Wow.exe
ProcessID: 70
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0023:F751D270
The instruction at "0xF751D270" referenced memory at "0x00000000". The memory could not be "read".
```

And then of course the other Blizzard error nonsense. I know this isn't so much a Ubuntu thing, but has anyone else maneuvered around this or have any ideas for a fix? Any help is much appreciated.

---

### Post by -tr on 2011-04-30
Seems to be some sort of problem with opengl compatibility or something.. I do have the current nvidia driver installed, and have 32 and 64 bit libgl.so so I'm not really sure what to do from here. =s

---

### Post by Shmantiv_Radio on 2011-04-30
What hardware are you using, and are you using WIFI?

---

### Post by -tr on 2011-04-30
> **Shmantiv_Radio said:**
> What hardware are you using, and are you using WIFI?

EVGA X58 SLI MB, Intel i7 920 CPU, EVGA GTX 260 GPU, 3x2GB 1866 OCZ DDR3 RAM.

Nope, ethernet.

---

### Post by Shmantiv_Radio on 2011-04-30
> **-tr said:**
> EVGA X58 SLI MB, Intel i7 920 CPU, EVGA GTX 260 GPU, 3x2GB 1866 OCZ DDR3 RAM.

Nope, ethernet.

You have got
```
SET gxApi "opengl"
```

in config.wtf yes?

---

### Post by -tr on 2011-04-30
> **Shmantiv_Radio said:**
> You have got
```
SET gxApi "opengl"
```

in config.wtf yes?

Didn't used to but added it earlier, yes.

---

### Post by slooksterpsv on 2011-04-30
Did you add the following to the registry:

HKEY_CURRENT_USER\Software\Wine -> Right-click on Wine -> New Key named: OpenGL

Click on OpenGL right-click on the right-hand side and choose New-> String Value name it: DisabledExtensions
Double click on it, add the this to the string:

GL_ARB_vertex_buffer_object

Choose OK, and try to start WoW again.

---

### Post by -tr on 2011-04-30
> **slooksterpsv said:**
> Did you add the following to the registry:

HKEY_CURRENT_USER\Software\Wine -> Right-click on Wine -> New Key named: OpenGL

Click on OpenGL right-click on the right-hand side and choose New-> String Value name it: DisabledExtensions
Double click on it, add the this to the string:

GL_ARB_vertex_buffer_object

Choose OK, and try to start WoW again.

Hrm? What registry?

EDIT: Nvm, found it. Trying that now.

UGH! That didn't work either.. =s

---

### Post by -tr on 2011-04-30
Well it seems that my 32 bit libraries are not up to speed. Where can I find them for 64 bit Ubuntu?

---

