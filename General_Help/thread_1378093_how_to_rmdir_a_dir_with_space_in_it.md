---
title: "how to rmdir a dir with space in it"
date: 2010-01-11
forum: General Help
---

### Post by Tsquad on 2010-01-11
Im trying to delete a folder from the terminal named iTunes Music but it thinks im trying to del a folder called iTunes and one called Music. How can i del this file from the terminal?

---

### Post by Icehuck on 2010-01-11
You can try typing in the terminal.

rmdir Itunes\ Music

Edit - Forgot to complete the command. Also you need to have that backslash in there.

---

### Post by Tsquad on 2010-01-11
> **Icehuck said:**
> You can try typing in the terminal.

rmdir Itunes\ Music

Edit - Forgot to complete the command. Also you need to have that backslash in there.

thank you! that worked.

---

### Post by andrew.46 on 2010-01-11
Hi Tsquad,

A slight variation:

```
rmdir 'iTunes music'
```

or simply type the first couple of letters of the directory name and then press the Tab key...

Andrew

---

### Post by skymera on 2010-01-11
> **andrew.46 said:**
> Hi Tsquad,

A slight variation:

```
rmdir 'iTunes music'
```

or simply type the first couple of letters of the directory name and then press the Tab key...

Andrew

Agree.

Love the tab key when it comes to finding dirs :)
But yeah an example of a space is /home/$USER/Documents/Folder\ Name

---

### Post by ndefontenay on 2010-01-11
Tab key is fine as long as you're in an interactive mode.
If you are planning to script it then you need single quotes or backslash.

---

