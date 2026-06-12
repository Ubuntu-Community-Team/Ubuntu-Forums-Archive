---
title: "Firefox Tab restore"
date: 2011-10-01
forum: General Help
---

### Post by Iksf on 2011-10-01
Ok basically any time i open firefox it opens all my previous tabs, and its a pain in the ahole. Iv gone through the settings and theres been nothing there, iv changed the about:config session restore key, does nothing, any help?

---

### Post by sanderd17 on 2011-10-01
tried this?

---

### Post by Iksf on 2011-10-01
Yup :(

---

### Post by sanderd17 on 2011-10-01
Hmm,

are you willing to delete your firefox profile? This will remove all saved passwords, the complete history, favourites and add-ons. You can probably backup most of those before you delete your profile.

To delete your profile, close firefox and execute
```

mv ~/.mozilla/firefox ~/.mozilla/firefox.backup

```

---

### Post by Iksf on 2011-10-02
Awesome worked thx man

---

### Post by lovinglinux on 2011-10-04
> **sanderd17 said:**
> Hmm,

are you willing to delete your firefox profile? This will remove all saved passwords, the complete history, favourites and add-ons. You can probably backup most of those before you delete your profile.

To delete your profile, close firefox and execute
```

mv ~/.mozilla/firefox ~/.mozilla/firefox.backup

```

Instead of recommending deleting the entire profile, I would suggest deleting *prefs.js* file. Most likely that the problem would be solved by doing that.

---

### Post by sanderd17 on 2011-10-04
Thanks for the tip.

@OP: I didn't completely removed your profile, if you want to get it back, just ask.

---

