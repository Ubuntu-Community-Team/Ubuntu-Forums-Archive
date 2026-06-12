---
title: "Installing TCL/TK Ruby Bindings is unsuccessful"
date: 2012-02-23
forum: General Help
---

### Post by Darkness Des on 2012-02-23
I'm working on expanding my knowledge of Ruby to including TCL/TK. Unfortunately, whenever I install the libraries, it does not work as expected. When running IRB to use the TK gem, this the output I get:


```
irb(main):001:0> require 'tk'
RuntimeError: tcltklib: fail to Tk_Init(). Can't find a usable tk.tcl in the following directories: 
    /usr/share/tcltk/tcl8.5/tk8.5 /usr/lib/tk8.5 /usr/local/lib/tcltk/tk8.5 /usr/local/share/tcltk/tk8.5 /usr/lib/tcltk/tk8.5 /usr/share/tcltk/tk8.5 /lib/tk8.5 /usr/library



This probably means that tk wasn't installed properly.

        from /usr/lib/ruby/1.8/tk.rb:1127:in `initialize'
        from /usr/lib/ruby/1.8/tk.rb:1127:in `new'
        from /usr/lib/ruby/1.8/tk.rb:1127
        from (irb):1:in `require'
        from (irb):1
        from :0
irb(main):002:0> 
```

When using "sudo apt-get install libtcltk-ruby1.8" everything goes off without a hitch. I just don't know the issue.

---

### Post by savanna on 2012-02-24
I would do a **dpkg -L libtcltk-ruby1.8** to find all the files installed with **libtcltk-ruby1.8**. See if you can find **tk.tcl** in the files. Then look at what the file **/usr/lib/ruby/1.8/tk.rb** is trying to load.

---

### Post by Darkness Des on 2012-02-24
Alright, I got the list of files that the package installed, but tk.tcl is not in there. As for what tk.rb is trying to load, IRB gives me no error with any of the requirements.

---

