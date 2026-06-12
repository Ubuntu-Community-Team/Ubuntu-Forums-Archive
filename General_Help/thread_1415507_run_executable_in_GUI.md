---
title: "run executable in GUI"
date: 2010-02-24
forum: General Help
---

### Post by JarrettK on 2010-02-24
I do alot pf C++, I like that I can just type "g++ myprogram.cpp" and it will comile into an executable, but when I try to run it in the terminal by double clicking or right clicking and choosing open nothing happens. The program works perfectly if I do 

```
./myprogram.out
```

but when I double click it, and choose "run in termminal", nothinh happens. How can I get it configured to open the terminal and run when run it from GUI?

---

### Post by lavinog on 2010-02-24
what does the program do?
Is it possible that the program is exiting when complete?  If so, the terminal might be closing before it is fully displayed.

Add some user interaction before the program exits.

---

### Post by JarrettK on 2010-02-24
I thought of that too, so I made one that ask for user input then exits:

```
#include <iostream>
int main(void) {
     std :: cout << "type something: ";
     char x[255];
     std :: cin >> x;
     return 0;
}
```

this works in terminal, but in GUI nothing happens.

---

### Post by d3v1150m471c on 2010-02-24
Is the program written as a GUI?

---

### Post by JarrettK on 2010-02-24
No, its just some Console C++, I'm sort of new to Ubuntu and Ive been using windows for quite some time ... I know that running that exact exe file in windows would open a console window and run ...but i'm not sure if its the same thing for Ubuntu, or if it is but I need to configure something.

---

### Post by d3v1150m471c on 2010-02-24
it isn't opening a terminal because it's not written to do so. I don't know c++ but say it were bash it would need something like 
```

xterm -e ./yourprogram

```

---

### Post by JarrettK on 2010-02-24
Strange ...............
the equivelent (I assume) to that in C++ is:

```
system("~/Desktop/myprogram.out");
```which should open a terminal and then open a.out in the terminal, which also diud nothing when i clicked on it. I noticed that when I right click it the first option just says "Open" not a specific program or command. Maybe there is a command I need to run .out files with?

A few minutes after running it my screen went black and started to print "kill process (myprogram.out) killing child processes and i turned my computer off.

---

### Post by d3v1150m471c on 2010-02-24
try this
```

system("xterm -e ./Desktop/myprogram.out")

```or
```

system("xterm -e ./home/Desktop/myprogram.out")

```

---

### Post by JarrettK on 2010-02-24
Thanks! That worked perfectly.

---

### Post by d3v1150m471c on 2010-02-24
lol and I don't even know c++. w00t

---

