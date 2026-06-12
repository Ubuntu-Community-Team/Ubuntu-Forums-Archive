---
title: "Testing a 'find &amp; replace' command"
date: 2010-09-29
forum: General Help
---

### Post by puremetal on 2010-09-29
Hi all

I need to run a find & replace on some variable names on my webserver. I've tested the following command and it works fine to do the find & replace accross multiple files within a directory:

```
find mytemp/ -type f -print0 | xargs -0 sed -i 's/apple/mango/g'
```

This will search in directory mytemp/ for apple and replace it with mango (for example)

However... does anyone know how could I could set this up so that it runs a test and outputs the results of what it would have done to a text file, so that I can check what will happen before running the find & replace for real? Simply piping this to a file with > results.txt doesn't work as it just runs the find & replace anyway.

Hope this makes sense! Thanks :)

---

