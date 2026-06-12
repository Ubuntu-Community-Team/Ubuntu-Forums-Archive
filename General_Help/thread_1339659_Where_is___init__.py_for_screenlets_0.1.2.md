---
title: "Where is __init__.py for screenlets 0.1.2"
date: 2009-11-27
forum: General Help
---

### Post by simartem on 2009-11-27
i am using ubuntu 9.10
I have installed screenlets 0.1.2
The screenlets disappear when i click "show desktop" button. 
I am looking for the file __init__.py to edit some settings but i cant find the related file. Where is it located ?

---

### Post by simartem on 2009-11-27
i have found the file in the following directory : 
[B]
/usr/share/pyshared/screenlets[/B]

And with the following method, the screenlets aren't dissapearing, it has solved the problem, Quote from the following link : (message #16) [https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/217507](https://bugs.launchpad.net/ubuntu/+source/screenlets/+bug/217507)

```


           I'm using Ubuntu Intrepid (gnome) with screenlets version 0.1.2.
 I edited __init__.py and replaced the line
 self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_TOOLBAR)
 with
 self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK)
 As stated earlier this fixed the problem with the screenlets disappearing but the wierd thing is; the screenlets are still movable!
 So far I have found nothing broken - maybe this should be a permanent change?



        

```

Works for me..

---

