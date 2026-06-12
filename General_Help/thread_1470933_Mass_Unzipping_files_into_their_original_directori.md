---
title: "Mass Unzipping files into their original directoriy"
date: 2010-05-03
forum: General Help
---

### Post by powerpleb on 2010-05-03
I have hundreds of these fonts I want to use and they are all individually zipped up and organised into their own individual directories. So one zip file per directory. What I want (but don't know how) to do is perform some bash magic and mass unzip them all so each file unzips into its own directory, so then each directory will contain the contents of its zip file.

The closest thing I've found is this: ```
ls /*/*.zip | xargs -n1 unzip
```
This goes into each directory but unzips the contents off all the files into the directory I ran it from. So does anyone know how I can do it so each zip file is unzipped into the directory it is currently in?

---

### Post by sisco311 on 2010-05-03
Try:

```

for dir in *; do 
  if [ -d "$dir" ]; then 
    cd "$dir" 
    unzip "*.zip" 
    cd ..
  fi
done

```

in one line:
```
for dir in *; do if [ -d "$dir" ]; then cd "$dir"; unzip "*.zip"; cd ..;fi; done
```

---

### Post by powerpleb on 2010-05-03
Thanks :)

---

