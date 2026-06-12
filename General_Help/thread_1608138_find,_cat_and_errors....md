---
title: "find, cat and errors..."
date: 2010-10-28
forum: General Help
---

### Post by computerx138 on 2010-10-28
Hi all,

I want to get a line count total of all PHP files, recursively from a specific folder. I'm still learning the shell, so might be coming at this the wrong way, however, I've tried:

> find -type d -exec cat {}/*.php \; | wc -l

Didn't work, so I tried:

> find . -type d -exec cat {}/*.php \; | wc -l

Still didn't work, so I decided to go for the complex route:

> find -type d -print0 | xargs -0 printf "%s/*.php\0" | xargs -0 cat | wc -l

Didn't work.

By "didn't work", I mean: cat is run in every folder, and gives:

> cat: ./folder/*.php: No such file or directory

... in folders I know full well have a dozen .php files.

I'm clearly doing something wrong, but I just don't understand what. As well as helping me with this command, can someone explain what I'm doing wrong or misunderstanding?

Thanks.

---

### Post by gmargo on 2010-10-28
```

find . -type f -name '*.php' -print0 | xargs -0 cat | wc -l

```

Your attempts are searching for directories instead of files, and then trying to use a shell expansion to find the files in each directory.  This code searches for files directly.

---

### Post by computerx138 on 2010-10-28
Brilliant, thank you very much!

---

