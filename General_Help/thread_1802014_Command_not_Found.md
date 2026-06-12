---
title: "Command not Found"
date: 2011-07-11
forum: General Help
---

### Post by aguilla1 on 2011-07-11
I have copied a printer driver update to 'home/Downloads/'
When I use dir, it shows install.sh 
When I check properties it shows install.sh is executable
When I type in sudo install.sh it claims Command not found.
When I double click the install.sh icon, it allows me to run it, but fails since I can not use sudo. The terminal screen disappears, so I can not read it. 
When I just run it, the installer package software says it is not a package.

What do I do? What did I do wrong?

---

### Post by Surendil on 2011-07-11
On terminal

```
 sudo ./install.sh 
```

---

### Post by haqking on 2011-07-11
> **aguilla1 said:**
> I have copied a printer driver update to 'home/Downloads/'
When I use dir, it shows install.sh 
When I check properties it shows install.sh is executable
When I type in sudo install.sh it claims Command not found.
When I double click the install.sh icon, it allows me to run it, but fails since I can not use sudo. The terminal screen disappears, so I can not read it. 
When I just run it, the installer package software says it is not a package.

What do I do? What did I do wrong?

first of all though Dir is supported, you are best using ls

also you need to use ./install.sh

append the ./ before the command executable

you will probably need sudo ./install.sh to be specific.

---

### Post by aguilla1 on 2011-07-11
yes, of course, How did I forget!!

Thanks for replying so quickly.:D

---

