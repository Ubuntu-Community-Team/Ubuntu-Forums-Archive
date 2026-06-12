---
title: "mv Command question....."
date: 2011-06-26
forum: General Help
---

### Post by Curse on 2011-06-26
When trying to mv a file, all I'm getting is > 

```

agnate@agnate-laptop:~$ mv ./Downloads/"movie.mp4 ./Videos/movie.mp4 {press enter key}
> 

```

Then it doesn't do anything... no new files, no old file being deleted.... nothing. 

Same thing if I do mv ./input ./Videos/ (not adding the specific output file name)

???

---

### Post by Vaphell on 2011-06-26
" opens a string, so mv doesn't see proper source/target parameters

put \ before " to tell shell to treat " as any other character

---

### Post by inameiname on 2011-06-26
> **Curse said:**
> When trying to mv a file, all I'm getting is > 

```

agnate@agnate-laptop:~$ mv ./Downloads/"movie.mp4 ./Videos/movie.mp4 {press enter key}
> 

```Then it doesn't do anything... no new files, no old file being deleted.... nothing. 

Same thing if I do mv ./input ./Videos/ (not adding the specific output file name)

???


I think what you want is this:

```

mv /path/to/Downloads/movie.mp4 /path/to/Videos/movie.mp4

```"As mentioned above, you have a '"' when you don't need it (typo ?), and also, you aren't trying to open the files, so that '.' is not what you want. And of course, if you did mean to put the '"', then again, as stated before, you need to '\' it beforehand so the terminal will understand it correctly.

---

### Post by Curse on 2011-06-26
Sorry, that was a typo from my original........ BUT it made me see that I did, in fact, leave an open " in my line!

Thank you guys :x little embarrassing lol

---

