---
title: "c++ g++ in 10.04 lucid"
date: 2010-08-09
forum: General Help
---

### Post by mr. tibbs on 2010-08-09
I'm trying to learn some basic c++, but I can't even get Hello, world! to work. Here's what I'm entering in gedit (or whatever it's called):
[B]
#include <iostream>

int main ()
{|
  cout << "Hello, world!";
  return 0;
}[/B]

And here's what I get when I enter **g++ hello.cpp -o test** in the terminal:

[B]hello.cpp:4: error: expected primary-expression before &#8216;|&#8217; token
hello.cpp:5: error: &#8216;cout&#8217; was not declared in this scope[/B]

What am I doing wrong? Any suggestions on how to make it work? I've followed a few different guides on how to do this, and, no matter what, I always get the first error. (The second one is new.) Please halp! :(

EDIT: Some of the other ones I've tried include colons and a mysterious lower case L, but I can't find those templates now.

---

### Post by Vaphell on 2010-08-09
what it says - g++ expects something before the | sign, why is it even there? also std::cout if you havent specified the namespace (using namespace std)

---

### Post by darolu on 2010-08-09
Try with:
```
#include <iostream>
[COLOR="DarkGreen"]**using namespace std;**[/COLOR]

int main() {
        cout << "Hello World!\n";
        return 0;
}

```
[COLOR="DarkGreen"]**using namespace std;**[/COLOR] with this you declare that you'll be using the standard c++ libraries. If you are not going to include this line you have to declare it with "**std::cout**" as Vaphell mentioned.

---

### Post by GregBrannon on 2010-08-10
Welcome to the forum!

You may find the stickies and threads in the Programming Talk area useful.  You can jump there using the Forum Jump tool at the bottom of most screens - it's near the bottom - or if you read 'new posts' like I do, just select "Programming Talk" from the last column of an existing thread.

Some of the best programming help on the web exists in this forum.

Good luck!

---

### Post by wangkeit on 2010-08-10
> **mr. tibbs said:**
> I'm trying to learn some basic c++, but I can't even get Hello, world! to work. Here's what I'm entering in gedit (or whatever it's called):
[B]
#include <iostream>

int main ()
{|
  cout << "Hello, world!";
  return 0;
}[/B]

And here's what I get when I enter **g++ hello.cpp -o test** in the terminal:

[B]hello.cpp:4: error: expected primary-expression before ‘|’ token
hello.cpp:5: error: ‘cout’ was not declared in this scope[/B]

What am I doing wrong? Any suggestions on how to make it work? I've followed a few different guides on how to do this, and, no matter what, I always get the first error. (The second one is new.) Please halp! :(

EDIT: Some of the other ones I've tried include colons and a mysterious lower case L, but I can't find those templates now.
 please remove the sign "|" and recompilation

---

