---
title: "Whats the command? (top)"
date: 2011-03-18
forum: General Help
---

### Post by Adrienk on 2011-03-18
What command would I use with Top to sort what is displayed when typing top to see the virual memory in a vm? So I am currently running ubunut 10.10 in a vm and I want to run top and display the virtual memory, what sort command would I include with top?

---

### Post by blueridgedog on 2011-03-18
The command "free" will show you how much is used. Pressing "o" will give you a virtual memory figure in "top".  You may have to move the field to see it.  You can then sort on it by hitting "<" or ">" to select it and "R" to reverse the sort.

More information can be found via "man top".

---

### Post by seawolf167 on 2011-03-18
You may also want to take a look a *htop*, I like it better than *top*

```
sudo apt-get install htop
```

---

