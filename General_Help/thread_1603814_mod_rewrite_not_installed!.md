---
title: "mod_rewrite not installed?!"
date: 2010-10-23
forum: General Help
---

### Post by gigaSproule on 2010-10-23
Hi,

I am trying to get my head around mod_rewrite and every tutorial seems to say that it is installed by default, but it's not installed at all. I have had so many issues with installing Apache it is driving me mad. Ironically everything just works in Ubuntu except the server stuff. Please help!

---

### Post by diesch on 2010-10-23
*mod_rewrite* is installed butnot enabled by default. Use ```
*sudo a2enmod rewrite
```*
to enable it.

*/etc/apache2/mods-available/* contains all the installed modules, */etc/apache2/mods-enabled* symlinks to the enabled ones.

---

### Post by gigaSproule on 2010-10-25
I tried other ways of trying to enable it, but it wasn't working. Thanks though as that seems to have got it working!

Now to just fix mySQL as it won't allow a user to connect to it...

---

