---
title: "Amarok isn't reporting to last.fm"
date: 2009-09-29
forum: General Help
---

### Post by Vunutus on 2009-09-29
I plugged in my account details and all, and I know they are valid. I can stream from my last.fm feeds just fine, but nothing I play in my local library gets reported.

I have checked the "submit tracks" option in the last.fm settings.

If I run amarok from a terminal and hit "test connection", the following error pops up:

```
amarok(14296) KNetworkReply::setMimeType: "text/xml"
":"
  QUrl( "" )
 "<?xml version="1.0" encoding="utf-8"?>
<lfm status="failed">
<error code="13">Invalid method signature supplied</error></lfm>"

```

How can I fix this? Last.fm doesn't really do me any good if I can't report plays =/

---

### Post by Vunutus on 2009-10-01
Bump.

---

### Post by CatKiller on 2009-10-01
Enable the backports repository and update your version of Amarok. The version that shipped with Jaunty had broken scrobbling.

---

### Post by Vunutus on 2009-10-01
Thanks, that seems to have worked! It also fixed a great deal of other bugs that were burning me. This version is a lot better :D

---

