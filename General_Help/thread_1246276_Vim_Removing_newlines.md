---
title: "Vim Removing newlines"
date: 2009-08-21
forum: General Help
---

### Post by yes9111 on 2009-08-21
I have a large text file with a lot of newline characters so that when I view it with vim, it doesn't fill up the whole screen.

I want to remove the newlines so I can just have the lines wrap with vi.  What's tricky however is that I want to keep the paragraph newlines intact.  I tried using
```
:%s/\n[a-z]//
``` but that removes the first character of the next line which is bad :(

Any help??

---

### Post by aldimond on 2009-08-21
You can do...

```
:%s/\n\([^\n]\)/\1/
```

This captures the non-newline character and then replaces the regex with that.

It doesn't preserve the extra lines between paragraphs, but you can add those back in with something like

```
:%! sed G
```

This pipes the whole document out to sed and tells it to insert a new line after each line.

---

### Post by aldimond on 2009-08-21
Hm.  I was assuming your source document has two newlines between paragraphs.  If this isn't the case you can replace the [^\n], which means any character other than newline, with the [a-z] you had before, or really whatever else matches the beginning of a mid-paragraph line ([a-z], even with ignorecase on, is a bad idea because it misses numbers and other characters you might have in the text; if your paragraphs start with tabs, try [^\t]; if they start with spaces try [^ ]).

---

