---
title: "Synergy and the UK £ (pound) sign"
date: 2009-09-15
forum: General Help
---

### Post by Another Monkey on 2009-09-15
I use Synergy between Windows XP and Ubuntu 9.04.  The XP box is the Synergy server and Ubuntu is the client.

It works pretty well right from the login and I even got the whole &#937;/@ (omega/at) issue resolved.  But try as I might I cannot figure out how to get the UK pound sign (£) to work.

I am using a UK keyboard, all the regional settings on XP and Ubuntu are UK, but when I try to use the £ key (Shift-3) I get nothing.

Has anyone got this working or know how to resolve it?  I'm not even sure how to find out if the keypress is getting passed to Ubuntu.

Synergy is a great tool, shame that development appears to have stopped.

---

### Post by Another Monkey on 2009-10-22
The problem seems to be intermittent, but since moving to Synergy+ 1.3.4 I have not seen it.
That also seems to fix the whole @/omega thing too (no need for the hack):
```
echo keycode 24 = q Q at at at at | xmodmap -
```

---

