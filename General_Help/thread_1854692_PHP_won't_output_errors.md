---
title: "PHP won't output errors"
date: 2011-10-04
forum: General Help
---

### Post by SlaughterDog on 2011-10-04
So I've got Apache and PHP installed for development testing, and despite having php's error reporting enabled in the php.ini file, I'm not getting any error output.

I figured I'd post this here since my PHP install came from the Ubuntu repositories, and I noticed error reporting was set to Off, despite the PHP default of it being on.

Is there anything that I might be overlooking?

---

### Post by 4llf0rn0t on 2011-10-04
Hi,

Have you tried ```
display_errors = On
```>

---

### Post by SlaughterDog on 2011-10-05
> **4llf0rn0t said:**
> Hi,

Have you tried ```
display_errors = On
```>

Yup, that's how I tried to turn them on.

---

