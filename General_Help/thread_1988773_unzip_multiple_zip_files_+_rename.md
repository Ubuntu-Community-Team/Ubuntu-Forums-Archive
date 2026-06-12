---
title: "unzip multiple zip files + rename?"
date: 2012-05-28
forum: General Help
---

### Post by qwertyjjj on 2012-05-28
I have about 40 zip files each with a different name. However, the txt file inside each zip is called the same thing File.txt
How can I unzip them all and rename the file inside it so that it does not overwrite each time?
unzip '*.zip' is for the unzipping but the renaming?
Or alternatively, create a folder for each file.

---

### Post by eleftg on 2012-05-28
-- cd into the directory containing the zip files

-- Save this into a file myzipscript.sh

```

#!/bin/bash

# change IFS (Internal Field Separator) variable
# to properly loop over filenames with spaces
export SAVEIFS=$IFS
export IFS=$(echo -en "\n\b")

for z in *.zip;
do
    d=`basename $z .zip`
    mkdir $d && unzip $z -d $d
done

export IFS=$SAVEIFS

```

-- Make it executable
```
chmod +x myzipscript.sh
```

-- Run it
```
./myzipscript.sh
```

---

### Post by steeldriver on 2012-05-28
or I think you could use unzip -c and redirect the standard output to a file with a name based on the archive, something like

```
for file in `ls *.zip`; do unzip -qc $file > ${file%.zip}.txt; done

```

the q (quiet) stops it adding the 'Archive : xxx' header to the top of the redirected file

---

