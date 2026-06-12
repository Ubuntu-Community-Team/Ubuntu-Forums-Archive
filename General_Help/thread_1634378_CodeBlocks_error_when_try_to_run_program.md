---
title: "Code:Blocks error when try to run program"
date: 2010-11-30
forum: General Help
---

### Post by trackisimo on 2010-11-30
Hello,

I installed Code:Blocks (8.02 from ubuntu software center) and try to run sample program (at first I tried some program related to OpenCV and configure the project for it).

The Build went OK but I cant Run the program.
So I tried the simplest progrma of hello World and still I get the same error even on a clean new project.

The Error:
"error while loading shared libraries: cv.so can not open shared object file : No such file or directory"

Please Help,
I use ubuntu 10.04...

---

### Post by tuxmanic on 2011-01-20
Hope you already resolved the issues, if not

> I installed Code:Blocks (8.02 from Ubuntu software center) and try to  run sample program (at first I tried some program related to OpenCV and  configure the project for it).

The Build went OK but I cant Run the program.
So I tried the simplest program of hello World and still I get the same error even on a clean new project.

The Error:
"error while loading shared libraries: cv.so can not open shared object file : No such file or directory"First of all he Code blocks available in Ubuntu repository is too old, but latest version is available through third party repositories. details @ [URL="http://lgp203.free.fr/spip/spip.php?article1"]http://lgp203.free.fr/spip/spip.php?article1
[/URL]
From your post i assume that you installed opencv correctly thats why you are compiling with out any error. Any way can you post the ouput of following command, just to make sure that everything is in the correct place.

```
pkg-config --cflags --libs opencv
```which will print all the include & library paths of opencv

---

