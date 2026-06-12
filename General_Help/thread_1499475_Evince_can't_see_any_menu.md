---
title: "Evince can't see any menu"
date: 2010-06-01
forum: General Help
---

### Post by rolodoom on 2010-06-01
I can't see any menu on Evince. There are no fonts there!!! Below is an attached screenshot.

Here's the code when I call evince from terminal:

```


(evince:5787): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans 9.9990234375'

(evince:5787): Pango-WARNING **: font_face status is: <unknown error status>

(evince:5787): Pango-WARNING **: scaled_font status is: out of memory

(evince:5787): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='DejaVu Sans 9.9990234375', text='&#9679;'

(evince:5787): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans 9.9990234375'

(evince:5787): Pango-WARNING **: font_face status is: <unknown error status>

(evince:5787): Pango-WARNING **: scaled_font status is: out of memory

(evince:5787): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans Oblique 12'

(evince:5787): Pango-WARNING **: font_face status is: <unknown error status>

(evince:5787): Pango-WARNING **: scaled_font status is: out of memory

(evince:5787): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='DejaVu Sans Oblique 12', text='Cargando…'

(evince:5787): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans Oblique 9.9990234375'

(evince:5787): Pango-WARNING **: font_face status is: <unknown error status>

(evince:5787): Pango-WARNING **: scaled_font status is: out of memory

(evince:5787): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans Oblique 9.9990234375'

(evince:5787): Pango-WARNING **: font_face status is: <unknown error status>

(evince:5787): Pango-WARNING **: scaled_font status is: out of memory

(evince:5787): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='DejaVu Sans Oblique 9.9990234375', text='Jovencillo emponzoñado de whisky: ¡qué figurota exhibe!'


```

---

### Post by rolodoom on 2010-10-10
It was a font problem. Deleted non **otf ttf** fonts from .fonts folder and the problem was solved.

---

### Post by Freaky#Funga on 2011-03-13
> **rolodoom said:**
> It was a font problem. Deleted non **otf ttf** fonts from .fonts folder and the problem was solved.

Hi,
I have exactly the same output and ugly output, but I don't even have a .fonts folder in my homedir. Any suggestions? Thanks in advance.

---

