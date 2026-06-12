---
title: "was not declared in this scope"
date: 2009-11-04
forum: General Help
---

### Post by Catapults on 2009-11-04
How do you fix this problem?

```
src/graphics/gstage.cp: In member function 'void gstage::SetLights(TGraphicsLightList*)':
src/graphics/gstage.cp:78: error: 'sprintf' was not declared in this scope
src/graphics/gstage.cp: In member function 'void gstage::AddLight(glight*)':
src/graphics/gstage.cp:266: error: 'sprintf' was not declared in this scope
scons: *** [.bld/Polyworld/graphics/gstage.o] Error 1
scons: building terminated because of errors.
make: *** [all] Error 2

```
:mad:

---

### Post by frikker on 2009-12-03
Hello.  Did you ever get this working? Here is what I had to do to get Polyworld working.

To fix your error, go into every file it complains about (in your case src/graphics/gstage.cp) and add the following to the top:
```
#include <stdio.h>
``` It will complain about l5 or 6 files.

After this is fixed, it will complain finally about a char * conversion error.  Go into src/tools/pwtxt/main.cpp and on line 180 change
```
char *name = rindex( path, '/' );
```to
```
const char *name = rindex( path, '/' );
```

---

