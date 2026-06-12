---
title: "minimize, resize and close button question"
date: 2009-10-29
forum: General Help
---

### Post by aaronmarsh632 on 2009-10-29
Hi,

I have been using ubuntu for a few years now but i still prefer these buttons on the other side like the mac. how can i change these?

and not to be rude but i dont want to hear that every1 else thinks its better so your not telling me or anything like that (this is just aimed at certain people so dont take it personally)

so if its possible and someone knows how, i would appreciate your help.

thanks

---

### Post by mcduck on 2009-10-29
Yes, it's possible.

Press Alt-F2 and run "gconf-editor" (or do the same in a terminal). Then use that to browse to apps/metacity/general and find the "button_layout" -key. Change it's value to "close,minimize,maximize:menu" and the buttons are now arranged as they are on OSX. :)

---

### Post by aaronmarsh632 on 2009-10-29
> **mcduck said:**
> Yes, it's possible.

Press Alt-F2 and run "gconf-editor" (or do the same in a terminal). Then use that to browse to apps/metacity/general and find the "button_layout" -key. Change it's value to "close,minimize,maximize:menu" and the buttons are now arranged as they are on OSX. :)

Thank you so much for your help. Perfect

---

### Post by mcduck on 2009-10-29
You're welcome. It's always nice when there's a really simple solution to some problem. :)

---

