---
title: "Gambas help"
date: 2010-01-11
forum: General Help
---

### Post by ve3tru on 2010-01-11
I'm new to Gambas and well programming too
I did some basic stuff in the 70's but what ever. I just want a program 
a simple button that can execute stuff in terminal.
any help would be real nice 
tnx

---

### Post by aaronp on 2010-01-17
> **ve3tru said:**
> I'm new to Gambas and well programming too
I did some basic stuff in the 70's but what ever. I just want a program 
a simple button that can execute stuff in terminal.
any help would be real nice 
tnx

Hi, I'm not new to programming but new to Gambas and finding very little documentation on how to start using it.
However, for what you want to do I'd suggest something pretty quick to get you started:

1. Drop a button from the toolbox onto a blank form.
2. Click on the button and set the properties you like in the properties window (e.g. 'Text' property to set the label)
3. Double click the button to bring up the code window. You can then type code you want to execute on a button click event after the line that says ```
PUBLIC SUB Button1_Click()
``` and ```
END
```

Now it depends on what you want to 'execute' on the click of a button as to what you put in here.
I've found a good pdf file that I'm going through. It's a bit sketchy but seems to be the best I've found so far...

[http://www.onlinefreeebooks.net/go.php?url=http://vectorlinux.osuosl.org/Uelsk8s/gambas-beginner-guide.pdf](http://www.onlinefreeebooks.net/go.php?url=http://vectorlinux.osuosl.org/Uelsk8s/gambas-beginner-guide.pdf)

---

