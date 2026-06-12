---
title: "g++ and gcc , cant find libraries"
date: 2010-06-26
forum: General Help
---

### Post by lordbux on 2010-06-26
Hi

I was have installed gcc and g++ both 4.4.3 Version

They were working fine, but now they suddenly seem to have lost track.
Both cant detect standard library files.

not even iostream ,fstream. (i have already tried the .h variant):confused:

my /usr/local/include/ directory is empty, should not something be there.:confused:

Please Help I am in an emergency::confused:

thanks in advance

---

### Post by lordbux on 2010-06-26
BUMP:

Sorry for the early one, but am in EMERGENCY

---

### Post by gmargo on 2010-06-26
What did you do just before it stopped working?  Don't say nothing. :-)

Since you don't provide any information, it's impossible to diagnose a problem.  Can you compile a simple hello world program?  Show us a simple program that you think should work but doesn't.

Why do you think something should be in /usr/local/include?  No ubuntu-supplied packages will install anything there.  You didn't try to compile gcc did you?

---

### Post by lordbux on 2010-06-27
> **gmargo said:**
> What did you do just before it stopped working?  Don't say nothing. :-)

Since you don't provide any information, it's impossible to diagnose a problem.  Can you compile a simple hello world program?  Show us a simple program that you think should work but doesn't.

Why do you think something should be in /usr/local/include?  No ubuntu-supplied packages will install anything there.  You didn't try to compile gcc did you?

*I Did not compile gcc , i installed it using apt-get.

Compiling a simply program as: ```
[B]#include<iostream.h>

int main()
{

cout<<"Hello :: Helo";

}[/B]
```

GIVES the error:
```

df.cpp:1:21: error: iostream.h: No such file or directory
df.cpp: In function ‘int main()’:
df.cpp:6: error: ‘cout’ was not declared in this scope

```

The basic problem is that the compiler could not locate the library files.

The only thing i can remember doing before the crash is that
i changed my hard disk onto a new machine (both Intel Procs):confused:

---

### Post by stderr on 2010-06-27
/usr/local/include - not really, no.

You want to use 
```
#include <iostream>
```

Also, you should probably include

```
 using namespace std;
```
after that so as not to have to use std::cout etc.

Are you sure you're compiling with g++ and not gcc?

---

### Post by lordbux on 2010-06-27
**already tried all the variations.**

both , iostream and iostream.h

*where are the library files located in ubuntu.

My problem is that the compilers cant find the library files.
Please help i  am in an  absolute emergency.

---

### Post by stderr on 2010-06-27
> **lordbux said:**
> *where are the library files located in ubuntu.

Headers: /usr/include/c++/<VERSION>/

And I don't know if I made it clear enough in my last post, but every system would return the same compiler errors for that input text as you posted, because the errors it's pointing out are valid errors in your code. You need to use <iostream> and you need to set the namespace for cout, either through "using namespace std;" or by explicitly calling "std::cout".

On my system:

```
#include <iostream.h>

int main() {
  cout << "Hello :: Helo";
}
```

Compile:

```
g++ -o df df.cpp
df.cpp:1:22: error: iostream.h: No such file or directory
df.cpp: In function &#8216;int main()&#8217;:
df.cpp:6: error: &#8216;cout&#8217; was not declared in this scope
```

Using corrected code:

```
#include <iostream>

int main() {
  std::cout << "Hello :: Helo";
}
```

Compile:

```
g++ -o df df.cpp
```

---

### Post by lordbux on 2010-06-27
> **stderr said:**
> Headers: /usr/include/c++/<VERSION>/

And I don't know if I made it clear enough in my last post, but every system would return the same compiler errors for that input text as you posted, because the errors it's pointing out are valid errors in your code. You need to use <iostream> and you need to set the namespace for cout, either through "using namespace std;" or by explicitly calling "std::cout".

On my system:

```
#include <iostream.h>

int main() {
  cout << "Hello :: Helo";
}
```

