---
title: "How to run c programs"
date: 2006-04-08
forum: General Help
---

### Post by Anilkumar on 2006-04-08
Hi everybody,

I want to run C programs in Linux.

so what is the procedure i need to do? 
What are the packages i need to install?
How can i Install them

previously i used to do them in windows now i am willing to do all my software work in linux

so please guide me

---

### Post by elsupermang on 2006-04-08
Basically you just need gcc make libstdc, just install the build-essential package and it will download what you need. As far as compiling for simple programs you can just type make helloworld for example. As far as some of the IDE's you should look into Anjuta for a native gnome interface or Kdevelop for KDE, you can run them on both window managers so its just a matter of preference.

---

### Post by taurus on 2006-04-08
Applications -> Accessories -> Terminal
```

sudo apt-get install build-essential  <-- to install c compile and related files
gcc program_name.c  <-- to compile it
./a.out  <-- to execute it

```

---

### Post by Anilkumar on 2006-04-13
Thanq u very much for u r support

---

