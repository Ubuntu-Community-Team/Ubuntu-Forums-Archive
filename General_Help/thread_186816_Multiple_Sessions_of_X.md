---
title: "Multiple Sessions of X"
date: 2006-06-02
forum: General Help
---

### Post by leetcharmer on 2006-06-02
Can I have multiple sessions of X running, each with it's own Desktop Manager?

I wanna have F7 take me to standard Ubuntu, F2 take me to Xubuntu.  Know how I can make this a reality?

---

### Post by garyng on 2006-06-02
My quick and dirty solution would be just Ctrl-Alt-F2, login then "X --query localhost" which should give you another GDM login screen where you can choose the WM.

---

### Post by leetcharmer on 2006-06-02
it still says server is already active for display 0 :/

also
> Fatal server error:
Unrecognized option: --query

---

### Post by garyng on 2006-06-02
ah, try "X :1" then.

---

