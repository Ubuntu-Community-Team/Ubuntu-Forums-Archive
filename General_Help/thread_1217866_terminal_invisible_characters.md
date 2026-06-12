---
title: "terminal invisible characters"
date: 2009-07-20
forum: General Help
---

### Post by krishna1650 on 2009-07-20
hello friends,
can anyone tell me how to make input characters invisible in terminal? for example for logging we have to enter password, that password is not shown in the terminal. 

thank you for your help.

---

### Post by aloshbennett on 2009-07-20
Depends on the scripting/programming language you are using.
In bash, you can use the following to turn off echo and read password:

```

echo "enter password"
stty -echo
read password
stty echo
echo "Really? $password? Thats not good enough"

```

---

### Post by krishna1650 on 2009-07-22
> **aloshbennett said:**
> Depends on the scripting/programming language you are using.
In bash, you can use the following to turn off echo and read password:

```

echo "enter password"
stty -echo
read password
stty echo
echo "Really? $password? Thats not good enough"

```
thank you for the reply, it's working.

---

