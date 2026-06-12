---
title: "Netbeans load errors after upgrade"
date: 2010-05-22
forum: General Help
---

### Post by edpatterson on 2010-05-22
I am receiving a ton of errors when loading netbeans 6.8 on my Ubuntu 10.4 machine.
```

Warning - could not install some modules: 
Java Debugger - None of the modules providing the capability org.netbeans.api.debugger.jpda.JPDADebuggerEngineImpl could be installed. 
Java Debugger - None of the modules providing the capability org.netbeans.spi.debugger.ui could be installed. 
IDE Platform - The module named org.netbeans.modules.editor.macros/0-1 was needed and not found. 
IDE Platform - The module named org.netbeans.modules.parsing.api was needed and not found. 
Editor Library 2 - None of the modules providing the capability org.netbeans.modules.editor.actions could be installed. 
Editor Library 2 - The module UI Utilities API was requested in version >= 7.17 but only 7.8.2.1 was found. 
HTML Editor - The module named org.netbeans.modules.editor.bracesmatching/0-1 was needed and not found. 
Common Scripting Language API (new) - The module named org.netbeans.spi.editor.hints/0-1 was needed and not found. 
Editor Code Templates - The module named org.netbeans.spi.editor.hints/0-1 was needed and not found. 
Ant - The module I/O APIs was requested in version >= 1.18 but only 1.16.2 was found. 
CSS Editor - The module named org.netbeans.modules.editor.bracesmatching/0-1 was needed and not found. 
...
many many more

```
I tried marking for reinstall and applying in the package manager, no joy.

Thanks for any help
Ed

---

### Post by nead on 2010-05-25
I have the exact same problem. Tried purging then reinstalling with downloaded file, but the problem is still here. Did you make any progress?

---

### Post by edpatterson on 2010-05-25
No, I completely removed all the packages, and reinstalled. Nothing but errors.

Ed

---

### Post by Mr Fredrick on 2010-05-30
I'm also have this problem, has anybody fixed it?

---

