---
title: "Help on Encoding Conversion on Multiple Files"
date: 2011-06-08
forum: General Help
---

### Post by Chaconne on 2011-06-08
Hi, all,

I'm trying to convert the encoding of multiple files in a directory and I try to do it as follows.

```

#/bin/bash
find . -type f -name *.txt -exec iconv -f GBK -t utf-8 "{}" -o "{}.utf8" \;
find . -type f -name *.utf8 -exec mv -f "{}" `echo "{}" | sed 's/.utf8//'` \;

```

The first command goes well by generating utf8 files from all txt files, but the second command fails with error message. Could someone enlighten me about the mistake in the command and share a workable solution?

Thanks in advance!

---

### Post by TeoBigusGeekus on 2011-06-09
```
#!/bin/bash
find . -type f -name *.txt -exec iconv -f GBK -t utf-8 "{}" -o "{}.utf8" \;
find ./ -type f -name "*.utf8"|while read file
do
    mv -f $file $(echo $file|sed 's/.utf8//')
done
```

---

### Post by Chaconne on 2011-06-09
Thank you very much for the replay, TeoBigusGeekus. I did a number of search in Google and found a similar expression and it seems work.

```
find . -type f -name *.utf8 | while read filename; do mv -fv "${filename}" "`echo "${filename}" | sed -e 's/.utf8//'`"; done
```

However, I'm still not clear what is the mistake in my original command.

---

