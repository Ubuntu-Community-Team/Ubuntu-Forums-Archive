---
title: "How do I open and/or edit .so files?"
date: 2011-10-19
forum: General Help
---

### Post by olain on 2011-10-19
How do I open and/or edit shared library (.so) files? I find them in the /lib/ and /usr/lib/ dirs. I know what they are but I need a gnome editor to edit these files.

---

### Post by Frogs Hair on 2011-10-19
Are looking for Gedit ? It is installed by default .

---

### Post by papibe on 2011-10-19
Those are binary files. You won't be able to open them in any regular text editor. What do you want to do with them?

If you are curious about a particular library, I would advice to get the source code (most of them is available on the repositories).

If you really want to see what's in there, I can see two options: (1) command line:
```
$ od -a /path/to/library | more 
```
or (2) install 'Hex Editor' from the Software Center.

Please note that if you modified a library without knowing what your are doing, you would be compromising the stability of your system.

I hope that helps,
Regards.

---

### Post by olain on 2011-10-19
Thanks.

---

### Post by SeijiSensei on 2011-10-19
You'd be a lot better off looking at the source code for these libraries than mucking around with a hex editor.  If there's something you want to change, edit the source and recompile.  Don't forget to contact the library's maintainers and propose your changes.  That's how open source works.

---

