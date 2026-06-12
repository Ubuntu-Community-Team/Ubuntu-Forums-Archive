---
title: "&quot;NooB&quot; learning C++"
date: 2012-06-14
forum: General Help
---

### Post by handofdave on 2012-06-14
i am just beginning to learn the ubuntu/linux os, while at the same time i'm also teaching myself C++, Html, Javascript, and Python. i know that this is a lot to do at one time but i figured that it wouldn't hurt to give it a shot. my problem is that i don't know how to even begin to compile the code or run it. i dont want to use one of those crazy ides--right now they seem a little to menacing, and besides the best way to learn linux is through terminal, right. So could someone please assist me in explaining how to compile my code. Please remember that i am a "NooB" so some terminology may be above my head.
thank you for your help.

---

### Post by steeldriver on 2012-06-14
1. install the build-essential meta package (it's more than you need at this stage, but it will make sure you get all the build tools and libs)

```
sudo apt-get install build-essential
```2. open a text editor and paste in the following

```
#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!" << endl;
  return 0;
}
```save the file as "helloworld.cpp"

3. open a terminal, 'cd' to the directory containing your new .cpp file,  and type

```
g++ -Wall -o helloworld helloworld.cpp
```4. run your program

```
./helloworld
```

BTW there is a whole subforum for Development and Programming questions

---

### Post by speel on 2012-06-14
Awesome! a little advice tho since you're just starting go with python, it pretty high level meaning it's as close to "english" as you can get. But hey good luck!

---

### Post by jmfal on 2012-06-14
Welcome to ubuntu and programming.

I use codeblocks with emacs(gui), its in synaptics.

It is similar to Visual Basics C++

A couple of places to start:

New Boston> Buckys Tutorials> C++

During my C++ class this spring they  were in the process of putting all the tutorials on youtube, look there.

You can try the "Khan Academy"  there are alot of tutorials on all types of programming and college courses

Good Luck!.

---

### Post by oldos2er on 2012-06-14
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Simian Man on 2012-06-14
> **handofdave said:**
> i am just beginning to learn the ubuntu/linux os, while at the same time i'm also teaching myself C++, Html, Javascript, and Python. i know that this is a lot to do at one time but i figured that it wouldn't hurt to give it a shot. 
That is a horrible idea, all of those languages are quite difficult on your own.  You won't learn anything by splitting up your effort like that.  Pick one - I'd recommend Python - and stick with it.

---

### Post by handofdave on 2012-06-15
thanks guys i really do appreciate all of the advice. thanks again

---

