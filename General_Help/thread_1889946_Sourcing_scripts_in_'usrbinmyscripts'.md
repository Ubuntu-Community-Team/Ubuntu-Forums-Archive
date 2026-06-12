---
title: "Sourcing scripts in '/usr/bin/myscripts'"
date: 2011-12-02
forum: General Help
---

### Post by Silvernail on 2011-12-02
I would like to put all my scripts that I write for special jobs into one source directory.  I forget the exact names and spend too much time looking for  them.

I went to /usr/bin and created this: '/usr/bin/myscripts/' with permissions 755.

A test produced this:
```

dave@dave:~$ echotest.sh
echotest.sh: command not found

```

To prove the file worked:
```

dave@dave:~$ /usr/bin/myscripts/echotest.sh
testing the new directory in /usr/bin

```

I would like to be able to list /usr/bin/myscripts to confirm the correct name of the script I want to run. Can I do that? How?

---

### Post by Vaphell on 2011-12-02
PATH variable, it doesn't have /usr/bin/myscripts
besides you can store your scripts in your home in bin folder. Ubuntu is configured to pick up existing ~/bin folder and add it to PATH automatically.

---

### Post by Silvernail on 2011-12-02
I wish I had known that, I would no have ask.

For my own knowledge:
I could export a new director to PATH?

---

### Post by mutley89 on 2011-12-02
```

export PATH=$PATH:/directory/to/add

```stick this on the end of your .bashrc to make it permanent

---

### Post by btindie on 2011-12-02
The convention is to put your on personal scripts into ~/bin  (e.g. /home/username/bin) and scripts that are to be available to all users in /usr/local/bin. You can see what the PATH variable is set to by typing
```
echo $PATH
```

---

