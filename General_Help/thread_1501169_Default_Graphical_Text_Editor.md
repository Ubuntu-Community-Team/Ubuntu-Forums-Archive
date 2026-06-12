---
title: "Default Graphical Text Editor"
date: 2010-06-04
forum: General Help
---

### Post by Skidbladniir on 2010-06-04
I'm using Thunar, and I would like to know how to change the default text editor.  It's set to emacs (due to a weird install), and I'd like it set to gedit globally.

Thanks

---

### Post by Yellow Pasque on 2010-06-04
Right click a text file, select Open With -> Open With Other Application. Choose gedit and make sure "use as default for this kind of file" is checked.

---

### Post by Skidbladniir on 2010-06-07
I know how to do that - I was just wondering if I could do that to all text files without clicking every type of file...

---

### Post by SlidingHorn on 2010-06-07
> **Skidbladniir said:**
> I know how to do that - I was just wondering if I could do that to all text files without clicking every type of file...

```
sudo apt-get remove emacs
sudo apt-get install gedit
```

?

---

