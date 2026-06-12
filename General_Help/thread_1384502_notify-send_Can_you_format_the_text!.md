---
title: "notify-send: Can you format the text?!"
date: 2010-01-18
forum: General Help
---

### Post by drewsus on 2010-01-18
Hello all!
So, I was wondering if there was any way to format the text for notify-send? Im making some scripts and everything works fine. I have an icon and such. But, all the text always shows up **bold** and in one "wrap around" line. In programs like Emesene or just system notifications they can be formated and show up in regular and bold text and new lines. 
Is there any way that I can achieve this? 
Thanks, 
dRew

---

### Post by sisco311 on 2010-01-19
```

notify-send -i "path/to/icon.png" \
"Title (bold)" \
"Text Line1
Text Line2
Text Line3"

```

---

### Post by drewsus on 2010-01-19
you, sir, are brilliant!

---

