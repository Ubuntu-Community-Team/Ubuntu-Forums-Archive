---
title: "GNOME Commander - default application"
date: 2010-01-04
forum: General Help
---

### Post by Milliways on 2010-01-04
Trying to open a file in GNOME Commander (1.2.7 Ubuntu 9.04) produces the following (not very helpful) error message:-

No default application found for the MIME type application/x-glade.
Open the "File types and programs" page in the Control Center to add one.

Trying to change the default application in Properties by clicking the Change button has no effect (it just changes colour).

The default is set in Nautilus, and works there.

---

### Post by bneven on 2010-01-06
Apparently, this is currently broken in Gnome Commander.
As it says on their documentation page, [http://www.nongnu.org/gcmd/doc.html#mime]("http://www.nongnu.org/gcmd/doc.html#mime") :

> Since GNOME has changed to follow the freedesktop.org standard of handling mimetypes, the editing of preferred programs in GNOME Commander is currently broken (v 1.1.7). We do have this in our TODO file, but until GCMD can handle edititing of preferred programs, there are two other ways of managing this on user basis; use nautilus or manually edit the configuration files that controls mime types in your home directory.

Well, using Nautilus didn't help me, I had a particular mime setting set up and working in Nautilus also, but not in Gnome Commander. Manually editing ~/.local/share/applications/defaults.list fixed this. Check that you have the line in that file that says: 
application/x-glade=[COLOR="Blue"]NAME_OF_YOUR_PREFFERED_APPLICATION[/COLOR].desktop

Look at [http://www.nongnu.org/gcmd/doc.html#mime]("http://www.nongnu.org/gcmd/doc.html#mime") , and for manually editing files look at 
[http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en]("http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en")

---

### Post by Milliways on 2010-01-06
> **bneven said:**
> Apparently, this is currently broken in Gnome Commander.
As it says on their documentation page, [http://www.nongnu.org/gcmd/doc.html#mime]("http://www.nongnu.org/gcmd/doc.html#mime") :



Well, using Nautilus didn't help me, I had a particular mime setting set up and working in Nautilus also, but not in Gnome Commander. Manually editing ~/.local/share/applications/defaults.list fixed this. Check that you have the line in that file that says: 
application/x-glade=[COLOR="Blue"]NAME_OF_YOUR_PREFFERED_APPLICATION[/COLOR].desktop

Look at [http://www.nongnu.org/gcmd/doc.html#mime]("http://www.nongnu.org/gcmd/doc.html#mime") , and for manually editing files look at 
[http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en]("http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en")

Thanks.

There was no defaults.list, so I created one with the following:-
```

[Default Applications]
application/x-glade=glade-3.desktop

```

---

### Post by PotatosFlambe on 2012-06-20
> **Milliways said:**
> Thanks.

There was no defaults.list, so I created one with the following:-
```

[Default Applications]
application/x-glade=glade-3.desktop

```

This discussion was extremely helpful. 

Putting _defaults.list_ in ~/.local/share/applications as instructed by 

*[http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en)*

did not work for me.
I spent quite a while looking for an answer and finally located _defaults.list_ in 

*/usr/local/share/applications*

Editing that file did the trick.

---

### Post by coffeecat on 2012-06-20
Old thread closed.

---

