---
title: "Firefox deletes all cookies, contrary to privacy settings"
date: 2010-09-24
forum: General Help
---

### Post by viktorzk on 2010-09-24
Hello,

Firefox used to work fine, then I played around (only) with privacy settings, and now it deletes all cookies (including ones set to expire in a month) at the end of the session. It is set to "remember history". Moving to a new profile is not an option.

Thanks!

---

### Post by lovinglinux on 2010-09-24
Instead of using Remember History, try the custom settings, making sure to untick "Clear History when Firefox closes" and set cookie policy to keep them until they expire. Also make sure you don't have any websites in the cookies exceptions list.

Additionally, when logging into a web sites, make sure you select the option to keep you connected.

---

### Post by viktorzk on 2010-09-24
Done, no change. I also tried the 'ask me every time' option for cookies, they still get deleted.

I don't know if this is useful, but attached is a screenshot of about:config with the filter 'cookie' (and not showing entries by extensions).

---

### Post by lovinglinux on 2010-09-24
You could close Firefox and move the prefs.js file from your user profile, so another one will be created with default settings when you start Firefox again. Keep in mind this also resets all your extensions settings.

---

