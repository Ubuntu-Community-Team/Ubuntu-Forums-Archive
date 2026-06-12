---
title: "Wrong sound device selected at boot"
date: 2010-07-12
forum: General Help
---

### Post by Foobarb on 2010-07-12
```
$ alsamixer
```Press F6 to select soundcard. 
Result: by default the wrong soundcard is selected. 

If I now select the right sound card, sound works as expected. I want it to be working at boot. 

If I do ```
alsactl store
``` afterwards (which does run without returning any errors).  

Anyone who knows how to select the right soundcard permanently?

---

