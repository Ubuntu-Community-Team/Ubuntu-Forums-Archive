---
title: "Pidgin autoaccept plugin"
date: 2009-09-27
forum: General Help
---

### Post by Elcid247 on 2009-09-27
idk if this is the right place, i did find a bug tracker for this but i thought id might post here as well.

the auto-accept plugin in pidgin puts "20%" or "%20" instead of spaces so i came up with some commands to fix it

```
rename s/"20%|%20"/" "/g *
```

idk if rename is installed by default so heres another "standard" one
```
find -regextype posix-egrep -regex ".*[%]20.*|.*20[%].*" -exec sh -c 'mv "{}" "$(echo "{}" | sed -r s/"[%]20|20[%]"/" "/g)"' \;
```


anyway i was wondering if some1 could tell me if theres a way to have this run automatically after files r auto-accepted

---

