---
title: "zenity and a new suggested filename"
date: 2010-03-25
forum: General Help
---

### Post by linuxcss on 2010-03-25
is there a way without creating a placeholder file to 
start zenity up with a filename which does not yet exist


i.e. I have current directory called /home/user1/dir4

and would like to have location field populated at invocation of
zenity with filename  "2010-03-25a"

the user could still select other directories and also edit the
suggested file name before pressing ok ...

or do I have to find another dialog tool to achieve this?

---

### Post by kaibob on 2010-03-25
I have never had an occasion to use this in a script, but the save and filename options appear to do what you want. For example 

```
zenity --file-selection --save --filename=2010-03-25a
```

I ran a test, and the above does allow you to change directories and to edit the filename. Also, you can add a path to the filename.

---

### Post by linuxcss on 2010-03-26
> **kaibob said:**
> I have never had an occasion to use this in a script, but the save and filename options appear to do what you want. For example 

```
zenity --file-selection --save --filename=2010-03-25a
```I ran a test, and the above does allow you to change directories and to edit the filename. Also, you can add a path to the filename.


Kaibob ... thanks, I haven't yet tested it much,
but this appears to be exactly what I was looking for!!!!
:)

---

