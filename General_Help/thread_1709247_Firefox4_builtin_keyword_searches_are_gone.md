---
title: "Firefox4 builtin keyword searches are gone?"
date: 2011-03-17
forum: General Help
---

### Post by Habitual on 2011-03-17
This used to work by default in previous versions of FF.

imdb $movie
wiki $some_topic

now they don't.

My personal favorite was
man $page
sadly that's gone too.

Here's how to fix it...
Open **about:config** and search for **keyword.URL** - it should be blank.
Double-click to edit and enter

```
http://google.com/search?btnI=1&q=
```

(This is the code at Google to press the I'm Feeling Lucky button)
This will restore the previous Firefox keyword search behavior.
**No restart necessary.**

Enjoy.

---

### Post by pqwoerituytrueiwoq on 2011-03-17
here is the url firefox 3.6 uses
```
http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=
```

---

### Post by Habitual on 2011-03-18
Thanks!

I was wondering what it actually was.

---

