---
title: "Wine Problems"
date: 2006-04-04
forum: General Help
---

### Post by h3llfyr3 on 2006-04-04
Hi all,
My app runs just fine under wine but i get a few messages like

fixme:keyboard:RegisterHotKey (0x20026,110,0x00000003,72): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:keyboard:UnregisterHotKey (0x20026,110): stub

What is causing the errors, presumably wrong versions of DLL's or registry issues.
Can anyone give me a starting point?
This place is just much more easy to get on with than winehq ;)

Many thanks
-H

---

### Post by dcstar on 2006-04-04
[QUOTE=h3llfyr3]Hi all,
My app runs just fine under wine but i get a few messages like

fixme:keyboard:RegisterHotKey (0x20026,110,0x00000003,72): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:keyboard:UnregisterHotKey (0x20026,110): stub

What is causing the errors, presumably wrong versions of DLL's or registry issues.
Can anyone give me a starting point?
This place is just much more easy to get on with than winehq ;)

Many thanks
-H[/QUOTE]
They are not "errors", they look like messages about Wine functions that haven't been fully implemented yet.

If your application works, why concern yourself about messages that you probably wouldn't even be aware of if you didn't launch it in a terminal?

---

### Post by justleen on 2006-04-04
seems perfectly normal to me.. .in my experience you will always get "errors"like that.. 

Solution: dont run it in a terminal :)

---

