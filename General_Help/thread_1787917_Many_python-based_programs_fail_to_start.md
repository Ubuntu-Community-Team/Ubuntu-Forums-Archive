---
title: "Many python-based programs fail to start"
date: 2011-06-21
forum: General Help
---

### Post by yanom on 2011-06-21
Many programs based on python (example here is the **burn** command-line disk burning program) crash on startup with errors similar to this one:

```
 File "<string>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/burnlib/burn.py", line 654, in main
    prog_intro()
  File "/usr/lib/pymodules/python2.7/burnlib/burn.py", line 156, in prog_intro
    if config.getboolean('general', 'ask_root'):
  File "/usr/lib/python2.7/ConfigParser.py", line 360, in getboolean
    v = self.get(section, option)
  File "/usr/lib/python2.7/ConfigParser.py", line 599, in get
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'general' 
```

It appears to be searching for some missing Python libraries or something.

---

### Post by yanom on 2011-06-21
anyone know how to fix this?

---

### Post by papillion on 2011-06-21
Have you reported it to the devs? Many times, it's a pretty quick fix for them.

---

### Post by Kylotan on 2011-06-22
Doesn't look like a Python specific problem to me - looks like data missing from a configuration file, or the whole file being missing.

---

### Post by gmargo on 2011-06-22
It's a program bug.

See **/usr/share/pyshared/burnlib/burn.py**.  If you run **burn** with no arguments, then on line 654, the prog_intro() function is called, which relies on configuration information.  However, that config info is not loaded until line 658.

Apply this patch to remove the call to prog_intro():
```

  $ diff -u `pwd`/burn.py.00 `pwd`/burn.py
--- /usr/share/pyshared/burnlib/burn.py.00      2009-12-22 03:58:01.000000000 -0800
+++ /usr/share/pyshared/burnlib/burn.py 2011-06-22 09:06:35.708510617 -0700
@@ -651,7 +651,7 @@
     if len(sys.argv) > 1:
         check_main_option(sys.argv[1])
     else:
-        prog_intro()
+        #prog_intro()
         parser.print_help()
         sys.exit()
 


```

---

### Post by yanom on 2011-06-23
> **gmargo said:**
> 
Apply this patch to remove the call to prog_intro():
```

  $ diff -u `pwd`/burn.py.00 `pwd`/burn.py
--- /usr/share/pyshared/burnlib/burn.py.00      2009-12-22 03:58:01.000000000 -0800
+++ /usr/share/pyshared/burnlib/burn.py 2011-06-22 09:06:35.708510617 -0700
@@ -651,7 +651,7 @@
     if len(sys.argv) > 1:
         check_main_option(sys.argv[1])
     else:
-        prog_intro()
+        #prog_intro()
         parser.print_help()
         sys.exit()
 


```

how do I apply that patch?

Copying it into the terminal (as a whole or line-by-line) doesn't work.

---

### Post by gmargo on 2011-06-23
Well, I shouldn't have used the patch (aka "diff") format for that simple a difference.
I originally had a more complicated patch, but afterwards found this simpler one.

If you supply appropriate arguments to the **burn** command, then you do not
need to edit anything.  This patch just covers the one oddball case that the original
authors missed.  

To apply the patch "by hand", just edit the file /usr/share/pyshared/burnlib/burn.py and comment out that one  line (approx line 654).

---

