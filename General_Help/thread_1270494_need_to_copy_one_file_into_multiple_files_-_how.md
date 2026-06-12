---
title: "need to copy one file into multiple files - how?"
date: 2009-09-19
forum: General Help
---

### Post by tweeks on 2009-09-19
Hello,
Is there a way to use the cp command to copy a file into multiple identical files (except for the filename)?  Like if I needed 500 identical copies of fileA.txt, my simple mind grasps for the way to do this by visualizing: cp fileA.txt > 500 copies starting with file1.txt and ending with file500.txt
I guess that probably would not work, but is there a simple script that would do this. I have done some simple scripting but my mind gets kind of foggy when it comes to loops and such.  Any help would be greatly appreciated.
thanks,
tim

---

### Post by falconindy on 2009-09-19
You could do this as a single line execution...
```
i=1;while [[ $i -le 500 ]]; do cp FileA.txt file$i.txt; i=$(($i + 1)); done
```

---

### Post by khelben1979 on 2009-09-19
Why not do it in graphical mode? I think it would be the easiest. I was able to do this effectively on AmigaOS 10 years ago, so I don't see why there would be any problems doing it inside Gnome or KDE. Just use copy and paste over the icon and let it fill up the window (should work).

---

### Post by kaibob on 2009-09-19
This is an alternative to the suggestion by falconindy. No better--just a bit shorter.

```
for i in {1..500} ; do cp fileA.txt file${i}.txt ; done
```

If the file names contains spaces, be sure to place them in quotes.

---

