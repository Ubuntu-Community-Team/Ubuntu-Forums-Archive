---
title: "desktop short cut for terminal?"
date: 2011-10-30
forum: General Help
---

### Post by Matrix01 on 2011-10-30
how do u make desktop short cut for terminal?

---

### Post by pretty_whistle on 2011-10-31
Go to Applications>Accessories>Terminal.  Right-click on Terminal and there's an option that says "Add this launcher to desktop"-clicking this will put it on the desktop.

This is in Ubuntu 11.04 classic desktop btw.

---

### Post by mc4man on 2011-10-31
Alternately you could browse here
```
nautilus /usr/share/applications
```

Scroll down to 'Terminal' > r. click > copy & then r. click > paste on the desktop

---

### Post by vat with tux on 2011-10-31
You can use keyboard shortcut "ctr+alt+T"  also to start terminal ...... :)

---

### Post by Matrix01 on 2011-11-04
[ATTACH]206279[/ATTACH]
typed code in terminal,
that did not work?

> **mc4man said:**
> Alternately you could browse here
```
nautilus /usr/share/applications
```Scroll down to 'Terminal' > r. click > copy & then r. click > paste on the desktop

---

### Post by Matrix01 on 2011-11-04
I clicked Applications in launcher,
can't find Accessories.

> **pretty_whistle said:**
> Go to Applications>Accessories>Terminal.  Right-click on Terminal and there's an option that says "Add this launcher to desktop"-clicking this will put it on the desktop.

This is in Ubuntu 11.04 classic desktop btw.

---

### Post by stinkeye on 2011-11-04
Open the dash (top button on launcher)
Start typing  **terminal**.
Drag the terminal icon to your desktop.
Right click on the icon ...properties > permissions and tick the execute box.

P.S If someone gives you a command to run it is better to copy and paste rather than type.
eg
```
nautilus /usr/share/applications
```

is not the same as
```
nautilus/usr/share/applications
```

spaces are important.

---

### Post by Matrix01 on 2011-11-05
[ATTACH]206374[/ATTACH]
clicked top button, and typed terminal,
dragged terminal icon to desktop,
got this message?

[ATTACH]206377[/ATTACH] 
[ATTACH]206376[/ATTACH]
and,
copied code, and pasted it on terminal,
dragged terminal icon to desktop,
got this message.



> **stinkeye said:**
> Open the dash (top button on launcher)
Start typing  **terminal**.
Drag the terminal icon to your desktop.
Right click on the icon ...properties > permissions and tick the execute box.

P.S If someone gives you a command to run it is better to copy and paste rather than type.
eg
```
nautilus /usr/share/applications
```is not the same as
```
nautilus/usr/share/applications
```spaces are important.

---

### Post by stinkeye on 2011-11-05
Not sure what your doing but try this.
Open a terminal and enter
```
nautilus /usr/share/applications
```

This should open the file browser at that location.
Find the item named "Terminal".
Right click on it and choose **Copyto > Desktop**

---

