---
title: "GTK + Mono on 9.10 - gtk-sharp"
date: 2010-02-07
forum: General Help
---

### Post by eznet on 2010-02-07
When using the Repo's "CLI binding for the GTK+ toolkit 2.12", I was getting the following:

```

$ gmcs Welcome.cs
Welcome.cs(2,7): error CS0246: The type or namespace name `Gtk' could not be found. Are you missing a using directive or an assembly reference?
    Try using -pkg:gtk-sharp
Compilation failed: 1 error(s), 0 warnings

$ gmcs -pkg:gtk-sharp Welcome.cs
Package gtk-sharp was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk-sharp.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk-sharp' found
error CS8027: Error running pkg-config. Check the above output.

```

So, I got to thinking...
```

$ locate gtk-sharp-2.0.pc
/usr/lib/pkgconfig/gtk-sharp-2.0.pc

```

And wondered...
```

$ sudo ln -s /usr/lib/pkgconfig/gtk-sharp-2.0.pc /usr/lib/pkgconfig/gtk-sharp.pc

```

And all was well in the world...

Hope this helps someone... Or me, if I encounter this error again...

Matt

---

