---
title: "terminal command keep original filename ?"
date: 2012-03-23
forum: General Help
---

### Post by then_dude on 2012-03-23
hello people,  i got an easy question but i can't seem to find the answer.   situation: a lot of times i use the terminal command line to speed up work.  for example: convert pdf's to jpg's.   i would like to keep the original name of the pdf and use it for the jpg, but i can't seem to make it work.   can anybody help me.   at this time i do the next  convert *.pdf file.jpg  i get file-1, file-2 .... but i would like the originale pdf name.  thanks

---

### Post by nothingspecial on 2012-03-23
You would use a for loop and parameter expansion
```

for f in *.pdf; do convert "$f" "${f%.pdf}".jpg; done
```

or

```
for f in *.pdf; do conver "$f" "${f/.pdf/}".jpg; done
```

See here [http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

Always test stuff you see posted in the forums before you try on it on your data, typos etc do happen.

---

### Post by WorMzy on 2012-03-23
```
for file in *.pdf
do
  filename=${file%.*}
  convert "$file" "${filename}.png"
done

```

Oops, too slow.

---

### Post by cortman on 2012-03-23
Sometimes the converter program will have such an option you can activate using a flag (-x), like ffmpeg. Look in the man page for your program.

---

### Post by then_dude on 2012-03-23
guys, you are just to great...  thanks a lot.

---

