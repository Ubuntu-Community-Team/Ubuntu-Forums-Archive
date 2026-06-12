---
title: "Mass Change id3 TITLE on MP3's"
date: 2012-08-07
forum: General Help
---

### Post by bonelifer on 2012-08-07
I have some podcast that the corporation that puts them out don't tag anymore. For most of the info, it's all the same so I've been able to set up a bash script for each one that adds that info. The problem lies in putting a TITLE on the mp3s as multiple days may pile up before I listen to them. I just want to output the filename minus the .mp3 extension to the TITLE tag. I found the code below to do that but I need it to be able to run through all the mp3's in the directory. 

```
#!/bin/sh

fn=$(readlink -f "$1")

basename=$(basename "$fn" .mp3)
title=${basename}

mid3v2 "$1" \
--song="$title"
```

---

### Post by Vaphell on 2012-08-08
```
#!/bin/bash

for file in *.mp3
do
  title="${file##*/}"
  title="${title%.*}"

  mid3v2 "$file" --song="$title"
done
```

---

### Post by bonelifer on 2012-08-08
Thanks Vaphell. Added that to my current bash file. Now I have all the tagging for the two podcasts completely automated and it saves me from having to use mp3tag from Windows. Not really sure why NBC stopped tagging them.

---

