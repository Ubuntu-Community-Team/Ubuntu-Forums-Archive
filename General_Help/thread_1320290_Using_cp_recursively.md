---
title: "Using cp recursively"
date: 2009-11-09
forum: General Help
---

### Post by Coding Monkey on 2009-11-09
Hi guys

I'm trying to recursively copy a bunch of files, while excluding certain folders.  It seems like my filter (whatever it's called) on the cp command is only checked on the top level.

I have a folder structure which is similar to the following:
```
- Project 1
  - CVS
  - Folder 1
    - CVS
    - File 1
    - File 2
```

I would like to copy everything except the CVS folders to a Project 2 folder.

After executing the following command from the Project 1 folder:  ```
cp -r [!CVS]* ../Project\ 2
``` the Project 2 folder looks like this:
```
- Project 2
  - Folder 1
    - CVS
    - File 1
    - File 2
```

Does anyone have an idea how I can exclude all CVS folders on all levels of the file structure?  Any help will be much appreciated, thanks!

---

