---
title: "glade with python"
date: 2009-08-17
forum: General Help
---

### Post by krishna1650 on 2009-08-17
hi all, i am making some gui using glade, the output file is in xml format. now i will use python to run the gui application properly. can anyone give some useful links how to do that, i mean the syntax for different buttons, textbox, how to control them in python. i searched the google and found some very simple examples. those examples does not cover all the options. so help me.

thank you.

---

### Post by oldfred on 2009-08-17
the new Glade 3.6 exports in the xml format for use with gtk.builder. Most of the tutorials I found used the older libglade versions.
Some info on builder
builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)
builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
py faqs builder
[http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp](http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp)

---

### Post by krishna1650 on 2009-08-18
> **oldfred said:**
> the new Glade 3.6 exports in the xml format for use with gtk.builder. Most of the tutorials I found used the older libglade versions.
Some info on builder
builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)
builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
py faqs builder
[http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp](http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp)
thank you, for reply. can you tell the difference between libglade and gtkbuilder. and which is better and easy to use?
thank you.

---

### Post by oldfred on 2009-08-18
Builder is the newer way according to this in jan 2008. Note that this was before glade was updated to directly export the builder xml format and then an extra conversion step was required.

[http://www.micahcarrick.com/01-01-2008/gtk-glade-tutorial-part-3.html#2](http://www.micahcarrick.com/01-01-2008/gtk-glade-tutorial-part-3.html#2)

Easy way to get started is to download glade and geany. Create or Copy one of the several demo projects to a new directory. Create/copy a glade file and save in directory. Open geany and create/copy the python code and save in the same directory and then see it execute from within geany. Start with something simple - Hello World and work your way up.

---

