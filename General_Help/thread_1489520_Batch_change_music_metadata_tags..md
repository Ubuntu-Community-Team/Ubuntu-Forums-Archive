---
title: "Batch change music metadata tags."
date: 2010-05-21
forum: General Help
---

### Post by nothingspecial on 2010-05-21
I`ve got this which renames everything from uppercase to lower case.
```

#!/bin/bash
for f in *; do
g=`expr "xxx$f" : 'xxx\(.*\)' | tr '[A-Z]' '[a-z]'`
mv "$f" "$g"
done
```

and I got this

```
rename 's/(\b\S+)/\u$1/g' *
```

from Falconindy (thankyou :)) which will then replace the first letter of each word back to upper case. 

I used them on the file names of about a thousand songs I have. But I would like to change the tags.

Every tag (artist, album, track etc) has been done with the caps lock on.

I would like only the first letter of each word, in each tag to be upper case and the rest lower case.

I know ffmpeg has the -metadata option and I know mencoder can do it as well.

But putting it together is beyond me.

A gui will do. Easytag will let you right click on a field and do what I want, but I can`t seem to get it to do it for all of them.

Thanks.

---

### Post by nothingspecial on 2010-05-21
Never mind, I got it. You just change how easytag reads file names in the scanner function.

---

