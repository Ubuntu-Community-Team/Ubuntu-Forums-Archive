---
title: "firefox bug"
date: 2012-06-14
forum: General Help
---

### Post by qwertyjjj on 2012-06-14
My FF seems to have lost all the bookmarks.
The hover hand does not show up anymore either on links and all links show up in black instead of blue.
Any ideas how I can restore the original profile>?

---

### Post by kanikilu on 2012-06-14
Try creating a new profile, or starting up in safe-mode:
```
firefox -P
```
```
firefox --safe-mode
```
As a last resort, maybe try reinstalling the Firefox package?

---

### Post by qwertyjjj on 2012-06-16
I had to delete the sqlite files in the profile and restart to get everything back.

---

