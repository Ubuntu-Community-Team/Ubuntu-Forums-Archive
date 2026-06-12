---
title: "google script help"
date: 2011-04-28
forum: General Help
---

### Post by Jack9099 on 2011-04-28
Okay I'm new here but I've been using ubuntu 10.04 for a while and i'm quite familiar with it :D 
But my problem is this: I tried making a bash script so Firefox would google my input, 
It's fairly simple because I just started making scripts. When i search for something, it doesn't search for something after a space i.e "Ubuntu Natty released"
This is how the script goes
```
#!/bin/bash
firefox  "http://www.google.com/search?q="$1"&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:eek:fficial&client=firefox-a"
```Any help appreciated :)

---

### Post by sisco311 on 2011-04-29
Welcome to the forums!

Spaces are not allowed in URLs. You could replace them with their hex value %20
```
#!/bin/bash

sterm="$@"
sterm="${sterm// /%20}"

firefox ""google.com/search?q=$sterm"

```

If you want to make your script more robust, then you have replace the other special characters as well:
[http://www.blooberry.com/indexdot/html/topics/urlencoding.htm](http://www.blooberry.com/indexdot/html/topics/urlencoding.htm)

If you are new to bash scripting, check out this bash guide along with the BashFAQ and BashPitfalls on the same wiki:
[http://mywiki.wooledge.org/BashFAQ/](http://mywiki.wooledge.org/BashFAQ/)

---

### Post by Jack9099 on 2011-04-30
Thanks so much, I'd fallen to sleep waiting for a reply!

---

