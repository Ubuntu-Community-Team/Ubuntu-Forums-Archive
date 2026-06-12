---
title: "Opening PDF inside Firefox using Document Viewer"
date: 2011-07-06
forum: General Help
---

### Post by hojjat on 2011-07-06
Since Adobe Reader is very heavy, I don't use it on Ubuntu. That also means I have no way to open PDF inside Firefox. Today I Googled this problem and ran into this link: [http://brainstorm.ubuntu.com/idea/7274/](http://brainstorm.ubuntu.com/idea/7274/)

Some people there mention that one can use mozplugger for that, but I couldn't figure out how. When I checked the /etc/mozpluggerrc file, it seems like it calls Evince Document Viewer like this:
```

repeat noisy swallow(evince) fill needs_xembed: evince "$file"

```

But that opens Evince as a separate application, and not inside Firefox window.

Any advice is appreciated.

---

### Post by hojjat on 2011-07-06
I found my solution after reading this:

[http://ubuntuforums.org/showthread.php?t=25685](http://ubuntuforums.org/showthread.php?t=25685)

The command that calls evince MUST be the first command.

---

### Post by dino99 on 2011-07-06
that should do the trick:

[https://addons.mozilla.org/en-us/firefox/addon/pdf-download/](https://addons.mozilla.org/en-us/firefox/addon/pdf-download/)

---

### Post by hojjat on 2011-07-06
Yeah it does. The only limitation is Evince Document Viewer doesn't give you a way to print the file, when it is opened inside Firefox.

---

