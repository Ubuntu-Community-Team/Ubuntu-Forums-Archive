---
title: "firefox and chorme not working"
date: 2011-02-08
forum: General Help
---

### Post by albanee on 2011-02-08
Hi, I am new pls help me.  All of a sudden since last week my firefox and google chrome web browser is not working. Chrome closes/crashes automatically as soon as i open it. However firefox open then when i type a web page it closes/crashes. I am currently using Epiphany web browser its not crashing but I would rather use chrome and firefox. btw Iam using Ubuntu 9.10
Please let me know if you guys need more info and how I can get it. I am new so please give me step by step details on how to fix it. 
thanks for your time

---

### Post by matt_symes on 2011-02-08
Hi

With Firefox closed, try renaming your hidden Firefox profile folder in your home directory.

After doing that start up firefox. It will create a new profile. Does it still crash ?

```
mv ~/.mozilla/ ~/.mozilla.bak
```

Kind regards

---

### Post by albanee on 2011-02-08
how do i go to firefox profile folder ?

---

### Post by albanee on 2011-02-08
mv: target `.mozilla.bak' is not a directory

---

### Post by matt_symes on 2011-02-08
Hi

There are 2 basic ways to do it. From the terminal (Applications-> Accessories ->Terminal) type.

```
mv ~/.mozilla/ ~/.mozilla.bak
```

or through the file browser (Places->Home Folder) select View->Show hidden folders. Find the folder and rename it. Don't delete it.

Then start up firefox.

Kind regards

---

### Post by albanee on 2011-02-08
mv: target `.mozilla.bak' is not a directory

---

### Post by matt_symes on 2011-02-09
Hi

Can you copy and paste exactly what you entered. It should work as shown on my machine.

```
matthew@matthew-laptop:~$ ls -ad .moz*
.mozilla
matthew@matthew-laptop:~$ mv ~/.mozilla/ ~/.mozilla.bak
matthew@matthew-laptop:~$ ls -ad .moz*
.mozilla.bak
matthew@matthew-laptop:~$ 
```

You may want to try the second method with nautilus.

Kind regards

---

### Post by albanee on 2011-02-09
thanks for the reply here is what i have got 


mohammed@mohammed-laptop:~$ ls -ad .moz*
.mozilla  .mozilla.bak  .mozilla-thunderbird
mohammed@mohammed-laptop:~$ mv ~/ .mozilla/ ~/.mozilla.bak
mv: cannot move `/home/mohammed/' to a subdirectory of itself, `/home/mohammed/.mozilla.bak/mohammed'
mohammed@mohammed-laptop:~$ ls -ad .moz*
.mozilla.bak  .mozilla-thunderbird
mohammed@mohammed-laptop:~$

---

### Post by albanee on 2011-02-10
any idea how to get it fixed ?

---

