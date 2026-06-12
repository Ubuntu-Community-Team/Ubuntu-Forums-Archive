---
title: "Gnome-Shell Issue"
date: 2010-04-05
forum: General Help
---

### Post by joeknoodle on 2010-04-05
Trying to install/run Gnome-Shell in Karmic, I get the following error:

```

joe@joe-desktop:~$ gnome-shell --replace
    JS ERROR: !!!   Exception was: Error: Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded")@:0
("Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:11
'
    JS ERROR: !!!     message = 'Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded'
    JS ERROR: !!!   Exception was: Error: Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded")@:0
("Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:11
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
@<main>:1
'
    JS ERROR: !!!     message = 'Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring Shell, version none: Requiring namespace 'Meta' version '2.28', but '2.29' is already loaded
joe@joe-desktop:~$ Cannot register the panel shell: there is already one running.

```Huh?

---

