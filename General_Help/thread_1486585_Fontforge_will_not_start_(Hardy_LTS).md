---
title: "Fontforge will not start (Hardy LTS)"
date: 2010-05-18
forum: General Help
---

### Post by Frogbarf on 2010-05-18
Suddenly, Fontforge will not start. The initial splash screen momentarily flashes by but that's it.

Only a week or two ago I was using it to investigate the Damase font, so its malfunction is quite new.

I've tried deleting and reinstalling the app, but that hasn't helped.

Where would the log for fontforge be, if there is one???

What should I look for?

PS: following a suggestion from another forum site, I ran fontforge via terminal, and this is what was displayed:

Copyright (c) 2000-2007 by George Williams.
 Executable based on sources from 02:03 GMT 10-Nov-2007.
Help! Server claimed font
	-bpg-courier-medium-r-normal--13-0-0-0-p-0-iso10646-1
 existed in the font list, but when I asked for it there was nothing.
 I may crash soon.
Segmentation fault

It looks like somewhere in the system there's a reference to BPG_Courier that running sudo fc-cache -f -v didn't clean up after deleting the relevant .ttf file a couple of days ago. But where, oh where is that info hidden???

---

