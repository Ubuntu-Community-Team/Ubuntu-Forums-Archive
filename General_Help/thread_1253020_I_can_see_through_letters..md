---
title: "I can see through letters."
date: 2009-08-29
forum: General Help
---

### Post by DigiTan on 2009-08-29
I'm having this weird issue where fonts on some applications are transparent.  Either I need to cut down on the pills, or it's like some transparent windows effect went slightly awry.  I'm disabling some Compiz features, but nothing sticks out as the smoking gun yet.  Any tips on fixing this?

---

### Post by DigiTan on 2009-09-14
Anything yet?  This isn't really a major issue, but I can "see" it getting out of hand.  Especially with a light background.

---

### Post by philinux on 2009-09-14
Looks like a theme problem. Trying changing to a different theme then back to the one you like.

---

### Post by DigiTan on 2009-09-14
Still no progress yet.  I tried disabling Compiz desktop effects to no avail.  But the funny thing is, I switched to the high-contrast theme for a short time and it made the *window* semi-transparent instead of the lettering.  I feel there's definitely some kind of transparent FX gumming up the works, but I'm not sure where to adjust it.

---

### Post by steveneddy on 2009-09-14
Have you been playing with RGBA stuff recently?

What have you done or installed recently (last two weeks) besides regular updates?

Are you using Murrine theme engines?

Do you have gnome-color-chooser installed?

Have you been messing around in 

**/usr/lib/gtk-2.0/modules**


lately?

post the contents of

/home/[COLOR=Blue]**username**[/COLOR]/.profile

```
gedit /home/username/.profile
```

---

