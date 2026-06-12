---
title: "Appending an index number to a list of files"
date: 2009-09-24
forum: General Help
---

### Post by tenmilez on 2009-09-24
I have a folder full of files that I would like to append (prepend?) a number to the beginning of based on its timestamp. So the earliest file would get 01_ added to it and so on. 

Thanks.

---

### Post by sedawk on 2009-09-24
This should do the trick with a 4-digit number
with leading zeros:

```

#!/bin/bash
typeset -i IDX
IDX=1
cd /your_folder ||exit 1
ls -t |while read FILE; do
  if [[ -f "$FILE" ]]; then
    PREFIX=$(eval printf "%.4d" $IDX)
    echo "mv \"$FILE\" \"${PREFIX}_${FILE}\""
    IDX=$IDX+1
  fi
done

```

---

### Post by tenmilez on 2009-09-26
I made a couple modifications to it:

1. removed the cd /<dir> bit because I find it's more useful if I don't have to edit the script for each use, I can just navigate to the folder I want and run the script there, and

2. I added a second line after the echo that actually performs the move instead of just saying that it's been moved. 

Thank you very much though. 

```
#!/bin/bash
typeset -i IDX
IDX=1
ls -t |while read FILE; do
  if [[ -f "$FILE" ]]; then
    PREFIX=$(eval printf "%.4d" $IDX)
    echo "mv \"$FILE\" \"${PREFIX}_${FILE}\""
    mv $FILE $PREFIX"_"$FILE
    IDX=$IDX+1
  fi
done
```

---

