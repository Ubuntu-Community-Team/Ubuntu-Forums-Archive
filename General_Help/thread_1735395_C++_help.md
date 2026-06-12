---
title: "C++ help"
date: 2011-04-21
forum: General Help
---

### Post by pottsiex5 on 2011-04-21
Hi, 
Im quite new to Ubuntu and am still trying to figure things out. I recently started learning C++, but i am having some problems. 

I installed build-essential and started to write my code. My code is:

#incluude <iostream>

int main()
{
      std::cout << "Hello World!\n";
      return 0;
}


I write that in Text Editor and save it as hello.cpp 
Heres my problem, what do i do now? ive tried "g++ -o hello.cpp" but i dont know what is wrong... how do i run the program and what should happen, thanks :)

---

### Post by TheStroj on 2011-04-21
Thats not enough:

Here's what you need to do:

```
g++ [arguments] file.cpp -o executable_name
```

Insted of [arguments] use a real argument, like -Wall, or nothing at all.
then run it with:_
```
./executable_name
```

---

### Post by Foxcow on 2011-04-21
For the sake of simplicity, I recommend:

```
 g++ file.cpp
```

the default executable will be called "a.out."  Then:

```
./a.out
```


The way that TheStroj described it above is a better way to do it.

---

### Post by seawolf167 on 2011-04-21
Just want to add that I really like Geany when writing code, I think you may like it even more since you can compile/run the program with a single click so you can bypass the manual g++ commands

```
sudo apt-get install geany
```

---

### Post by pottsiex5 on 2011-04-21
Thanks very much! I got it to work :)

---