Compile:

```
g++ -o df df.cpp
df.cpp:1:22: error: iostream.h: No such file or directory
df.cpp: In function ‘int main()’:
df.cpp:6: error: ‘cout’ was not declared in this scope
```

Using corrected code:

```
#include <iostream>

int main() {
  std::cout << "Hello :: Helo";
}
```

Compile:

```
g++ -o df df.cpp
```

[B]
PROBLEMS:::[/B]
*/usr/include/c++/<VERSION>/  ===> **/usr/include/ is empty not even c++**
* tried namespace std; == Still wont find library:

---

### Post by stderr on 2010-06-27
Hmm, try installing libstdc++6-4.4-dev

```
sudo apt-get install libstdc++6-4.4-dev
```

Also you can see if you've got, e.g. iostream, anywhere else under /usr:

```
find /usr -name iostream
```

---

### Post by gmargo on 2010-06-27
> **lordbux said:**
> [B]
PROBLEMS:::[/B]
*/usr/include/c++/<VERSION>/  ===> **/usr/include/ is empty not even c++**


That's a pretty big problem.  Have you installed the **build-essential** package?

---

### Post by lordbux on 2010-06-30
> **gmargo said:**
> That's a pretty big problem.  Have you installed the **build-essential** package?

It seems build-essential was not installed , but still i am having the  trouble like. 


```
In file included from /usr/include/c++/4.3/bits/postypes.h:47,
                 from /usr/include/c++/4.3/iosfwd:47,
                 from /usr/include/c++/4.3/ios:44,
                 from /usr/include/c++/4.3/istream:45,
                 from /usr/include/c++/4.3/fstream:45,
                 from libvistax.h:5:
```

```
libvistax.h: In function ‘int passw(char*)’:
libvistax.h:24: error: ‘strcpy’ was not declared in this scope
libvistax.h: In function ‘int wtest(char*)’:
libvistax.h:35: error: ‘strcpy’ was not declared in this scope
libvistax.h:36: error: ‘ofstream’ was not declared in this scope
libvistax.h:36: error: expected ‘;’ before ‘tet’
libvistax.h:37: error: ‘strcat’ was not declared in this scope
libvistax.h:38: error: ‘tet’ was not declared in this scope
libvistax.h:45: error: ‘system’ was not declared in this scope
libvistax.h:49: error: ‘cout’ was not declared in this scope
libvistax.h: In function ‘void alcen(char*)’:
libvistax.h:56: error: ‘strlen’ was not declared in this scope
libvistax.h:57: error: ‘cout’ was not declared in this scope
libvistax.h:58: error: ‘cout’ was not declared in this scope
libvistax.h: In function ‘int random(int)’:


and lot more..till end

```

---

### Post by pedro_orange on 2010-06-30
Have you included the correct header files?
Also, have you included the std namespace?

```
using namespace std;
```

---

### Post by lordbux on 2010-07-02
using "name space std" solved that problem 

thank you everyone  BUT i am having a new trouble, 

i am using netbeans IDE and it is giving an error that

fstream, iostream, stdio.h, unistd 

have unresolved includes in them, ..what should i do.

is there somehow i can get the old original iosteam.h , fstream.h and other binaries 
the new set is just a mess.

Please help. Thanks in advance

---

### Post by stderr on 2010-07-02
Indeed, it was never going to work without using namespace std or a std:: prefix. You need to remember that in C++, functions are called relative to a [namespace]("http://en.wikipedia.org/wiki/Namespace_%28computer_science%29").

I would personally recommend when you're starting out programming cpp that you start on the command line - this way you can much more easily grasp the basic concepts. When you can code simple programs straight, write the compilation commands, etc, then you've got a solid starting point to move to a GUI-based IDE. IDEs, in my experience, tend to make large projects slightly more manageable, and small projects longer & harder. Anyway...

Unresolved includes probably means your header paths are set incorrectly - in your case, in the NetBeans IDE preferences.

