---
title: "Emacs colours"
date: 2006-02-03
forum: General Help
---

### Post by Fjodor on 2006-02-03
After installing emacs-extra and some modes, the background colour is now suddenly black with white text. Does anyone know how to make it black on white again?

---

### Post by thermans on 2006-02-03
Looks like it's definitely coming from the "emacs-extra" package.  From the startup file:

  ```
 '(default ((t (:foreground "white"))))
  '(default ((t (:background "black"))))
```

There are a couple of things you can do:

1. Remove "emacs-extra".

2. Override the colours to what you want by doing:

```
M-x customize-face <default>
```
And setting the foreground and background colours.

My recommendation would be the first one.  It's pretty sloppy for a package to be making assumptions about your environment and changing them willy-nilly.

What functionality were you looking for from "emacs-extra"?

---

### Post by Fjodor on 2006-02-03
Not much really. I just thought it might give emacs some extra oomph. Or something. Didn't really think further than "if I have this installed, I might get something out of it. Can't hurt...". Obviously it could...

Thanks for the suggestions

---

### Post by spetey on 2006-02-06
Thanks for this thread, I had the same trouble, and for the same reason.

Let me just add here the phrase 'emacs colors', since I didn't find this thread the first time around with my Americentric spelling.  *Emacs colors!*

;)
spetey

---

### Post by annsachd on 2006-02-06
Thanks for posting this. I was going through much the same thing with it.

Also interesting about the different spellings of colors hindering your search. It would be cool if the search would take that into account.

I'll add one: kolors.

---

