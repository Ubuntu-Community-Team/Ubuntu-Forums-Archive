---
title: "Chromium cannot determine or set default browser."
date: 2010-05-18
forum: General Help
---

### Post by casbahdk on 2010-05-18
I have been experiencing a problem with Thunderbird links not opening Chromium, so I checked the options. This message is in red under the basics --> default browser area:
> Chromium cannot determine or set default browser.
Does anyone know what is going on?

---

### Post by garvinrick4 on 2010-05-18
My Chromium looks the same way as yours and I have Firefox set as default. I have a key command set to open browser (non-specific) and it opens Firefox every time. I would not worry about it at all that seems to be Chromiums default settings. Have a nice day.

---

### Post by DrKenobi on 2010-05-18
> **casbahdk said:**
> I have been experiencing a problem with Thunderbird links not opening Chromium, so I checked the options. This message is in red under the basics --> default browser area:

Does anyone know what is going on?

Try going to Preferred Application, and choose Custom on write this:

> /usr/lib/chromium-browser/chromium-browser %s

This is how i set in my Ubuntu

---

### Post by casbahdk on 2010-05-19
Cheers Dr. This doesn't stick. The system forgets the setting as soon as I click "ok". If I open the custom section again, the field is blank :(

---