---

### Post by lordbux on 2010-07-03
> **stderr said:**
> Indeed, it was never going to work without using namespace std or a std:: prefix. You need to remember that in C++, functions are called relative to a [namespace]("http://en.wikipedia.org/wiki/Namespace_%28computer_science%29").

I would personally recommend when you're starting out programming cpp that you start on the command line - this way you can much more easily grasp the basic concepts. When you can code simple programs straight, write the compilation commands, etc, then you've got a solid starting point to move to a GUI-based IDE. IDEs, in my experience, tend to make large projects slightly more manageable, and small projects longer & harder. Anyway...

Unresolved includes probably means your header paths are set incorrectly - in your case, in the NetBeans IDE preferences.


I have been working on cpp for the last 5 years.
and i made a switch to gcc and g++ only 2 years back.
till then i used to use Turbo C++.
and everything was fine first , then suddenly with an update, my compilers went absolutely mad, the **iostream.h and fstream.h everything became iostream fstream **..etc.  the till then i could do without "namespace std". and now it wont do without it.

**and the file.eof() function just vanished, it says there nothing exist calls eof.  **
I am in middle of a important projecta nd it seems i have to rewrite the entire 80,000 lines of code again. to adjust to the new changes which i don't understand the reason for. 

**+ i am getting many unresolved dependencies from header files. it seems includes inside the header files are too missing. **

is there any way i can get my old compiler and libraries back.

---

### Post by stderr on 2010-07-03
Hmm, considering that I think we need to know more about what changed on your system to cause you all these problems. 

Can you crosscheck your recently updated/changed package list against the date/time you first started experiencing these problems?

System->Admin->Synaptic, File->History.

Also can you post the output of 

```
ls -l $(whereis g++ | awk '{ print $2 }')
```

and

```
sudo dpkg -l libstdc++*
```

edit: I would add that the behavior you're now experiencing is what I've been used to for years, and that it's been my understanding that references such as <iostream.h> have been deprecated for many years, due to the introduction of namespaces. So I'm pretty interested to see what you have been using and what's happened... maybe such things have still been supported as deprecated for ages and now with g++ 4.4 they've finally removed support - don't know.

---

### Post by stderr on 2010-07-03
You'd probably have success rolling back to an early g++ version and early libs - something like this:

[http://www.linuxquestions.org/questions/programming-9/help-finding-deprecated-c-libraries-iostream-h-fstream-h-734338/]("http://www.linuxquestions.org/questions/programming-9/help-finding-deprecated-c-libraries-iostream-h-fstream-h-734338/")

---

### Post by lordbux on 2010-07-03
> **stderr said:**
> You'd probably have success rolling back to an early g++ version and early libs - something like this:

[http://www.linuxquestions.org/questions/programming-9/help-finding-deprecated-c-libraries-iostream-h-fstream-h-734338/]("http://www.linuxquestions.org/questions/programming-9/help-finding-deprecated-c-libraries-iostream-h-fstream-h-734338/")



You were rite, the problem was due to the updated libraries and compiler.

it seems compiling in command line solves a great deal of problem.
and a few renaming made easier, though i am sure that somewhere
in future i may face a few errors as i have renamed iostream to iostream.h and etc.
 
Thanks for all your kind support, 
You guys make linux Beat. :popcorn: :)

---

### Post by COKEDUDE on 2010-07-03
Does anyone know what caused these problems?

---

### Post by stderr on 2010-07-03
Glad you got it working again lordbux :) Good luck with the rest of the project!

edit, @cokedude: It would seem to have been the use of deprecated syntax that appears to have been removed from the g++ compiler relatively recently, the solution to which could be either to go through all the code and update it (rather impractical in lordbux's 80k line project!), or use an earlier version of the compiler.

I had quite an advantage in a sense, in that by the time I came to learn C++ everyone was using namespaces and the newer libraries, so I skipped an extra phase of transition.

---

