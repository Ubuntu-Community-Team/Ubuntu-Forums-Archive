---
title: "How to make Liferea forced read an rss to RTL ?"
date: 2011-05-22
forum: General Help
---

### Post by alz3abi on 2011-05-22
Hello every body.

any body can help me build script (filter) for liferea to to wrap content of RSS and read as RTL.

i tried to do this.

```
#!/usr/bin/sed
sed 's/\[CDATA\[\(.*\)\]\]/[CDATA[<div dir="RTL">\1<\/div>\]\]/'
```with no luck. any help please ?

edit : fixed.

like this
```

#!/bin/bash
/bin/sed -e 's_\(<content:encoded><!\[CDATA\[\)_\1<div dir="rtl">_g' -e 's_\(\]\]><\/content:encoded>\)_</div>\1_g'

```

---

