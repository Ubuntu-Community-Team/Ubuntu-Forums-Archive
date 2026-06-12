---
title: "conky won't print hashtags in twitter feed"
date: 2012-02-18
forum: General Help
---

### Post by sbjaved on 2012-02-18
I use "python-twitter" to display my feed in conky. When I run the python script, the output in terminal is complete with all hashtags but conky refuses to print anything with a '#' sign before it (probably treats it as a comment). Is there any way to make conky print '#' symbol?

e.g. tweet:
Bill Maher Stand Up Comedy #Baltimore, MD & #Washington, DC! Mar. 31st & Apr. 

Nothing will be printed after 'Comedy'

---

### Post by sbjaved on 2012-02-18
Solved it!
Adding \# causes conky to print # :) From there it was a simple matter of 
```
str = #
new_str = str.replace('#', '\#')
print new_str
```
Hope this helps someone.

---

