---
title: "how do I use G++ on Ubuntu 11.04"
date: 2011-09-13
forum: General Help
---

### Post by hard knock on 2011-09-13
I need a step by step on how to use g++/C++ on ubuntu 11.04 
I usually use visual studio but I want to learn how to write C++ on Linux
Please help!!!

---

### Post by seawolf167 on 2011-09-13
You can use any text editor to write your code, like *gedit*. Once you write the code, from a terminal in your working directory, type in

```
g++ input_file_name.cpp
```

then to run your program

```
./a.out
```

Alternatively, you can use the -o switch to specify an "outfile", or a program like *geany* as a "one-stop-shop"

```
g++ -o output_file_name input_file_name.cpp
```

```
sudo apt-get install geany
```

---

