---
title: "Use bash script to load copy buffer"
date: 2009-10-30
forum: General Help
---

### Post by approaching on 2009-10-30
So i wrote this little script that generates some encrypted text, and every time i need to copy that text, then paste it into something else. is there a way to just have the script copy that text into what i would imagine is the gnome copy buffer?

---

### Post by kaibob on 2009-10-30
I'm not sure I understand your question (my fault), but you may want to have a look at the xsel utility. For example, the following copies kaibob to the clipboard.

```
echo "kaibob" | xsel -i -b
```

---

