---
title: "csh"
date: 2010-05-23
forum: General Help
---

### Post by vukaragol on 2010-05-23
Hi everyone

bash shell is deafult in my ubuntu and i need to use csh shell to write a script for Generic mapping tools.
Can use csh while bash is still the deafult shell

forgive me if this is a silly question :)

---

### Post by dearingj on 2010-05-23
Sure you can. Just install csh like this:
```
sudo apt-get install csh
```

then put as the first line of your script file:
```
#!/bin/csh
```

That line tells Ubuntu to always run the script through csh.

---

### Post by vukaragol on 2010-05-23
thank you :)

---

