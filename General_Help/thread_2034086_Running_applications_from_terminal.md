---
title: "Running applications from terminal?"
date: 2012-07-27
forum: General Help
---

### Post by Redshft on 2012-07-27
Hello,
I am a C++ programmer and I just started using Ubuntu for work however I'm having trouble figuring out how to run applications through the terminal. What I normally do is cd to the location of the application and then type in the name of the application in the terminal. This doesn't work all of the time.

For example, I just wrote a simple program that outputs text to console to test this. I did this:

cd workspace/C++/Test/Debug
Test
No command 'Test' found, did you mean:
Command 'test' from package 'coreutils' (main)

Test is the name of the application. What am I missing?

---

### Post by papibe on 2012-07-27
Hi Redshft. Welcome to the forums ):P

Every thing you try to run will be looked on the PATH. For security reasons the current directory it is not included on the PATH.

You can easily run a command in the current directory by saying explicitly it is in the current directory:
```
./Test
```
Hope that helps. Come here often and have fun.
Regards.

BTW: you can print the current search PATH by running:
```
echo $PATH
```

---

### Post by matt_symes on 2012-07-27
Hi

If you're in the same directory as the executable then run it like this..

```
./Test
```

Kind regards

---

