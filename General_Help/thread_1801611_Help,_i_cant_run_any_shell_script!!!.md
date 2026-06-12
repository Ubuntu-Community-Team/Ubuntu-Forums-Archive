---
title: "Help, i cant run any shell script!!!"
date: 2011-07-10
forum: General Help
---

### Post by dark ariel7 on 2011-07-10
I have the natty version of lubuntu.
 i gave it permision to run as an executable
i made the xterminal the default application to open it.
the shell script itself is ok because i started it in ubuntu and it worked.
the shell script will only open as a text file.
 i really need help fast i only have about 5 hours to fix this problem.:(

---

### Post by lmarmisa on 2011-07-10
Type this command:

```

bash yourscriptfile

```

---

### Post by wojox on 2011-07-10
```

chmod +x myScript
./myScript

```

---

### Post by dark ariel7 on 2011-07-10
what do you mean by scriptfile?
where the shell is?

---

### Post by dark ariel7 on 2011-07-10
also is there a gui version of this
can i do this without the terminal

---

### Post by dark ariel7 on 2011-07-10
will this problem be fixed if i repalce pcman with another file mangement tool
if so which one should i use and how do i install it?

---

### Post by wojox on 2011-07-10
> **dark ariel7 said:**
> will this problem be fixed if i repalce pcman with another file mangement tool
if so which one should i use and how do i install it?

Personally I like thunar but it doesn't matter. It has to do with the script and terminal. What are the permissions to the file. In xterminal "cd" to the directory your script is in and run:

```
ls -al
```

---

### Post by dark ariel7 on 2011-07-10
please make things a little less technical im a total linux noob.

---

### Post by wojox on 2011-07-10
> **dark ariel7 said:**
> please make things a little less technical im a total linux noob.

Are you using xterminal or Lxterminal?

---

### Post by dark ariel7 on 2011-07-11
lxterminal

---

### Post by dark ariel7 on 2011-07-11
anyone out there?
preferably with an answer
preferably not one to use in the terminal because i dont know how to use it.

---

### Post by wojox on 2011-07-11
Your help is posted previously, if your gonna write shell scripts you need to use the terminal.

---

### Post by dark ariel7 on 2011-07-11
i dont want to write it i already have it i need to run it to install a driver. it worked in ubuntu and xubuntu.
the driver is for an airlink awll5088 usb wifi adapter

---

### Post by wojox on 2011-07-13
> **dark ariel7 said:**
> i dont want to write it i already have it i need to run it to install a driver. it worked in ubuntu and xubuntu.
the driver is for an airlink awll5088 usb wifi adapter

Have you right clicked the script and checked it's permissions to see if it's executable?

---

### Post by dark ariel7 on 2011-07-14
i did and it is executable

---

