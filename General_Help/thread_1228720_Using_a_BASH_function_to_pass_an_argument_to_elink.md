---
title: "Using a BASH function to pass an argument to elinks"
date: 2009-08-01
forum: General Help
---

### Post by Anticontrame on 2009-08-01
Hi all,

I'm trying to make a function that will allow me to google a phrase (with spaces) from the command line. Using
> function g() { elinks www.google.com/search?q="$@" ; }
only works if I type
> g "test me"

I'd like to do it without including the quotes every time, but without them elinks will google "test" and tell me that it's unable to retrieve the file "me". What am I doing wrong?

Thanks!

---

### Post by unutbu on 2009-08-01
I can't explain why your version does not work, but this seems to work for me:
```
function g() { KEY="$@"; firefox "www.google.com/search?q=${KEY}" ; }
```
(I tried it with firefox; I assume it will work for elinks too.)

---

### Post by Anticontrame on 2009-08-01
It does work. Thank you!

---

