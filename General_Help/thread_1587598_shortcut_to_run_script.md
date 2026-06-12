---
title: "shortcut to run script"
date: 2010-10-03
forum: General Help
---

### Post by l3ecl on 2010-10-03
i wrote a hello world script using bash and i'm trying to run this script via terminal by pressing F1, but it is not working.

my hello world script is: ```
 #!/bin/bash          
          echo Hello World    
        
```



in the keyboard shorts of ubuntu, i have F1 as: ```

gnome-terminal /home/user/hello_world_script
```

i'm obviously doing it wrong, but i would like to learn the proper way

---

### Post by l3ecl on 2010-10-03
if it makes any difference the script has a chmod of 700

---

### Post by aeronutt on 2010-10-03
Try

```
gnome-terminal -e /home/user/hello_world_script
```

---

### Post by l3ecl on 2010-10-04
i get an error stating :

```
There was an error creating the child process for this terminal
```

---

### Post by l3ecl on 2010-10-04
```
gnome-terminal -e /home/user/hello_world_script

```
gives me an error stating:

```
There was an error creating the child process for this terminal
```

---

