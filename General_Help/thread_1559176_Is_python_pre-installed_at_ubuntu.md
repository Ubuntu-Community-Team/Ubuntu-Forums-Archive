---
title: "Is python pre-installed at ubuntu?"
date: 2010-08-23
forum: General Help
---

### Post by hakermania on 2010-08-23
So, can somebody with Ubuntu, having done all its updates to run a python file or has to install a package first?

---

### Post by Primefalcon on 2010-08-23
> **hakermania said:**
> So, can somebody with Ubuntu, having done all its updates to run a python file or has to install a package first?
yup open a terminal and type

```
python --version
```

To see what version you are running

---

### Post by hakermania on 2010-08-23
No no, that's not the point...
i am making a program and idk if I have to tell the users how to install python or not

---

### Post by d3v1150m471c on 2010-08-23
don't
```

if which python >/dev/null
  then
      echo "python installed"
  else
     sudo apt-get install python
     # or yum install
fi

```

---

### Post by hakermania on 2010-08-23
So python is not pre-installed......!!!?!?!?!?
How is this possible?
A lot of pre-installed programs use a combination of python and C to run.....

---

### Post by lykeion on 2010-08-23
[https://help.ubuntu.com/community/PowerUsersProgramming#Python](https://help.ubuntu.com/community/PowerUsersProgramming#Python)

---

### Post by Bachstelze on 2010-08-23
> **hakermania said:**
> So python is not pre-installed

Of course it is....

---

### Post by hakermania on 2010-08-23
Fiouffff
cool thank you!

---

