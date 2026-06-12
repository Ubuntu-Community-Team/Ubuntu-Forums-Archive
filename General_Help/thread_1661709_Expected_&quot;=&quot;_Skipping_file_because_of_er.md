---
title: "Expected: &quot;=&quot; Skipping file because of errors...(what is this output means?)"
date: 2011-01-07
forum: General Help
---

### Post by maizuddin35 on 2011-01-07
Hello guys. I need to know what is this, and maybe I can fix it, or you guys can help me with this thing.

```
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
In file "/usr/share/menu/plymouth-manager", at (or in the definition that ends at) line 4:
?package(plymouth-manager):needs="X11" section "Applications/System/Administration" title="Plymouth Manager" command="/usr/bin/plymouth-manager.gambas" icon="/usr/share/pixmaps/plymouth-manager.png"
                                               ^
Expected: "="
Skipping file because of errors...
/usr/share/menu/mars: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/mars generated no output or returned an error.
Processing triggers for python-support ...
Setting up libmowgli2 (0.7.0-2) ...
Setting up libaudcore1 (2.4.0-0ubuntu3) ...
Setting up libbinio1ldbl (1.4-14) ...
Setting up libcue1 (1.4.0-1) ...
Setting up liblash3 (0.6.0~rc2-1ubuntu2) ...
Setting up libfluidsynth1 (1.1.2-2) ...
Setting up libmcs1 (0.7.1-1build1) ...
Setting up libresid-builder0c2a (2.1.1-8) ...
Setting up libsidplay2 (2.1.1-8) ...
Setting up audacious-plugins (2.4.0-0ubuntu3) ...
Setting up libaudclient2 (2.4.0-0ubuntu3) ...
Setting up audacious (2.4.0-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
In file "/usr/share/menu/plymouth-manager", at (or in the definition that ends at) line 4:
?package(plymouth-manager):needs="X11" section "Applications/System/Administration" title="Plymouth Manager" command="/usr/bin/plymouth-manager.gambas" icon="/usr/share/pixmaps/plymouth-manager.png"
                                               ^
Expected: "="
Skipping file because of errors...
/usr/share/menu/mars: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/mars generated no output or returned an error.
adib@maizuddin35:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

there is this,
 ```

In file "/usr/share/menu/plymouth-manager", at (or in the definition that ends at) line 4:
?package(plymouth-manager):needs="X11" section  "Applications/System/Administration" title="Plymouth Manager"  command="/usr/bin/plymouth-manager.gambas"  icon="/usr/share/pixmaps/plymouth-manager.png"
                                               ^
Expected: "="
Skipping file because of errors...
/usr/share/menu/mars: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/mars generated no output or returned an error.
```

Clearly I don't understand what the problem.can anyone?

---

### Post by dandnsmith on 2011-01-07
The first error (in plymouth-manager) says there is '=' missing between 'section' and "Application...
If you look in other items in /usr/share/menu you'll be able to see the format.

The second error (in mars) may be simple, but I don't see that in my directory, so, lacking full context, cannot comment further.

---

### Post by maizuddin35 on 2011-01-07
what do you think , that I need to do ?

---

### Post by dandnsmith on 2011-01-07
Edit the files, and rerun whatever caused it - some sort of update?
Might just be something which gets done on bootup

---

### Post by FlameReaper on 2011-01-16
```
?package(plymouth-manager):needs="X11" section[COLOR="Red"]**=**[/COLOR]"Applications/System/Administration" title="Plymouth Manager"  command="/usr/bin/plymouth-manager.gambas"  icon="/usr/share/pixmaps/plymouth-manager.png"
```

Do the above edit and I suppose everything will go fine.

---

### Post by maizuddin35 on 2011-01-16
can you explain what doest that command/code means? Later Ill get back to my computer and try it out

---

### Post by FlameReaper on 2011-01-16
Nothing much. Just that the line 4 contained in "/usr/share/menu/plymouth-manager" where after "section" is missing a "=". That's there to it. Basically, nothing is assigned to "section" making it unable to work properly.

More like a definitions file semantics problem. Or, like, it's as if you typed a comma at the end of a line in a C source file instead of a semicolon, where the source code fails to compile because of that.

---

