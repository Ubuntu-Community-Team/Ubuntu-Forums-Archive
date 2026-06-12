---
title: "cd / command wont work with live cd?"
date: 2012-04-03
forum: General Help
---

### Post by buggetjr on 2012-04-03
Hello, I have a school assignment where I would use the command line "cd /". It is said that I should now be located in root level of my file system but in my case nothing is happening ? Although every other command line in the assignment works fine. Worth mention is that I use the new ubuntu and i run it from a live cd. 

Would be grateful for any kind of help though I google it without any success and it driving me crazy :mad:

---

### Post by HiImTye on 2012-04-03
```
tye@T:~$ cd **/**
tye@T:**/**$ cd **~**
tye@T:**~**$ cd **/home**
tye@T:**/home**$ cd **/**
tye@T:**/**$ cd** ~**
tye@T:**~**$ 
```there is no 'output' from the command but as you can see, there is a difference after it is given, indicated by your current folder, directly before the $ (indicating BASH)

/ is the root folder (the very top level of your file system) all files and folders come after that
~ is a shorthand display of your home folder ($HOME). on Ubuntu, that is typically '/home/<your_username>/' for instance:
```
tye@T:~$ cd /home/tye/
tye@T:~$
```as you can see, it is still displaying simply '~'
```
tye@T:~$ cd ~/Videos
tye@T:~/Videos$ cd $HOME/Videos
tye@T:~/Videos$ cd /home/tye/Videos
tye@T:~/Videos$ 
```
are all the same folder

---

### Post by codemaniac on 2012-04-03
after changing your current directory with cd command , use **pwd ** command to check the path you are standing on .

---

