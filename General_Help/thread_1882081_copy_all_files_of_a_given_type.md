---
title: "copy all files of a given type"
date: 2011-11-16
forum: General Help
---

### Post by Mount on 2011-11-16
!BASH! !BASH! HEAD ON DESK... 

Hi Need some help this code is giving "Syntax error: redirection unexpected"


```
#!/bin/bash

while IFS = read -r -d '' filename
do
	cp "$filename" /temp/
done < <(find ./ -name '*.pdf' -print0)
```

what be it that I do wrong?

All I want is to find all files matching *.pdf in a given directory tree and copy them to a new location... 

help thank you please

---

### Post by tonysathre on 2011-11-16
```

#!/bin/bash

for f in *.pdf
do
        printf "Moving file $f to /tmp\n"
        mv $f /tmp/$f
done

```

---

