---
title: "Update issue"
date: 2010-02-24
forum: General Help
---

### Post by nos09 on 2010-02-24
i looked for update and got an error at last. here is the screen shot.
what would be the problem ?


sorry i got it wrong. but still you can see the words throgh the "take screen shot window"
sorry made mistake by taking screen shot.

---

### Post by wojox on 2010-02-24
Open a terminal and run:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

```
sudo gpg --export --armor C1289A29 | sudo apt-key add
```

---

### Post by nos09 on 2010-02-24
> **wojox said:**
> Open a terminal and run:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

```
sudo gpg --export --armor C1289A29 | sudo apt-key add
```

thanks. will see if that works. connection is low now.

---

### Post by nos09 on 2010-02-25
didn't worked !!!
here is what i got. when i typed the command you gave me..

---

