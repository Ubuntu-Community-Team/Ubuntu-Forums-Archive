---
title: "Cannot pipe gdialog output to variable"
date: 2010-03-20
forum: General Help
---

### Post by d3v1150m471c on 2010-03-20
I'm trying to use the output from gdialog's input box in another command with no success. 

```

var=`gdialog --inputbox something 50 50`

```

Any suggestions?

---

### Post by d3v1150m471c on 2010-03-20
```

var=$(gdialog --inputbox something 50 50)

```
This doesn't work either

---

### Post by rnerwein on 2010-03-20
hi
gdialog use stderr as stdout. you have to call it:

bla=`gdialog --inputbox  50 50 [COLOR=Red]2>&1[/COLOR]`
echo $bla

ciao

---

### Post by d3v1150m471c on 2010-03-20
This works if I were putting the command into a terminal but it doesn't work from a shell script.

---

