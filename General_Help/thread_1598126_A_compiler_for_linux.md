---
title: "A compiler for linux?"
date: 2010-10-16
forum: General Help
---

### Post by Blue Summer on 2010-10-16
I downloaded dev c++ by bloodshed and ran it wine, it all works but the graphics are very sluggish, don't know weather that's because I'm using the latest one (my fps drops in WoW now after the new patch aswel). Anyways I'm looking for a linux compiler that's similar to bloodsheds dev c++, that GCC compiler looks far too advanced and I've got to do all sorts of crap with it to get it to work, is there no .deb file I can install of it or something?

---

### Post by Zteam on 2010-10-16
I'm not really sure what you are looking for, but GCC and Codeblocks (this is not a compiler but a IDE to the compiler and a editor) is very nice :)

Otherwise just look for other c++ compilers in synaptic or software center

---

### Post by Blue Summer on 2010-10-16
> **Zteam said:**
> I'm not really sure what you are looking for, but GCC and Codeblocks (this is not a compiler but a IDE to the compiler and a editor) is very nice :)

Otherwise just look for other c++ compilers in synaptic or software center

I'm just looking for something to compile and run my programs for college. Something exactly the same as dev c++

---

### Post by binarylife on 2010-10-16
> **Blue Summer said:**
> I'm just looking for something to compile and run my programs for college. Something exactly the same as dev c++

Download and install Code:blocks IDE form ubuntu software center.
then use this code in terminal to install the compiler, it is also used for C++:
```

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install build-essential
$ gcc -v
$ make -v
```

---

### Post by Blue Summer on 2010-10-16
Cheers for that mate, where should the icon for it be? Can't find it in my lists

edit: Nvm found it thanks alot mate. Had to reinstall it, desktop messed up so had to log before it had done :)

double edit: Can't find iostream.h wtf?

---

### Post by Topsiho on 2010-10-16
iostream.h is obsolete for quite some years now and replaced with iostream

An example of C++ programming new style:

#include <iostream>
using namespace std;

int main()
{
cout << (317 + 52);
return 0;
cin.get;  //if necessary to wait for the keyboard to see result
}

Hope this helps to solve THIS problem :)

Topsiho

---

### Post by Blue Summer on 2010-10-16
Right... So all I have to do is put <iostream> and using namespace:std

I use system pause for the last part :)

---

### Post by James78 on 2010-10-16
Additionally, you should check out (and bookmark) [CPlusPlus]("http://www.cplusplus.com/reference/"). They'll show you what headers to use, and even what's in them.

---

### Post by Blue Summer on 2010-10-16
> **James78 said:**
> Additionally, you should check out (and bookmark) [CPlusPlus]("http://www.cplusplus.com/reference/"). They'll show you what headers to use, and even what's in them.

Thanks, I've used cplusplus quite alot they've got some great information. Just trying to wrap my head around what the hell a structure is, I understand a class (didn't get taught about sub classes for some reason) but I don't understand what a structure is, time to read a cplusplus tutorial lol

edit: Now I've just realised I don't have to know what a "structure" is it's a constructor rofflecaeks

---

