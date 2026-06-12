---
title: "Output to file"
date: 2010-09-11
forum: General Help
---

### Post by RedSingularity on 2010-09-11
How can i redirect output of a command to a file?  The command generates constant output until i stop it.  I want all the info it got to go to a file so i can read it later.  

sudo netsniff-ng -d eth0 > ~/Desktop/file

is the exact command, but when i halt the process and check the file on the desktop it is empty.

---

### Post by 3Miro on 2010-09-11
This will redirect only output that will otherwise show up in the terminal. Errors might not show up either. For errors you may have to use:

```
 sudo netsniff-ng -d eth0 1> ~/Desktop/file 
```

or 2, I can never remember.

---

### Post by cgroza on 2010-09-11
you can pipe a programs output to another programs input via " | ". For example:

sudo apt-get update | nano ~/output

From there just save the file.

---

### Post by RedSingularity on 2010-09-12
Great!  Thanks guys.

---

### Post by Lukas666 on 2010-09-12
> **cgroza said:**
> you can pipe a programs output to another programs input via " | ". For example:

sudo apt-get update | nano ~/output

From there just save the file.

Or he could learn that "standard output" and "error output" are two different things which may look the same and need to be redirected separately.

---

### Post by HermanAB on 2010-09-12
This should redirect both stdout and stderror to the file:

```
sudo netsniff-ng -d eth0 > ~/Desktop/file 2>&1
```

---

### Post by RedSingularity on 2010-09-12
> **HermanAB said:**
> This should redirect both stdout and stderror to the file:

```
sudo netsniff-ng -d eth0 > ~/Desktop/file 2>&1
```


Interesting, that works too.  Thanks :)

---

### Post by cgroza on 2010-09-13
> **Lukas666 said:**
> Or he could learn that "standard output" and "error output" are two different things which may look the same and need to be redirected separately.

Thats what i do and it works.

---

