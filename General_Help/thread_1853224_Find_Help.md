---
title: "Find Help"
date: 2011-10-01
forum: General Help
---

### Post by Yellobes on 2011-10-01
x@y:~/Folder$ find -name *.pls -exec mv {} ../Music/pls/ \;
find: paths must precede expression: z.pls
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]


Why is it spitting the help at me? 

There are 20+ pls files in this directory btw.

---

### Post by papibe on 2011-10-01
The shell is expanding (translating into filenames) the expression *.pls. In order to pass the regular expression intact to the command find, quote it:
```
$ find -name '*.pls' -exec mv -v '{}' ../Music/pls/ \;
```
Also, I would recommend quoting the {} part, as in above.

Note: I added a verbose option to the command 'mv'. so you can see and trace what is being moved.

Hope it helps,
Regards.

---

### Post by Yellobes on 2011-10-01
Stupid mistake, thank you so much for the prompt answer!

---

### Post by papibe on 2011-10-01
;) You're welcome! Please mark the thread solved when you have the chance.
Regards.

---

