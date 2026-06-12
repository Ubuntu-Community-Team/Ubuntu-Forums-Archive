---
title: "Scripts help needed"
date: 2010-06-25
forum: General Help
---

### Post by t1nm@n on 2010-06-25
hello 
this here's my problem 
1. how can i have open in terminal -rightclick menu add- in nautilus.
2.i love to know how sripts work and how i can make them.

please help me~~

---

### Post by Pollox on 2010-06-25
For (1), install nautilus-open-terminal.  For (2), you would probably be better off either looking for a tutorial (searching the forums is a good place to start) or asking a specific question.

---

### Post by t1nm@n on 2010-06-26
thanks a lot dude...

---

### Post by nmobrien4 on 2010-06-26
To write a bash script, first create a ~/bin directory to store your  scripts and add it to your path (It should be in there already). Go to  ~/bin and use your favourite text editor to create a file containing your  script. Example:

```
gedit myscript.sh
```

Write your script and save it. Then make it executable with:

```
sudo chmod +x myscript.sh
```

You should now be able to execute your script by typing it's name in the  terminal.

---

