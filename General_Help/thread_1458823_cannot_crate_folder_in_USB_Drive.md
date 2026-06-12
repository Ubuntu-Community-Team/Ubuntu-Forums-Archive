---
title: "cannot crate folder in USB Drive"
date: 2010-04-20
forum: General Help
---

### Post by Dr-a on 2010-04-20
when I try to create a folder in my USB drive I get this ..

Error while creating directory untitled folder.
There was an error creating the directory in /media/TRAVELDRIVE

any idea ?:confused:

---

### Post by sanderd17 on 2010-04-20
What do you get if you try to make a folder in the commandline?
```

mkdir name_of_folder

```

---

### Post by Dr-a on 2010-04-20
> **sanderd17 said:**
> What do you get if you try to make a folder in the commandline?
```

mkdir name_of_folder

```

the new folder goes to the home folder :confused:
how can I make it go to the usb drive ?

---

### Post by Paddy Landau on 2010-04-20
Your USB is mounted on your machine as
/media/TRAVELDRIVE

So, use the following command.
```
mkdir /media/TRAVELDRIVE/newfolder
```

---

### Post by coffeecat on 2010-04-20
> **Dr-a said:**
> the new folder goes to the home folder :confused:
how can I make it go to the usb drive ?

You need to specify the path:

```
mkdir /media/TRAVELDRIVE/name_of_folder
```

---

