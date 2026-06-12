---
title: "Correct usage of perl expression in 'rename'-shell command"
date: 2011-01-21
forum: General Help
---

### Post by M3phista on 2011-01-21
Hi everyone,

I want to rename some files in one directory and found the command
'rename' most appropriate.

Changing the file extension is easy since there are lot of examples for this.

But now I want to rename my files like this:

'somePrefix_blablabla.ext' --> '0_blablabla.ext'
'somePrefix_blablablablabla.ext' --> '0_blablablablabla.ext'

I DON'T want an incrementation, just the leading prefix '0_'

Can anybody give me the correct perl expression syntax for this?

Thanks a lot!

---

### Post by nothingspecial on 2011-01-21
***Edit - I reread your post,

If you want to replace everything before the first _ with a 0

```
rename -n 's/^.*?_/0_/g' *
```

Remove the -n if it does what you want.

---

### Post by M3phista on 2011-01-21
Perfekt!

Exactly what I was searching for.

Thank u very much :)

---

