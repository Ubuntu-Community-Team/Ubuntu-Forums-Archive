---
title: "Error:     X error: BadShmSeg (invalid shared segment parameter)"
date: 2009-09-24
forum: General Help
---

### Post by bhasi4g on 2009-09-24
I have installed opnet modeler on one of my machine running ubuntu.
Tried to run OPNET modeler from another machine(Ubuntu) using SSH -X user@IP
 OPNET modeler opens up but the graphics is not good..it throws the following error message on the screen
===========================================================================
en
<<< Recoverable Error >>>
  * Time:      09:59:58 Fri Sep 25 2009
  * Product:   modeler (32-bit)
  * Package:   Vg (Virtual Graphics)
  * Function:  vg_x_error_trapper_nonfatal
  * Error:     X error: BadShmSeg (invalid shared segment parameter); serial: 1708; major: 147; minor: 2; resource: 69206200;


<<< Recoverable Error >>>
  * Time:      09:59:58 Fri Sep 25 2009
  * Product:   modeler (32-bit)
  * Package:   Vg (Virtual Graphics)
  * Function:  vg_x_error_trapper_nonfatal
  * Error:     X error: BadAccess (attempt to access private resource denied); serial: 1734; major: 147; minor: 1; resource: 69206169;
========================================================================
I can run MATLAB without any problem though!!

Any help would be greatly appreciated.
Thanks in advance

---

### Post by j_ignacio82 on 2010-02-23
Start opnet using -noxshm parameter, i.e:

[FONT=Lucida Console]opnet -noxshm[/FONT]

This argument indicates opnet to not use share memory. It should be work.

Bye.

---

### Post by rrgalvao on 2010-11-29
> **j_ignacio82 said:**
> Start opnet using -noxshm parameter, i.e:

[FONT=Lucida Console]opnet -noxshm[/FONT]

This argument indicates opnet to not use share memory. It should be work.

Bye.

Excellent, it helped me a lot. Worked for opnet modeler and also for opnet spguru.
Thank you very much!

---

