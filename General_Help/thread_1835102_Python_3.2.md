---
title: "Python 3.2"
date: 2011-08-28
forum: General Help
---

### Post by AnotherMuggle on 2011-08-28
Evening All,

I can see that Ubuntu 11.04 has Python 2.7 installed by default.  I have some code I want to run which requires 3.2.  Is anyone able to tell me what the correct procedure is to get 3.2 installed on my computer?

Do I install 3.2 alongside 2.7?  Remove 2.7 first?  Does 2.7 get updated?

Thanks in advance,
TK

---

### Post by angryfirelord on 2011-08-28
All you'll have to do is just install python3.2 from apt-get. You can keep both versions, but Python 3.2 will be executed by using python3 instead of just the python command.

---

### Post by cgroza on 2011-08-28
You can install Python3.2 but do not remove Python2.7. It is still needed by your system.
You can invoke Python3.2 with:
```
python3.2 
```

---

### Post by AnotherMuggle on 2011-08-29
Fantastic, I love straightforward solutions like this. 

Thank you both.

---

