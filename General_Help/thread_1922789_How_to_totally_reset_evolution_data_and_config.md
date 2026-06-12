---
title: "How to totally reset evolution data and config?"
date: 2012-02-09
forum: General Help
---

### Post by CaptSaltyJack on 2012-02-09
What's the best way to totally restart evolution from scratch (all data, prefs, config etc)? I don't want to remove the app, I've just configured things wrong and it's acting wonky.

---

### Post by TeoBigusGeekus on 2012-02-09
Look in your home folder for folders/files (hidden or not) that have to do with evolution (ie .evolution, .evolutionrc, etc.) and delete them.
You could even do a
```
find ~/ -iname "*evolution*"
```
to see them.

---

### Post by CaptSaltyJack on 2012-02-09
Great, thanks!

---

