---
title: "Sending mail via with bash"
date: 2011-04-25
forum: General Help
---

### Post by conradin on 2011-04-25
hi all,
I am trying to send myself mail via the CLI, but im failing...
what is wrong here?


```

#!/bin/bash
mail -s "$Test1" "myEmai@gmail.com" < /file.txt

```

---

### Post by HermanAB on 2011-04-25
Did you install a MTA such as Postfix/Citadel/Qmail?

---

### Post by SeijiSensei on 2011-04-25
Does it complain that it can't find the "mail" program?  If so, install **bsd-mailx**.  As Herman says, you'll also need to have an MTA running like Postfix.  "sudo apt-get install postfix bsd-mailx" should be all you need to get started.

---

### Post by conradin on 2011-04-26
I thought mailutils might be enough. It didnt prompt me, for anything, it just didnt work. I just installed postfix. Ill see how it goes.

---

### Post by conradin on 2011-05-17
Seiji Sensei  gets it. I had postfix, I set it up in postfix. it was still broken... I installed bsd-mailx, and restarted, and now it works!

---

