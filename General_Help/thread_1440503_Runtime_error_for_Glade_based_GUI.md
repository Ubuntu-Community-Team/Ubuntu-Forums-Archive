---
title: "Runtime error for Glade based GUI"
date: 2010-03-27
forum: General Help
---

### Post by miak on 2010-03-27
I'm trying to write a GUI using Glade and pyGtk. I had a problem so decided to go back and start from a helloWorld, but I still have a problem.
here is my code for the program
```

#!/usr/bin/env python

import sys
try:
    import pygtk
    pygtk.require("2.0")
except:
    pass
try:
    import gtk
    import gtk.glade
except:
    sys.exit(1)

class HellowWorldGTK:
    """This is an Hello World GTK application"""

    def __init__(self):
        
        #Set the Glade file
        self.gladefile = "pyhelloworld.glade"  
            self.wTree = gtk.glade.XML( "pyhelloworld.glade") 
        
        #Create our dictionay and connect it
        dic = { "on_btnHelloWorld_clicked" : self.btnHelloWorld_clicked,
            "on_window1_destroy" : gtk.main_quit }
        self.wTree.signal_autoconnect(dic)

    def btnHelloWorld_clicked(self, widget):
        print "Hello World!"


if __name__ == "__main__":
    hwg = HellowWorldGTK()
    gtk.main()

```Couldn't attach .glade file(Getting Invalid File Error)

When I run the python file I get following error message:
```

(pyhelloworld.py:2489): libglade-WARNING **: Expected <glade-interface>.  Got <interface>.

(pyhelloworld.py:2489): libglade-WARNING **: did not finish in PARSER_FINISH state
Traceback (most recent call last):
  File "./pyhelloworld.py", line 34, in <module>
    hwg = HellowWorldGTK()
  File "./pyhelloworld.py", line 22, in __init__
    self.wTree = gtk.glade.XML( "pyhelloworld.glade") 
RuntimeError: could not create GladeXML object

```

Can anyone help with this? Or give me a sample program that works(including .glade file). You can send the file(s) to [email]mamikonyana@yahoo.com[/email].

Thanks,
miak

---

### Post by oldfred on 2010-03-27
I am  self taught so I do not know if this is good or not but I got it to load. I do not know if button works since I created my own glade file.

```

#!/usr/bin/env python

import sys
try:
    import pygtk
    pygtk.require("2.0")
except:
    pass
try:
    import gtk
    import gtk.glade
except:
    sys.exit(1)

class HellowWorldGTK:
    """This is an Hello World GTK application"""
    
    def on_window1_destroy(self, widget, data=None):
        DBclose()
        gtk.main_quit()

    def __init__(self):
        try:
            self.builder = gtk.Builder()
            self.builder.add_from_file("pyhelloworld.glade")
        except:
            self.show_error_dlg("Failed to load UI XML file: pyhelloworld.glade")
            sys.exit(1)
            
        #Set the Glade file
        #self.gladefile = "pyhelloworld.glade"  
        #self.wTree = gtk.glade.XML( "pyhelloworld.glade")
        self.window = self.builder.get_object("window1")
        self.btnHelloWorld = self.builder.get_object("btnHelloWorld")
        #Create our dictionay and connect it
        #dic = { "on_btnHelloWorld_clicked" : self.btnHelloWorld_clicked,
           # "on_window1_destroy" : gtk.main_quit }
        #self.wTree.signal_autoconnect(dic)
        self.builder.connect_signals(self)

    def on_btnHelloWorld_clicked(self, button):
        print "Hello World!"
        
        # Run main application window
    def main(self):
        #self.window.maximize()
        self.window.show()
        gtk.main()


if __name__ == "__main__":
    hwg = HellowWorldGTK()
    gtk.main()

```

---

### Post by miak on 2010-03-28
It seems to work, but when I run the program from terminal no error message is displayed or anything like it, and program keeps running as it is supposed to do, but I don't see any window at all. Any ideas?

miak

---

### Post by oldfred on 2010-03-28
Half the time I spent trying to get mine to work was the same issue. It ran with no error but no window. I had forgotten that the default in glade for many things is hidden and had change the window setting to show. My default window also was tiny, it I was using it I would change default sizes and location. I would also create a location text box or other to write the message, I think it will only show on the terminal not in the window.

---

### Post by miak on 2010-03-28
I still don't know what was the problem, but I got another template from internet and it seems to be working. I don't know what was wrong with the code you gave me(maybe it didn't suit my .glade file or something else), but my code was incomplete that was the main problem and i had a syntax error too. 
Thank you very much for you time
Best,
miak

---

### Post by Tony Flury on 2010-03-28
In future - if you have programming question like this, you will get more targetted assistance in the Programming Talk forum.

I am glad you got it solved though.

---

### Post by jcr1 on 2010-04-22
Hi,

I am currently just starting to try and learn to use Glade to build simple apps and I am too running into exactly the same problem. If I set my project to GTKBuilder, I get the RuntimeError: could not create GladeXML object, if I set it to libglade, it seems to run but nothing appears.

Not sure where my problem is but could it be to do with using self.gladefile rather than self.builder?

There seems to be many different ways and not many obvious examples that all point to a common way of doing things.

Thanks for any feedback.

---

### Post by oldfred on 2010-04-22
Just as I was starting a year or two ago they were converting to builder, so I have done everything with builder as it was my understanding that it was the future.

Glade does not set visible as a default, so you need to check your main window to see if it is visible.

I liked using geany as I can paste code into it, save it with .py and it knows it a python program.  I can then run it and see error messages. It does not have a debugger but it is not difficult to add print of variables into the program to track a variable.

---

