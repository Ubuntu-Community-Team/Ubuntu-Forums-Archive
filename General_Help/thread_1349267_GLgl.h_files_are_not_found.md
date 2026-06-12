---
title: "GL/gl.h files are not found"
date: 2009-12-08
forum: General Help
---

### Post by ardakshalkar on 2009-12-08
I have Ubuntu 9.10 and I installed qt creator.
I try to learn opengl and I have such an error 
Gl/gl.h files are not found.
I have found thread with similar problems, but that actions did not help me.
Thank you for help!

---

### Post by pbrane on 2009-12-08
Make sure you have **#include <GL/gl.h>** Note the uppercase GL. 
Also make sure you have the necessary dev packages installed. I think libgl1-mesa-dev, libglu1-mesa-dev are two that you need.

---

### Post by Semox78 on 2013-03-07
[COLOR=#000000]2009[/COLOR]
[COLOR=#000000]pbrane,

Thank you so much, the packages were missing. That solved my issue. [/COLOR]:guitar:

Valid for Ubuntu 12.04.2 LTS

Best regards,
Semox78

---

### Post by oldos2er on 2013-03-07
Closed, please don't bump old threads.

---

