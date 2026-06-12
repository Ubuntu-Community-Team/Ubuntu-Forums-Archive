---
title: "how to delete /opt thrash"
date: 2010-08-17
forum: General Help
---

### Post by cjaramilu on 2010-08-17
I have a partition "/opt" which has its "/opt/.Trash-1000" directory.
"opt" is owned by me the user I log in.  Why my thrash icon
doesn't show the "/opt" thrash?  how can I delete my "opt" thrash with
a GUI instead of writing  "sudo rm /opt/.Thrash-1000/files/*" on a terminal?

---

### Post by sandyd on 2010-08-17
> **cjaramilu said:**
> I have a partition "/opt" which has its "/opt/.Trash-1000" directory.
"opt" is owned by me the user I log in.  Why my thrash icon
doesn't show the "/opt" thrash?  how can I delete my "opt" thrash with
a GUI instead of writing  "sudo rm /opt/.Thrash-1000/files/*" on a terminal?
view -> show hidden files

---

### Post by wojox on 2010-08-17
Thrash or trash. Either way you need sudo privileges because everyone should have access to /opt.

---

### Post by cjaramilu on 2010-08-17
If I go with Nautilus to /opt/.Trash-1000/files directory and select all 
the files, I don't see how i can erase them. The only option is "Move
to Thrash" which leaves the files right where they are.

---

### Post by ercferret18 on 2010-08-17
You can select the files, then hold down shift and press delete on your keyboard.

---

### Post by wojox on 2010-08-17
> **cjaramilu said:**
> If I go with Nautilus to /opt/.Trash-1000/files directory and select all 
the files, I don't see how i can erase them. The only option is "Move
to Thrash" which leaves the files right where they are.

Try:

```
gksudo nautilus
```

---

### Post by cjaramilu on 2010-08-17
When i run "gksudo nautilus" and then click on Trash, i get
The folder contents could not be displayed. 
Sorry, could not display all the contents of "trash": Operation not supported

---

### Post by cjaramilu on 2010-08-17
ercferret18 solution worked!  no need for gksudo nautilus.
thanks everybody.

Still, I wonder why my Trash icon doesn't do that.

---

### Post by cjaramilu on 2010-08-17
no need for shift + delete key.... just select and delete key

---

