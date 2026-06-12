---
title: "trying to install game"
date: 2010-04-10
forum: General Help
---

### Post by nerdy_kid on 2010-04-10
trying to install Excalibur: Morgana's Revenge, but make fails with
```

/usr/include/SDL/SDL_video.h: In member function ‘bool ImageDescriptor::LoadFromFile(FileSpecifier&, int, int, int, int, int)’:
/usr/include/SDL/SDL_video.h:589: error: too few arguments to function ‘SDL_Surface* SDL_LoadBMP_RW(SDL_RWops*, int)’
ImageLoader_SDL.cpp:70: error: at this point in file
ImageLoader_SDL.cpp: At global scope:
ImageLoader_SDL.cpp:142: fatal error: opening dependency file .deps/ImageLoader_SDL.Tpo: Permission denied
compilation terminated.
make[3]: *** [ImageLoader_SDL.o] Error 1
make[3]: Leaving directory `/home/jesse/Desktop/0-AlephOne-20100218/Source_Files/RenderMain'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jesse/Desktop/0-AlephOne-20100218/Source_Files'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jesse/Desktop/0-AlephOne-20100218'
make: *** [all] Error 2

```

so i downloaded the windows version and ran it with wine, that installed fine, but when i try to start a game, wine crashes with
```

-----@-----laptop:~/.wine/drive_c/Program Files/EMR$ wine EMR\ 3.0.exe 
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0080: stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0001: stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1cd720,0x1cd668): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1ce050,0xc6eb48): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xc673f8,0x1cd668): stub
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:event:wait_for_withdrawn_state window 0x2002c/4e00005 wait timed out
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglCreateContext Cannot get FB Config for iPixelFormat 0, expect problems!
----@-----laptop:~/.wine/drive_c/Program Files/EMR$ 

```


is there a solution to one of these problems??

---

### Post by nerdy_kid on 2010-04-10
nvm, got it to run in a windows VM :)

---

