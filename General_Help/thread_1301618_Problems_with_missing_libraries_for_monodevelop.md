---
title: "Problems with missing libraries for monodevelop"
date: 2009-10-26
forum: General Help
---

### Post by hamdev on 2009-10-26
I am trying to develop a Gtk# based application in monodevelop 2.0.0. As soon as I add:

```
	using( Graphics g = Gtk.DotNet.Graphics.FromDrawable(args.Event.Window) )
        {
         ...
        }
```

and attempt to build the project, I get the following errors:

cannot find metafile '/usr/lib/monodevelop/AddIns/NUnit/MonoDevelop.NUnit.dll'(CS0006)
cannot find metafile '/usr/lib/monodevelop/Addins/VersionControl/MonoDevelop.VersionControl.dll'(CS0006)

There is no /usr/lib/monodevelop directory on my system. What package or packages do I have to install to get them?

I am using Ubuntu 9.04.

---

