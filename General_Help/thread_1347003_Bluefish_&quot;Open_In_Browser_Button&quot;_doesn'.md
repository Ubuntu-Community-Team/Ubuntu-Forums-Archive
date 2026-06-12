---
title: "Bluefish &quot;Open In Browser Button&quot; doesn't work"
date: 2009-12-05
forum: General Help
---

### Post by huebner on 2009-12-05
using Bluefish Version 1.0.7
When I click on "View In Browser" button Firefox opens to default URL - not to the html page I have named/saved/ and am editing in Bluefish.

My operating system is Ubuntu version 9.10
Firefox version 3.5.5

In "Bluefish/edit/preferences/External Programs" 
I have entered as label: Firefox  (first location - at the top of the list)
 and as command: -new-window %s&
but when I click on "Apply" -new-window disappears and is replaced with -x

What can I do to resolve this Bluefish "View in brower button" issue?

---

### Post by andrew.46 on 2010-02-05
Hi Huebner,

If you are still around you will find that the correct syntax is:

```
/usr/bin/firefox -new-window "%s" &
```

All the best,

Andrew

---

