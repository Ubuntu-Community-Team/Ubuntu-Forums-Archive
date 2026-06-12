---
title: "Can't copy-and-paste via GUI but I can via CLI?"
date: 2012-09-14
forum: General Help
---

### Post by t0p on 2012-09-14
_Pretty m_uch what it says in the title.  I try to cut (or copy) and paste a file from one place to another (eg. family-guy-s08e03.mp4 from Home to ~/Videos/Family Guy/ but when I right-click in the Family Guy folder, the Paste command is greyed-out.  But if I do it in Terminal,

```
t0p@mars:~$ mv family-guy-s08e03.mp4 Videos/Family\ Guy/
```there's no problem at all, the file goes where it's been told to go.  What's up with this?

---

### Post by vasa1 on 2012-09-14
> **t0p said:**
>   What's up with this?
WFM with Thunar (Xfce 4.10). Which file manager is being used?

---

### Post by t0p on 2012-09-14
> **vasa1 said:**
> WFM with Thunar (Xfce 4.10). Which file manager is being used?

Oh wonderful non-answer answer.

I'm usually using nautilus nautilus.  I didn't post this to start a pissing competition: all I want is to copy-paste.. Plz, plz,anyone gotta fix?  I got 5 years experience, but the slightest clue may help.

---

### Post by LewisTM on 2012-09-14
Could you be affected by this [bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/882307")?
Apparently others suffer from the same greying of the Paste item, which is still clickable.

---

### Post by t0p on 2012-09-14
> **LewisTM said:**
> Could you be affected by this [bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/882307")?
Apparently others suffer from the same greying of the Paste item, which is still clickable.

Aha!  You have saved me from much mystery!  Paste is greyed-out but is still clickable.  I wonder how long it would've tried right-clicking etc before I figured it out myself?

Thanks, LewisTM!!!   :)

---

### Post by hakermania on 2012-09-14
Nice to see this being mentioned. I am ashamed to say that I was kind of bored to go check if this bug has been reported because I knew that somebody would have already done it :P

---

