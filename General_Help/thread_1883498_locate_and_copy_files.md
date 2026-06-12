---
title: "locate and copy files"
date: 2011-11-19
forum: General Help
---

### Post by fetjesus on 2011-11-19
Hello all,

I have been trying to do a script that can copy files of a certain type/name to a directory of my choosing.

The idea is to create a text file that contains for instance
Penguin
Dogs*
lunatic*
Then I want the script to locate those files in all directories and subdirectories from the directories I run the script and then copy them to the file /animals/

HAve anyone done a script like this already? I've been trying some using find etc but I think my scripting talents are lacking...

Thanks ahead!

Mikael

---

### Post by mutley89 on 2011-11-19
Something like this?

```

while read line; do find directory_to_search -name "$line" -exec cp {} directory_to_copy_to \;; done < file_containing_filenames

```

---

