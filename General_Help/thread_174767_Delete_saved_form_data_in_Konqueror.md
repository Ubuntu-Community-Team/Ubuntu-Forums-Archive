---
title: "Delete saved form data in Konqueror?"
date: 2006-05-12
forum: General Help
---

### Post by Dryer Lint on 2006-05-12
I searched for a while now and couldn't find how to do this.

I wouldn't mind, but Konqueror has been remembering two typo-login attempts from myself to my mail account for MONTHS now and I always have to skip over them when I use the auto-completion.

---

### Post by sinkxdie on 2006-05-12
I think you have to delete them from the little wallet icon in your system tray.

EDIT: Yeah, click on the wallet icon, expand "maps" and then delete the site with the bad password.

---

### Post by Dryer Lint on 2006-05-12
That's not it, I accidentally pressed enter before entering my password, nothing got saved in the KWallet.

I mean regular form data, like the search strings I used on this forum for example, those are all saved, too.

---

### Post by sinkxdie on 2006-05-12
I don't know if thats possible, I mean it probably is, but there isn't any autocomplete or roboform or whatever I used to use on Windows.

---

### Post by sinkxdie on 2006-05-12
Ok i got it.
Go to Settings>Configure Konqueror>Web Behaviror
And then uncheck the box that says, "form completion"

---

### Post by Dryer Lint on 2006-05-12
Yes! Deactivating, applying and then reactivating it worked, it seems! :D

Thank you very much!

---

### Post by Dryer Lint on 2006-05-13
Update: False alarm, it didn't work!

After restarting Konqueror, all my old form data is back. :S

---

### Post by Neo Ex on 2006-05-13
KControl -> Security and Privacy -> Privacy -> check Form field filling (or something like that :p ) -> Clean.

---

### Post by trotski on 2006-05-13
Try clearing the cache and messing with the cache settings under Settings>Configure Konqueror>Cache

---

### Post by Dryer Lint on 2006-05-15
Thank you!

Deleting the form data from the kcontrol applet worked.

---

### Post by excalq on 2008-05-29
Another thing you can do is right click on the specific form input box that has the autocomplete history you want to clear, and choose "Clear History"

---

