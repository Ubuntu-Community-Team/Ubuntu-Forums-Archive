---
title: "Installing C++ Program"
date: 2010-05-10
forum: General Help
---

### Post by SkrunchBoy on 2010-05-10
Trying to install a c++ program, i have CodeBlocks and Code Lite on here, but none work, can somebody give me a step by step guide on how to install it and get it working please

Thanks

---

### Post by nothingspecial on 2010-05-10
Are you trying to compile a self written C++ program.

If so
```

sudo apt-get install build-essential
```

Then try again.

If not, what are you trying to install?

---

### Post by SkrunchBoy on 2010-05-10
Trying to install a program that will allow me to create and run self made c++ items... install Code Lite program and it wouldn't compile!

---

### Post by nothingspecial on 2010-05-10
```
sudo apt-get install g++
```

```
g++ name_of_file _you_want_to_compile -o what_you_want_your_prorgam_to_be_called
```

```
chmod +x new_compiled_program
```

```
./new_compiled_program
```

---

### Post by undrline on 2010-06-21
I only have experience with CodeBlocks in Windows.  I found it was very similar to Dev-C++, which has a Linux version.  Why don't you give Dev-C++ a try, and see if it suits your needs:
[http://sourceforge.net/projects/dev-cpp/](http://sourceforge.net/projects/dev-cpp/)

---

