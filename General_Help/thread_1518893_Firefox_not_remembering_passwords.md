---
title: "Firefox not remembering passwords"
date: 2010-06-27
forum: General Help
---

### Post by canadianwriterman on 2010-06-27
Just did a clean, fully updated install of Lucid. Unlike the development version I was running, Firefox now will not remember usernames or passwords for sites. I have "Remember passwords for sites" under Preferences checked. Anyone having this experience.

---

### Post by canadianwriterman on 2010-06-27
Problem solved. I deleted .mozilla from the Home directory. Everything works again.

---

### Post by lovinglinux on 2010-06-27
> **canadianwriterman said:**
> Problem solved. I deleted .mozilla from the Home directory. Everything works again.

Next time, just make sure "Passwords" are not selected in the "Clear History" Settings. Although deleting your profile solve many problems, you lose all settings, so I don't like to recommend that solution. Instead you could have deleted only the password files from your profile, which are **key3.db** and **signons.sqlite** or tried to identify the culprit.

For more info about all this stuff see [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)

---

