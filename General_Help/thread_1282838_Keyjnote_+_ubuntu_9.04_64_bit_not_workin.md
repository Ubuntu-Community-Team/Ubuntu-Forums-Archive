---
title: "Keyjnote + ubuntu 9.04 64 bit not workin"
date: 2009-10-04
forum: General Help
---

### Post by natacho on 2009-10-04
Hi
I'm trying to run keyjnote with ubuntu 9.04 64bit in my HP tx2000

This is what i get
```
keyjnote slides.pdf 
Welcome to Impressive version 0.10.2
/usr/bin/keyjnote:94: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import random, getopt, os, types, re, codecs, tempfile, glob, StringIO, md5, re
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing
Detected screen size: 1280x800 pixels
FATAL: cannot create rendering surface in the desired resolution (1280x800)

```

Thanks for the help

---

### Post by amit_m on 2009-11-01
I am also having same kind of error. I am using Karmic Kaola and installed keyjnote using synaptic; so, I hope I have all the dependencies. 

```
keyjnote -L time=TR  /media/581D-78B0/Presentation/GE_2.pdfWelcome to Impressive version 0.10.2
/usr/bin/keyjnote:94: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import random, getopt, os, types, re, codecs, tempfile, glob, StringIO, md5, re
Detected screen size: 1024x768 pixels
OpenGL renderer: Mesa DRI Intel(R) 852GM/855GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
Using GL_ARB_texture_rectangle.
Traceback (most recent call last):
  File "/usr/bin/keyjnote", line 4015, in <module>
    run_main()
  File "/usr/bin/keyjnote", line 3576, in run_main
    main()
  File "/usr/bin/keyjnote", line 3567, in main
    UpdateCaption(Pcurrent)
  File "/usr/bin/keyjnote", line 2337, in UpdateCaption
    pygame.display.set_caption(caption, __title__)
TypeError: argument 1 must be string without null bytes, not str


```

---

