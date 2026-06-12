---
title: "gnome-shell 3.4.1/ ubuntu 12.04"
date: 2012-07-30
forum: General Help
---

### Post by alberto00 on 2012-07-30
Hi,
I can't run gnome-shell on my ubuntu 12.04. I'm getting these errors
```
x@iks:~$ gnome-shell
    JS ERROR: !!!   Exception was: Error: Requiring Gtk, version 3.0: Typelib file for namespace 'Gtk', version '3.0' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring Gtk, version 3.0: Typelib file for namespace 'Gtk', version '3.0' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/environment.js:12
"'
    JS ERROR: !!!     message = '"Requiring Gtk, version 3.0: Typelib file for namespace 'Gtk', version '3.0' not found"'
    JS ERROR: !!!   Exception was: Error: Requiring Gtk, version 3.0: Typelib file for namespace 'Gtk', version '3.0' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring Gtk, version 3.0: Typelib file for namespace 'Gtk', version '3.0' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/environment.js:12
"'
    JS ERROR: !!!     message = '"Requiring Gtk, version 3.0: Typelib file for namespace 'Gtk', version '3.0' not found"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring Gtk, version 3.0: Typelib file for namespace 'Gtk', version '3.0' not found
x@iks:~$
```
Everything started after upgrading rhythmbox to 2.97 version, which I built from sources.
Thank you in advance for any advice.

---

### Post by HiImTye on 2012-07-30
library conflicts are common with source builds if you don't know what you're doing. I suggest you stay away from them

---

### Post by Frogs Hair on 2012-07-30
You can install the latest Rythmbox via PPA which will update automatically.  [http://www.webupd8.org/2012/06/rhythmbox-297-released-with-improved.html](http://www.webupd8.org/2012/06/rhythmbox-297-released-with-improved.html)

---

