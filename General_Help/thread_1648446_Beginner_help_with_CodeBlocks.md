---
title: "Beginner help with Code::Blocks"
date: 2010-12-18
forum: General Help
---

### Post by vacco on 2010-12-18
I am looking into learning  some basic C++ programming, and installed Code::Blocks as recommended by the tutorials I've found. I followed [this]("http://www.cprogramming.com/code_blocks/") guide for setting it up, although it is for Windows. I've come as far as opening a new project with the code for the Hello World program already there, but nothing happens when I try to build or run it. :(

Also, in the Windows tutorial, Pressing F9 compiles the code to a .exe. What is the outcome in Ubuntu supposed to be? A .bin?

---

### Post by 3Miro on 2010-12-18
My guess is that you don't have a compiler installed. Go to System -> Admin -> Synaptic Package Manager and install gcc and g++. Or from the terminal:
```
 sudo apt-get install gcc g++ 
```

You can test to see if it works. Put this into some text file:
```
 #include <iostream>
int main( int argc, char **argv ){
std::cout << "Hello World" << std::endl;
return 0;
}; 
```

Then you should be able to compile it form the terminal:
```
 g++ input_file.cpp -o executable_name 
```
If you don't give it executable name, the default is "a.out".

---

### Post by vacco on 2010-12-18
I was thinking something like that too, but both gcc and g++ appears to be installed. The problem seems to be related to the running of the binaries, rather than the building of them. Binaries are created in the project's bin folder when I click build, but will not run, whatsoever. I have also tried double clicking them from Nautilus with no luck, even though the "allow to run" checkbox is checked. The only way I can make it run is launching it through the terminal (./main.cpp)

Note: The program should indeed run in terminal, but I thought the terminal window should open automatically when required by an application, as it does when I launch Octave (which also run in terminal) from the programs menu.

---

### Post by 3Miro on 2010-12-18
> **vacco said:**
> I was thinking something like that too, but both gcc and g++ appears to be installed. The problem seems to be related to the running of the binaries, rather than the building of them. Binaries are created in the project's bin folder when I click build, but will not run, whatsoever. I have also tried double clicking them from Nautilus with no luck, even though the "allow to run" checkbox is checked. The only way I can make it run is launching it through the terminal (./main.cpp)

Note: The program should indeed run in terminal, but I thought the terminal window should open automatically when required by an application, as it does when I launch Octave (which also run in terminal) from the programs menu.

There should be a command "Run in terminal". Otherwise, most of us do keep an open terminal when coding. Look for a "run" option in Code::Blocks too, it should automatically open a terminal for you (I know Geany does). It may have to be set up.

It should be ./program and your program should not be called main.cpp

---

### Post by 3Miro on 2010-12-18
You can use Ctr + F10 (from Build menu). You may have to change the terminal program. Go to Settings -> Environment -> General Settings -> Terminal to launch .... Then make sure you have the following:
```
gnome-terminal -x
```

---

### Post by vacco on 2010-12-18
I have already tried both the "Run" and the "Build and run" buttons in CB, without success. Keeping a terminal window in the background did not help much either. Should the "Run in terminal" option be somewhere under the Build menu or...?
How would I go to configure the terminal to automatically open?

---

### Post by 3Miro on 2010-12-18
> **vacco said:**
> I have already tried both the "Run" and the "Build and run" buttons in CB, without success. Keeping a terminal window in the background did not help much either. Should the "Run in terminal" option be somewhere under the Build menu or...?
How would I go to configure the terminal to automatically open?

Did you get my second post. Make sure you have gnome-terminal set. If not, you should get an error message at the bottom of Code::Blocks. You can post that for us to see what is happening.

Keeping a terminal open helps me by being able to quickly Alt + Tab into it to run the program and then Alt + Tab back to Code::Blocks. Sorry if it wasn't clear enough.

Nautilus may have a right-click "Run in terminal" option.

---

### Post by vacco on 2011-01-06
Just thought I'd mention I found a solution in case it could be helpful to anybody.

Now, I discovered this after a reinstall where everything was working so I cannot be 100% sure this is it, but I *think* xterm which Code::blocks opens command line applications in by default, somehow was not installed (even though it is my understanding that it is a dependency of CB).

---

