---
title: "E: Couldn't find package build"
date: 2010-06-27
forum: General Help
---

### Post by alperkayisi on 2010-06-27
Hi guys,

When I type this command ;

sudo apt-get install build essential

I got this ;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build

but I can run" ./configure" and" make" command. But I couldn't run make install command pls help me out . when I run make install I got ;

the file name is nmap-5.21

lper@ubuntu:~/nmap-5.21$ make install
g++ -c -Iliblua -Ilibdnet-stripped/include -Ilibpcre  -Ilibpcap -Inbase -Insock/include   -DHAVE_CONFIG_H -DNMAP_NAME=\"Nmap\" -DNMAP_URL=\"http://nmap.org\" -DNMAP_PLATFORM=\"x86_64-unknown-linux-gnu\" -DNMAPDATADIR=\"/usr/local/share/nmap\" -D_FORTIFY_SOURCE=2 main.cc -o main.o
make: g++: Command not found
make: *** [main.o] Error 127
What is wrong with that ?

---

### Post by ibuclaw on 2010-06-27
You're missing the hi-fen in the package name.

```
sudo apt-get install build-essential
```

Regards

---

### Post by alperkayisi on 2010-06-27
Thanks a lot bro. but I am new at ubuntu, so my question may sounds silly to you but I have to ask that :) . commands are succesfully runned and my package successfully installed. my question is how can I open it

---

