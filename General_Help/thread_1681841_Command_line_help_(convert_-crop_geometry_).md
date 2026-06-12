---
title: "Command line help (convert -crop geometry )"
date: 2011-02-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-02-04
I know the command goes like this 
```
convert -crop geometry Desktop/file.png Desktop/file2.png
```i just do not know what the geometry variable needs to be 
I assume i need 4 numbers 
x1, y1, x2, and y2
how do i need to place them in the command
also is x2/y2 bases on 0,0 or x1,y1

EDIT
answer:
"$WIDTH x $HEIGHT + $X1 + $Y1"
convert -crop 100x50+15+10 Desktop/file.png Desktop/file2.png

---

