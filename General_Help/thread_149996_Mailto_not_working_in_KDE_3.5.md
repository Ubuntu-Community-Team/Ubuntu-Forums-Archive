---
title: "Mailto not working in KDE 3.5"
date: 2006-03-25
forum: General Help
---

### Post by Gordonbp531 on 2006-03-25
I've installed KDE 3.5 on top of Ubuntu. I've set my default mail program in User settings, but mailto links on websites just do nothing at all! is there a fix for this?

---

### Post by Gordonbp531 on 2006-03-25
In fact even if I set everything back to the default settings, nothing works.

---

### Post by Barrakketh on 2006-03-25
System Settings -> User Account -> Default Applications

---

### Post by Gordonbp531 on 2006-03-26
[QUOTE=Barrakketh]System Settings -> User Account -> Default Applications[/QUOTE]

Done that - if I set the default mail app to be Kmail, then it all works. if I set the default app to be Thunderbird (say) then after tweaking Firefox in about:config, mailto works in Firefox, but not in Konqueror. Konqueror tries to start up kmail and fails.

---

### Post by Barrakketh on 2006-03-26
[QUOTE=gendibal]Done that - if I set the default mail app to be Kmail, then it all works. if I set the default app to be Thunderbird (say) then after tweaking Firefox in about:config, mailto works in Firefox, but not in Konqueror. Konqueror tries to start up kmail and fails.[/QUOTE]
Could you try "ps -A | egrep -i '^gnome.*' and kill all of the processes you see?  I've notice that if one of those two (I killed them both to make sure) are running, that whenever I open a file in Konqueror it uses the file associations I see in Nautilus.  When they are killed, it goes back to using the ones I see in Konqueror.

---

