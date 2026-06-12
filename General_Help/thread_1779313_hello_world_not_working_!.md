---
title: "hello world not working !"
date: 2011-06-10
forum: General Help
---

### Post by elliotbeken on 2011-06-10
Hi all,

i have tried to create a hello world bash script and it does not work!

the code i used is:
>  #!/bin/bash         

echo "Hello, World"i have names the script "hello.sh" and it was created in nano.

i have also changed the permissions to a+x on the file

if i run the file in terminal or just run it opens a terminal windows and just closes.

what have i done wrong ?

thanks

---

### Post by amalbose on 2011-06-10
u can run it from terminal itself. navigate to the folder having the hello.sh file and type in:
```
./hello.sh
```

---

### Post by elliotbeken on 2011-06-10
yes that works

is there a way that i can show it in a message box in the top right ?

---

### Post by Habitual on 2011-06-10
```
notify-send "Hello World"
```

---

### Post by ghostborg on 2011-06-10
If you get a command not found for notify-send you can install it
by ```
sudo apt-get install libnotify-bin
```

---

### Post by elliotbeken on 2011-06-10
thanks for the help

---

