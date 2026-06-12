---
title: "Error extraxting ZIP file"
date: 2010-05-08
forum: General Help
---

### Post by pepe machine on 2010-05-08
Hello guys, I have this file that is in ZIP. I can open it and browse the files inside via archive manager. But extracting it gives me an error.

When using GUI it says that  'ERROR while extracting files'

and in command line when i command
unzip -q myfile.zip

it display this errors

file #2109:  bad zipfile offset (local header sig):  -2122072556
file #2110:  bad zipfile offset (local header sig):  -2121511988
file #2111:  bad zipfile offset (local header sig):  -2121511886
file #2112:  bad zipfile offset (local header sig):  -2121375823
file #2113:  bad zipfile offset (local header sig):  -2121310073
file #2114:  bad zipfile offset (local header sig):  -2121282474
file #2115:  bad zipfile offset (local header sig):  -2121107851
file #2116:  bad zipfile offset (local header sig):  -2121015601
file #2117:  bad zipfile offset (local header sig):  -2120957317
file #2118:  bad zipfile offset (local header sig):  -2120906286
file #2119:  bad zipfile offset (local header sig):  -2120906193

please help me guys. i know this is not an ubuntu issue. I just need to find a way to extract my file. i need it badly.

---

### Post by dracayr on 2010-05-08
Just as it says, it's a broken zipfile

---

### Post by pepe machine on 2010-05-08
is there any software to fix it?

---

### Post by dracayr on 2010-05-08
not that I know of. With unrar, there's the option -kb which lets you keep the broken extracted files /which may be at least partly correct, but I didn't see anything like that in the manpage of unzip.

---

### Post by pepe machine on 2010-05-11
any other suggestion guys, is there a repair tool for my zip file.? i have found some softwares that can repair a corrupted zip file but sadly it only runs on windows.. :(

---

