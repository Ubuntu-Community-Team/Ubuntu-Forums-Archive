---
title: "Fontmatrix &lt; does anyone know how to use it?"
date: 2010-09-06
forum: General Help
---

### Post by lkejke on 2010-09-06
I installed Fontmatrix, thinking I'd get a straight forward solution for managing fonts.

It's incredibly confusing.

Does anyone use it?

I need help. I went through and de-activated all the fonts. That seemed to work because now my whole system is using one very terrible basic sans font.

Now I want to reactivate selected fonts.

But here's the crazy thing... when I open Fontmatrix, ALL the checkboxes next to ALL the fonts are still/already checked!? How can I "check" them (again) to reactivate them if they are all already checked?

I've been fiddling with this program for a few hours now.

Linux without a good font manager = FAIL!

---

### Post by lkejke on 2010-09-06
Crisis over... sort of!

I have all the fonts reactivated. I un/reinstalled the package and fiddled around with opening/closing the app, rebooting etc.

However, the app is still extremely buggy.

I am starting to go through and setup tags. But it's a tediously long process.

Why isn't there a proper font manager with Ubuntu?

---

### Post by nemoinis on 2010-10-08
Fontmatrix lets you deactivate system fonts but it does not "notice" that they are now deactivated, nor does it let you reactivate them...
To reactivate a font you've accidentally deactivated, you can edit ~/.fonts.conf and remove everything between <rejectfont> and </rejectfont>

---

