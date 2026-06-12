---
title: "open .txt in terminal"
date: 2010-05-15
forum: General Help
---

### Post by l3ecl on 2010-05-15
when i double click a .txt file, i dont want gedit to open it, and instead, i would like it to open in terminal with it's output displayed (like cat .txt). how do i do this?

when i click on the .txt, i can get gnome-terminal to run, but i can't get it to open the .txt. 

what do?

---

### Post by kaibob on 2010-05-15
> **l3ecl said:**
> when i double click a .txt file, i dont want gedit to open it, and instead, i would like it to open in terminal with it's output displayed (like cat .txt). how do i do this?

when i click on the .txt, i can get gnome-terminal to run, but i can't get it to open the .txt. 

what do?

The following shell script will do what you want. You have to define this script as the default open-with program for text files. 

```
#!/bin/bash

gnome-terminal --execute bash -c "cat '$1' ; bash"
```

---

### Post by Bradj47 on 2010-05-15
> **kaibob said:**
> The following shell script will do what you want. You have to define this script as the default open-with program for text files. 

```
#!/bin/bash

gnome-terminal --execute bash -c "cat $1 ; bash"
```

Wouldn't that only display the text file? If you wanted to edit it as well wouldn't you do this?: 
```
#!/bin/bash

gnome-terminal --execute bash -c "vi $1 ; bash"
```

---

### Post by kaibob on 2010-05-15
> **Bradj47 said:**
> Wouldn't that only display the text file? If you wanted to edit it as well wouldn't you do this?: 
```
#!/bin/bash

gnome-terminal --execute bash -c "vi $1 ; bash"
```

The OP said that he wanted to open a text file "in terminal with it's output displayed (like cat .txt)". That's what my suggested command does. If the OP does want to edit the text file, then your suggestion is an excellent one.

---

### Post by l3ecl on 2010-05-15
this is my first script ever, kindly help me debug. here's what i did:

1.)i type "vi script-name"

2.)then pasted your code.

3.)and tried to open the application using "script-name"
[IMG]http://img237.imageshack.us/img237/7336/35157905.png[/IMG]

4.) i probably messed up already b/c it doesnt work

---

### Post by spiky001 on 2010-05-15
removed

---

### Post by geo909 on 2010-05-15
> **spiky001 said:**
> try nano
```
nano
```

Ah, why don't people read better the OP's question, before
answering?! :))

---

### Post by spiky001 on 2010-05-15
sorry thought i misread it i,ll remove it

---

### Post by l3ecl on 2010-05-15
i got it working! thanks for the help

---

